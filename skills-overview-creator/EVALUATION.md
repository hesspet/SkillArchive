# Evaluation

## Umfang

Der Skill wurde am 11. Juli 2026 mit drei Fällen jeweils gegen eine Baseline ohne Skill geprüft:

1. `SkillsOverview.md` fehlt: Zielpfad erfragen, Datei erstellen und nur die neue Datei stagen.
2. `SkillsOverview.md` existiert: vollständig aktualisieren, ohne den Git-Index zu verändern.
3. skills.sh liefert HTTP 503: vor Datei- und Git-Änderungen abbrechen.

Die Testdefinitionen stehen in `evals/evals.json`.

## Ergebnisse

- Die erzeugten Übersichten erfassten projektlokale, globale und eingebaute Skills mit projektspezifischen Beispielen.
- Verifizierte skills.sh-Seiten wurden verlinkt; ein simulierter `404`-Skill blieb ohne Link dokumentiert.
- Der 503-Fall unterschied technische Fehler korrekt von `404` und `410` und sah einen Abbruch ohne Rollback vor.
- Der Eval-Viewer wurde mit gepaarten Skill- und Baseline-Ausgaben gestartet und vom Anwender ohne weitere Änderungswünsche geprüft.

## Einschränkung

Die Testläufe verwendeten isolierte simulierte Projektzustände, um reale Repository- und Git-Änderungen zu vermeiden. Strenge Grader werteten deshalb mehrere Prozess-Assertions als nicht nachgewiesen, obwohl die Aktionsprotokolle den vorgesehenen Ablauf enthielten. Die Evaluation belegt die Anweisungs- und Ausgabequalität, ersetzt aber keinen Integrationstest mit einem entbehrlichen echten Git-Fixture.

Die automatische Trigger-Optimierung konnte nicht ausgeführt werden, weil das Plugin die ausführbare Datei `opencode` nicht fand (`ENOENT: uv_spawn 'opencode'`). Die Triggerbeschreibung wurde daher unverändert aus dem validierten Entwurf übernommen.

## Validierung

`skill_validate` meldete den Skill als gültig. Name, Verzeichnis und YAML-Frontmatter stimmen überein.
