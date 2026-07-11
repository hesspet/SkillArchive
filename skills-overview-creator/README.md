# skills-overview-creator

OpenCode-Skill zum Erstellen und Aktualisieren einer projektbezogenen `SkillsOverview.md`.

## Funktionen

- Erfasst projektlokale, globale und eingebaute Skills.
- Erkennt die Projektsprache und formuliert Beschreibungen sowie Beispiele passend zum Projekt.
- Ergänzt verifizierte skills.sh-Links; nicht gelistete Skills bleiben ohne Link enthalten.
- Bricht bei technischen skills.sh-Problemen ab, bevor eine bestehende Übersicht verändert wird.
- Fragt bei fehlender Zieldatei nach dem Ablageort und schlägt `docs/SkillsOverview.md` vor.
- Staged in Git ausschließlich eine neu erstellte Übersicht. Aktualisierte Dateien werden nicht automatisch gestaged.
- Führt keine Commits oder Git-Rollbacks aus.

## Beispiele

```text
Erstelle eine Übersicht aller installierten Skills für dieses Projekt.
```

```text
Aktualisiere docs/SkillsOverview.md auf die aktuell verfügbaren OpenCode-Skills.
```

## Installation

Globaler OpenCode-Pfad:

```text
~/.config/opencode/skills/skills-overview-creator/
```

Die Verzeichnisstruktur muss mindestens `SKILL.md` enthalten. `evals/evals.json` dokumentiert die verwendeten Testfälle.

## Sicherheit

Eine vorhandene Übersicht wird erst nach vollständiger Inventur und erfolgreicher Prüfung aller ableitbaren skills.sh-Seiten ersetzt. Technische Netzwerkfehler führen zum Abbruch ohne Änderung. Fehlende Skill-Seiten (`404` oder `410`) sind kein technischer Fehler.
