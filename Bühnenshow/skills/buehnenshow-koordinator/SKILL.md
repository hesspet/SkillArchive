---
name: buehnenshow-koordinator
description: Use when planning, drafting, reviewing, or organizing German Bauchreden, Puppen and Zaubershow material. Trigger for complete show concepts, puppet dialogue, magic-trick integration, ODT dialogue workflows, staging, material planning, and marketing handoffs in this repository.
---

# Buehnenshow Koordinator

Aufgabe: Koordiniert Entwurf, Prüfung und Übergabe von Bauchreden-, Puppen- und Zaubershows.
Erstellt: 04.07.2026
Letzte Änderung: 04.07.2026
Version: 1.0.1

## Zweck

Nutze diesen Skill als primären Einstieg, wenn aus einer Idee, einem Thema, einem Trick, einem Puppenprofil oder einer Zielgruppe eine spielbare Show, Szene oder Begleitdokumentation entstehen soll.

## Quellen

Lies zuerst die relevanten Projektregeln und Fachquellen:

- `AGENTS.md` für ODT-Regeln, Sprache, Rollen, Sprechzeichen und Ablage.
- `Puppenprofile/` für Charakter, Sprache, Ausstattung und Einschränkungen der Puppen.
- `Trickarchiv/` für verfügbare Tricks, Einhändigkeit, Requisiten, Helferbedarf und Varianten.
- `Shows und Showelemente/` für vorhandene Showteile, wenn der Nutzer darauf verweist.

## Workflow

1. Kläre pragmatisch nur das, was das Ergebnis deutlich beeinflusst: Anlass, Zielpublikum, Ort, Dauer, gewünschte Puppe, gewünschte Tricks, Tonalität und gewünschtes Ausgabeformat.
2. Dokumentiere Annahmen knapp, wenn der Nutzer direkt ein Ergebnis will.
3. Wähle passende Rollen-Agenten oder Rollen-Skills aus.
4. Prüfe Bauchreden-Einschränkungen: schwierige Laute wie B, P und M, Sprechpausen, freie Hand, Sitzposition, einhändige Trickführung und Puppenwechsel.
5. Plane Zauberei als Teil der Geschichte, nicht als lose Nummer.
6. Erfinde keine Spezialrequisiten, außer der Nutzer gibt sie vor oder `Trickarchiv/` beziehungsweise ein Puppenprofil erlaubt sie.
7. Erstelle Dialogtexte als echte `.odt`-Datei über den `odt`-Skill. Ein Markdown-Review-Artefakt oder nur ODT-tauglicher Text ersetzt die ODT-Datei nicht, wenn der Auftrag ODT verlangt.
8. Schreibe Konzepte, Listen und Marketing als Markdown.

## Teamrollen

Nutze nach Möglichkeit die projektlokalen Agenten aus `.opencode/agents/`. Falls sie in der laufenden Sitzung noch nicht verfügbar sind, verwende den allgemeinen `general`-Agenten mit der jeweiligen Rollenbeschreibung.

- `buehnenshow-dialogpartner`: Ideen, Rahmenhandlung, Konflikte, Gags, Varianten.
- `buehnenshow-texter`: Dialogfassung, Sprechzeichen, Bauchredner-Spielbarkeit, ODT-Vorbereitung.
- `buehnenshow-regisseur`: Timing, Bühnenbeats, Wechsel, Blickführung, Publikumsführung.
- `buehnenshow-material`: Requisiten, Verbrauchsmaterial, Aufbau, Transport, Helfer, Risiken.
- `buehnenshow-marketing`: Webtexte, Social Media, Handzettel, Showdokumentation.

## Ergebnisprüfung

Prüfe vor Abschluss:

- Deutsch mit deutscher Rechtschreibung, Umlauten und ß.
- Neutrale Rolle `Puppenspieler*in`; Puppen bleiben personalisiert.
- ODT nur für Dialogtexte, niemals DOCX.
- Wenn ODT verlangt ist, muss eine echte `.odt`-Datei erzeugt oder geändert werden; ein reiner Textentwurf ist dann unvollständig.
- ODT-Dialogaufbau nach `AGENTS.md`: Metadaten, Titel, Kurzbeschreibung, Figuren, Requisiten, Legende, Dialog, Schluss-Spielanweisung.
- `/`, `//`, `~`, `[Spielanweisung]` und `**fett**` korrekt eingeplant.
- Zielpublikum und Lokalität passend behandelt.
- Materialliste basiert auf Nutzerangabe, Puppenprofil oder Trickarchiv.
