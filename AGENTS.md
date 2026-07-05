# SkillArchive

Archiv zur Veröffentlichung von OpenCode-Skills und -Agenten auf GitHub.

## Bei Start des Projektes

* Bei jedem Start des Projektes mit OpenCode, codebase-memory neu indizieren. 
* Neue Dateien, sofern sie nicht von .gitignore ausgeschlossen wurde, immer in GIT aufnehmen.
* Nutze immer CRLF  anstelle LF. Reines Windows Umfeld.

## Struktur

Jede Skill/Agent-Gruppe hat ein Unterverzeichnis:

```
<Gruppe>/
  readme.md       # Beschreibung der Gruppe, Aktivierung, Workflows
  skills/
    <name>/
      SKILL.md     # YAML frontmatter: name, description
  agents/
    <name>.md      # YAML frontmatter: description, mode: subagent
```

Aktuell: `Bühnenshow/` (einzige Gruppe).

## Wichtig für Agenten

- **Dieses Repo ist das Publikationsarchiv.** Skills/Agenten hier sind die Quellen, die Nutzer in ihr Projekt kopieren. Nicht die aktive `.opencode/`-Installation.
- **Sprache: Deutsch** mit Umlauten und ß.
- **Neue Gruppe anlegen**: Verzeichnis mit `skills/`, `agents/` und `readme.md` erstellen. `readme.md` erklärt Zweck, Aktivierung, Workflows.
- **Skill anlegen**: `skills/<name>/SKILL.md` — YAML-Frontmatter mit `name` und `description`. Description = Triggerbedingung (wann OpenCode den Skill vorschlagen soll). Body = ausführliche Anleitung.
- **Agent anlegen**: `agents/<name>.md` — YAML-Frontmatter mit `description` und `mode: subagent`. Body = Rollenbeschreibung.
- **Keine DOCX**, nur ODT für Dialogtexte und Markdown für Konzepte/Listen/Marketing.
- **Sprechzeichen** (nur für Bauchredenskills relevant): `/` (kurzer Atemschnitt), `//` (Pause), `~` (Dehnung), `[Spielanweisung]`, `**fett**` (Betonung).
- **Neutrale Rollenbezeichnung**: `Puppenspieler*in`.
- **Projektregel**: Prüfe vor Abschluss, ob alle referenzierten Quellen (`Puppenprofile/`, `Trickarchiv/`, `Shows und Showelemente/`) in den Skills korrekt benannt sind — diese existieren nicht in SkillArchive, sondern im Zielprojekt des Nutzers.

## Commands

Kein Build-Tool, kein Test-Framework. Nur git.
