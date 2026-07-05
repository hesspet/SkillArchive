# Nutzungsanleitung: Bühnenshow-Skills

Aufgabe: Anleitung zur Nutzung der projektlokalen Skills für Bauchreden-, Puppen- und Zaubershows.
Erstellt: 05.07.2026
Letzte Änderung: 05.07.2026
Version: 1.0.0

## Aktivierung

Die Skills liegen projektlokal unter `.opencode/skills/` und gelten für dieses Repository:

- `buehnenshow-koordinator`
- `buehnenshow-dialogpartner`
- `buehnenshow-texter`
- `buehnenshow-regisseur`
- `buehnenshow-material`
- `buehnenshow-marketing`

Nach dem Anlegen oder Ändern von Skills OpenCode neu starten oder eine neue Sitzung öffnen, damit die Skills zuverlässig geladen werden.

## Grundregel

Nutze `buehnenshow-koordinator`, wenn eine Aufgabe mehrere Bereiche betrifft: Idee, Dramaturgie, Text, ODT, Regie, Material oder Marketing.

Nutze Spezialskills, wenn die Aufgabe klar begrenzt ist:

- `buehnenshow-dialogpartner`: Ideen, Varianten, Konflikte, Gags und Rahmenhandlungen.
- `buehnenshow-texter`: Dialogfassung, Sprechzeichen, Bauchreden-Spielbarkeit und ODT-Dialoge.
- `buehnenshow-regisseur`: Timing, Bühnenbeats, Blickführung, Publikumsführung und Kürzungen.
- `buehnenshow-material`: Requisiten, Verbrauchsmaterial, Transport, Aufbau, Helferbedarf und Risiken.
- `buehnenshow-marketing`: Webtexte, Social Media, Handzettel und Veranstaltertexte.

## Wichtiger ODT-Hinweis

Dialogtexte müssen als echte `.odt`-Dateien erstellt oder bearbeitet werden. Dafür muss zusätzlich der Skill `odt` genutzt werden.

Markdown reicht nur für Konzepte, Listen, Marketingtexte und Arbeitsnotizen. DOCX wird nicht verwendet.

Ein ODT-Dialog enthält nach Projektregel:

- Metadatenkopf mit Erstelldatum, letzter Änderung und Version.
- Titel.
- Kurzbeschreibung.
- Figuren.
- Requisiten.
- Sprechzeichen-Legende.
- Dialog.
- Schluss-Spielanweisung.

Sprechzeichen:

- `/` kurzer Atemschnitt.
- `//` deutliche Pause mit weichem Zeilenumbruch.
- `~` gedehntes Wort.
- `[Spielanweisung]` nicht gesprochene Aktion.
- `**fett**` Betonung.

## Rollen-Agenten

Der Koordinator kann passende Rollen-Agenten aus `.opencode/agents/` einsetzen. Wenn sie in einer laufenden Sitzung noch nicht verfügbar sind, kann der allgemeine Agent mit klarer Rollenbeschreibung genutzt werden.

Typische Übergabe:

- Dialogpartner sammelt Ideen.
- Koordinator wählt Richtung und klärt offene Punkte.
- Texter schreibt Dialog oder ODT-Fassung.
- Regisseur prüft Spielbarkeit.
- Material prüft Requisiten und Organisation.
- Marketing schreibt Außentexte.

## Formulierungsbeispiele

### Komplettes Showkonzept

```text
Nutze buehnenshow-koordinator. Entwickle ein 15-Minuten-Showkonzept für ein Straßenfest mit Alrich und einem Trick aus dem Trickarchiv. Bitte mit Rahmenhandlung, Ablauf, Publikumsbeteiligung, Requisitenliste und Risiken.
```

### Dialog als echte ODT-Datei

```text
Nutze buehnenshow-koordinator und buehnenshow-texter. Erstelle einen 4-Minuten-Dialog als echte ODT-Datei für Alrich. Thema: Lampenfieber vor einer Zaubershow. Baue Sprechzeichen, Requisitenliste und Schluss-Spielanweisung ein.
```

### Pantomimische Puppe

```text
Nutze buehnenshow-texter. Schreibe eine ODT-Dialogszene mit Nasreddin. Nasreddin spricht nicht, sondern antwortet nur pantomimisch. Puppenspieler*in soll seine Gesten für das Publikum deuten.
```

### Brainstorming

```text
Nutze buehnenshow-dialogpartner. Gib mir fünf Ideen für eine kurze Puppen-Zauberszene zum Thema Bücher, mit je einer Puppe, einem Konflikt, einem Trickmoment und einem Risiko für die Umsetzung.
```

### Regieprüfung

```text
Nutze buehnenshow-regisseur. Prüfe diesen Dialog auf Timing, Pausen, Blickführung, Puppenwechsel, Einhändigkeit und Publikumsführung. Gib konkrete Kürzungen und Spielanweisungen zurück.
```

### Materialcheck

```text
Nutze buehnenshow-material. Prüfe diese Show auf Requisiten, Verbrauchsmaterial, Transport, Aufbauzeit, Helferbedarf, Technik, Genehmigungen und praktische Risiken.
```

### Marketingtext

```text
Nutze buehnenshow-marketing. Schreibe einen kurzen Webtext, einen langen Webtext, fünf Social-Media-Posts und einen Handzetteltext für eine familienfreundliche Puppen-Zaubershow. Keine Trickmethoden verraten und keine Künstlerbiografie erfinden.
```

### Bestehenden Text verbessern

```text
Nutze buehnenshow-koordinator. Überarbeite den vorhandenen Dialog in Shows und Showelemente/... für bessere Bauchreden-Spielbarkeit. Erhalte die Tricklogik, verbessere Pausen und erstelle wieder eine echte ODT-Datei.
```

## Typische Workflows

### Neue Show entwickeln

1. Thema, Anlass, Zielpublikum, Dauer und gewünschte Puppe nennen.
2. `buehnenshow-koordinator` starten.
3. Ideen durch `buehnenshow-dialogpartner` sammeln lassen.
4. Ablauf vom Koordinator strukturieren lassen.
5. Dialoge durch `buehnenshow-texter` als echte ODT-Datei erstellen lassen.
6. Regieprüfung durch `buehnenshow-regisseur` durchführen lassen.
7. Materialcheck durch `buehnenshow-material` durchführen lassen.
8. Bei Bedarf Werbetexte durch `buehnenshow-marketing` schreiben lassen.

### Vorhandene Show verbessern

1. Bestehende Datei oder Verzeichnis nennen.
2. Ziel der Überarbeitung nennen: kürzer, kindgerechter, lustiger, klarere Trickführung oder bessere Spielbarkeit.
3. Koordinator prüft Quellen, Puppenprofile und Trickarchiv.
4. Texter und Regisseur verbessern Text und Spielanweisungen.
5. Material-Skill prüft, ob Ablauf und Requisiten zusammenpassen.
6. Bei Dialogen wird die ODT-Datei aktualisiert.

### Nur Marketing erstellen

1. Zielgruppe, Anlass, Dauer und Puppe nennen.
2. `buehnenshow-marketing` direkt nutzen.
3. Gewünschte Formate nennen: Website, Social Media, Handzettel, Veranstaltertext.
4. Keine Zaubermethoden, keine Fake-Referenzen und keine erfundene Künstlerperson verwenden lassen.

## Gute Angaben im Prompt

Je mehr dieser Angaben vorhanden sind, desto weniger Rückfragen sind nötig:

- Anlass: Geburtstag, Straßenfest, Kindergarten, Klinik, Pflegeeinrichtung, Vereinsfeier.
- Zielgruppe: Kinder bis 6, Kinder ab 6, Erwachsene, gemischt, Klinik oder Pflege.
- Dauer: zum Beispiel 3, 10, 20 oder 45 Minuten.
- Puppe: Alrich, Nasreddin oder eine neue Puppe mit Kurzprofil.
- Trick: vorhandener Trick aus `Trickarchiv/` oder vom Nutzer beschriebener Trick.
- Ausgabe: ODT-Dialog, Markdown-Konzept, Checkliste oder Marketingtext.

## Beispiel für sehr guten Prompt

```text
Nutze buehnenshow-koordinator. Ich brauche ein 10-Minuten-Konzept für eine kleine Kindergarten-Gruppe ohne Tonanlage. Puppe: Nasreddin, pantomimisch. Trick: rotes Tuch verschwindet und erscheint als Papierschlange. Ergebnis zuerst als Markdown-Konzept mit Materialcheck. Danach soll ein kurzer Dialog als echte ODT-Datei entstehen.
```
