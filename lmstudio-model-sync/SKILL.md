---
name: lmstudio-model-sync
description: "Synchronisiert LM Studio Modelle in die OpenCode-Konfiguration. Fragt LM Studio API (http://127.0.0.1:1234/v1/models) ab, zeigt nummerierte Liste, Benutzer wählt per Komma-getrennten Nummern oder 'all' aus. Überschreibt nur models-Liste im lmstudion-Provider in ~/.config/opencode/opencode.json. ERZWINGE diesen Skill bei: 'aktualisier die Modelle', 'neue Modelle geladen', 'Config pflegen', 'LM Studio', 'Modelle synchronisieren', 'opencode config Modelle', 'Provider Einstellungen Modelle', 'lmstudion Modelle updaten', 'lade die aktuellen Modelle', alle Anfragen die irgendwie Config-Pflege oder LM Studio Modellverwaltung betreffen – auch vage Formulierungen."
---

# lmstudio-model-sync

Synchronisiert LM Studio Modelle in die OpenCode-Konfiguration.

## Wann auslösen

Immer bei:
- "aktualisier die Modelle", "neue Modelle geladen", "Config pflegen"
- LM Studio, Modell-Pflege, opencode Config, Provider-Einstellungen
- "welche Modelle sind verfügbar", "synchronisier die Modelle"
- Jede vage Anfrage zu Modellen oder Config-Pflege

## Workflow

### 1. LM Studio Modelle abfragen

HTTP GET `http://127.0.0.1:1234/v1/models`

Extrahiere `data[].id`. Filtere Embedding-Modelle (Name enthält "embedding" oder "nomic").

### 2. Auswahl anbieten

```
Verfügbare Modelle in LM Studio:
1) qwen3.5-9b-deepseek-v4-flash
2) ornith-1.0-9b
...

Welche Modelle in Config übernehmen?
(Komma-getrennte Nummern, z.B. "1,2,5" oder "all")
```

Validiere Eingabe. Wiederhole bei Ungültigkeit.

### 3. Config aktualisieren

**Config-Pfad:** `~/.config/opencode/opencode.json`
**Provider:** `lmstudion` (baseURL: `http://127.0.0.1:1234/v1`)

Ersetze NUR den `models`-Block innerhalb von `provider.lmstudion`.

Beachte: Die Datei ist JSONC (enthält `//`-Kommentare). **Parsiere sie NICHT als JSON**, sonst gehen Kommentare verloren. Manipuliere als Text (Edit/Replace).

Format pro Modell:
```json
"model-id": { "name": "model-id (local)" }
```

### 4. Bestätigen

Zeige Diff/Summary. Hinweis: OpenCode neustarten.

## Fehlerbehandlung

- LM Studio nicht erreichbar: "LM Studio läuft nicht. Bitte Port 1234 prüfen."
- Keine Modelle: "Keine Modelle in LM Studio gefunden."
- Config nicht gefunden: Prüfe auch `opencode.jsonc`.
