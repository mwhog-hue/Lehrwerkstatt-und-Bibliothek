# Lehrwerkstatt – Änderungen in Version 2.1

*(vormals „Unterlagenwerkstatt“, Version 2.0) · Stand: 09.10.2026*

Sehr geehrte Frau Weiße,

nachfolgend sind die Änderungen der Version 2.1 zusammengestellt. Alle bisherigen Funktionen, Bereiche, Speicherschlüssel und das Sicherungsformat sind unverändert erhalten; es wurde nichts entfernt. Ihre im Browser gespeicherten Daten (IndexedDB) werden weiterverwendet.

---

## 1. Installation als App repariert

### Festgestellte Ursachen

| Nr. | Befund | Folge |
|---|---|---|
| a | Die App verweist auf `manifest.webmanifest`, die Datei hieß aber `manifest-2.webmanifest`. | Der Browser fand keine App-Beschreibung. |
| b | Im Manifest standen die Symbolpfade ohne den Ordner `icons/`. | Kein Symbol ladbar (Fehler 404). |
| c | Die App-Datei hieß `LW_index.html`; Manifest (`start_url "./"`) und `sw.js` (Vorabspeicherung von `./index.html`) erwarten `index.html`. | Die Vorabspeicherung im Service Worker schlug fehl; damit war keine Installation möglich. |
| d | Name im Manifest und im Titel noch „Unterlagenwerkstatt“, das Symbol zeigt „Lehrwerkstatt“. | Uneinheitliche Bezeichnung. |
| e | Das Browser-Symbol (Favicon) und das Logo in der Kopfzeile waren eingebettete alte Bilder. | Altes Erscheinungsbild im Browser-Tab und in der Kopfzeile. |

### Vorgenommene Korrekturen

- **Dateinamen:** `LW_index.html` → `index.html`, `manifest-2.webmanifest` → `manifest.webmanifest`.
- **Manifest:** Name und Kurzname „Lehrwerkstatt“, feste Kennung `"id": "./"`, Symbolpfade mit `icons/`, zusätzlich ein maskierbares Symbol in 192 px.
- **sw.js:** Cache-Name auf `lehrwerkstatt-v2.1` hochgezählt; die vorab gespeicherten Dateien entsprechen jetzt genau den vorhandenen Dateien (inklusive aller Symbole).
- **App-Datei:** Titel und Kopfzeile „Lehrwerkstatt“, Browser-Symbol und Apple-Touch-Icon verweisen auf die Dateien im Ordner `icons/`; das Kopfzeilen-Logo ist durch das neue Lehrwerkstatt-Symbol ersetzt (weiterhin eingebettet, damit es auch bei Nutzung als Einzeldatei erscheint).
- **Symbole geprüft:** `icon-192.png`, `icon-512.png` und `apple-touch-icon.png` (180 px) entsprechen bereits der Vorlage `Lehrwerkstatt_Original.png` und blieben unverändert. Neu aus der Vorlage erzeugt wurden:
  - `icon-maskable-512.png` und `icon-maskable-192.png`: Das runde Emblem füllt 78 % der Fläche (rund 11 % Schutzrand je Seite) auf rotem, leicht verlaufendem Grund. Damit bleibt der Schriftzug auch bei runder Beschnittform vollständig sichtbar. Die bisherige Fassung war zwar ebenfalls innerhalb der Schutzzone, das Emblem aber deutlich kleiner (rund 65 %).
  - `favicon.ico` (16/32/48/64 px), `icon-16.png`, `icon-32.png`: aus dem runden Emblem mit transparentem Rand, damit es im Browser-Tab größer wirkt.
- **Weiterleitung:** Neue kleine Datei `LW_index.html`, die gespeicherte Links und Lesezeichen automatisch auf die Lehrwerkstatt (`./`) umleitet.
- **README.md:** Abschnitte „Aufbau des Repositorys“ und „Veröffentlichen“ angepasst, einschließlich einer Tabelle, welche Dateien auf GitHub zu ersetzen, zu löschen oder neu hochzuladen sind.

### Prüfung (Playwright/Chromium über lokalen HTTP-Server)

Manifest lädt fehlerfrei; alle acht Symboldateien antworten mit Status 200; der Service Worker wird registriert, installiert und aktiviert, der Cache `lehrwerkstatt-v2.1` enthält alle elf vorgesehenen Dateien; die Installierbarkeitsprüfung von Chrome meldet keine Fehler; die Weiterleitung `LW_index.html` führt zur App.

---

## 2. Neu: Übungsbestand (Grundbestand) in der Praxisbibliothek

### Wo finde ich es?

Bereich **„Praxis & Planspiele“** → oben der Reiter **„Übungsbestand (Grundbestand)“**. Der bisherige Inhalt des Bereichs steht unverändert im Reiter „Eigene Praxisbausteine“, der beim Öffnen weiterhin zuerst angezeigt wird.

### Was ist enthalten?

- 32 Module (K01–K07, R08–R31, EH) mit 420 Übungen, fest eingebaut und **schreibgeschützt**. Der Bestand wird nicht im Browser gespeichert, kann also weder verändert noch versehentlich gelöscht werden und ist auf jedem Gerät sofort vorhanden.
- Da die Lehrwerkstatt nur von Ausbilderinnen und Ausbildern genutzt wird, sind **Lösungen** sowie die **Ausbilderangaben** offen sichtbar: Quelle/Folienbezug, Herkunft der Fassung, App-Bezug, ggf. zusammengeführte Karten, Fassungshinweis und Anmerkung.

### Funktionen

| Funktion | Beschreibung |
|---|---|
| Filter | Modul, Art (allein, mit Hund, als Helfer/in, in der Gruppe), Aufsicht (keine, empfohlen, erforderlich), Dauer (bis 10 / 11–20 / 21–30 / über 30 Min. / über mehrere Tage oder Einheiten), „nur mit Ausbilderfassung“, „nur noch nicht übernommene“. |
| Volltextsuche | Durchsucht alle Felder einschließlich Lösung und Ausbilderangaben; mehrere Wörter müssen alle vorkommen. |
| Detailansicht | Steckbrief, Ziel, Aufgabe, Ablauf, Fragen, Sicherheit, Erfolgskriterien, leichter/schwerer, Hilfen, Reflexion, Lösung, abgedeckte Lerninhalte des Moduls (mit Folienbezug) und alle Lerninhalte des Moduls, Ausbilderangaben, Ausbilderfassung. Mit ‹ und › blättern Sie durch die gefilterte Liste. |
| In eigene Praxisbibliothek übernehmen | Legt eine bearbeitbare Kopie als Entwurf an (siehe Zuordnung unten). Das Thema ist vorgeschlagen und in der Detailansicht wählbar. Die Kopie trägt den Vermerk „aus Grundbestand <Kennung>“, über den sich die Originalübung jederzeit wieder öffnen lässt. |
| Zur Unterrichtseinheit hinzufügen | Einheit wählen (oder „+ Neue Unterrichtseinheit mit dieser Übung anlegen“). Wahlweise wird die Übung als Text in „Planspiel / praktische Übung“ und die Lösung in „Lösung / Auswertung“ (nur Dozentenversion) angehängt **oder** als verknüpfter Praxisbaustein eingebunden. Optional wird eine Zeile im Ablaufplan ergänzt. |

### Zuordnung bei der Übernahme in die eigene Praxisbibliothek

| Praxisbaustein | aus der Übung |
|---|---|
| Titel | Titel |
| Thema | Vorschlag je Modul (z. B. K01–K07 → Kynologie, R12/R20/R28 → Flächensuche, R18 → Sprechfunk, EH → Erste Hilfe Hund), änderbar |
| Format | nach Art: Selbstlernübung, Übung mit Hund, Helferübung, Gruppenübung (diese vier Formate wurden der Formatliste hinzugefügt; die bisherigen bleiben) |
| Dauer | Dauer |
| Niveau | allein → Grundlage, Gruppe → Aufbau, mit Hund/als Helfer → Praxisnah |
| Hilfsmittel | Material |
| Lernziel | Ziel |
| Ablauf / Lage / Rollen | Teilnehmende, Aufsicht, Voraussetzungen, Aufgabe, Ablauf, Fragen, Sicherheit, Erfolgskriterien, leichter/schwerer, Hilfen, Reflexion |
| Lösung / Hinweise für Lehrende | Lösung (Ergebnis, Lösungsweg), abgedeckte Lerninhalte, Quellenvermerk `[Quelle: …]`, Fassungshinweis/Anmerkung, ggf. Ausbilderfassung |

Die Themenzuordnung je Modul ist ein Vorschlag meinerseits (logische Zuordnung, nicht aus den Unterlagen belegt); für Module wie R16, R25, R26, R30 wurde „Organisation / Recht“ gewählt. Sie können das Thema vor der Übernahme in der Detailansicht ändern.

### Ausbilderfassung (Nachlieferung vorbereitet)

- Die Datei `/home/claude/apps/AUSBILDERFASSUNG_SCHEMA.md` lag bei der Bearbeitung **nicht vor**. Die Anzeige wurde deshalb bewusst fehlertolerant gebaut. Erwartet wird je Übung ein Objekt mit den Abschnitten `vorbereitung`, `zeitplan`, `rollen`, `beobachtung`, `typische_fehler`, `varianten`, `jahresplan`, `dokumentation`. Gängige Schreibweisen werden ebenfalls erkannt (z. B. „Typische Fehler“, „Varianten nach Ausbildungsstand“, „Planung im Jahresplan“). Weitere Felder erscheinen zusätzlich am Ende.
- Jeder Abschnitt darf Text, eine Liste, eine Tabelle (Liste gleichartiger Objekte, z. B. Zeitplan mit Minuten/Phase/Inhalt) oder ein Objekt mit Unterpunkten sein (z. B. Varianten je Ausbildungsstand).
- Der Datenblock steht in `index.html` vor dem Hauptprogramm:
  `window.LW_AUSBILDERFASSUNG=/*AUSBILDERFASSUNG_START*/{}/*AUSBILDERFASSUNG_END*/;`
  Zwischen die Markierungen gehört ein JSON-Objekt `{"K01-S1": {…}, …}`. Eine Liste in der Form `[{"id": "K01-S1", "ausbilderfassung": {…}}]` wird ebenfalls akzeptiert.
- Ist der Block fehlerhaft, startet die App trotzdem; im Übungsbestand erscheint dann ein roter Hinweis. Ohne Ausbilderfassung zeigt die Detailansicht einen kurzen Vermerk „wird nachgeliefert“.
- Die Darstellung wurde mit Probedaten geprüft und die Probedaten anschließend wieder entfernt. Sobald das Schema vorliegt, empfehle ich einen kurzen Abgleich.

### Sicherung

Übernommene Praxisbausteine (mit dem neuen Feld `origin` = Kennung der Übung) und geänderte Unterrichtseinheiten laufen in der vollständigen Sicherung mit. Das Sicherungsformat (`unterlagenwerkstatt-backup`, Version 2) ist unverändert; ältere Sicherungen lassen sich weiterhin einspielen. Die Sicherungsdatei heißt jetzt `lehrwerkstatt-sicherung-JJJJ-MM-TT.json`. Der Grundbestand selbst ist nicht Teil der Sicherung, weil er in der App enthalten ist.

### Anleitung

Abschnitt 9 der Anleitung heißt jetzt „Praxis und Planspiele, Übungsbestand“ und beschreibt die neue Funktion; Abschnitt 1 und die häufigen Fragen wurden um je einen Punkt ergänzt.

---

## 3. Prüfung

Mit Playwright (Chromium) über einen lokalen HTTP-Server, 58 Einzelprüfungen ohne Befund, keine JavaScript-Fehler:

- alle acht bisherigen Bereiche aufrufbar; Unterrichtseinheit anlegen, eigener Praxisbaustein, Entwurfsvorlage, Bearbeiten wie bisher;
- Filter, Volltextsuche (auch in Ausbilderfeldern), „weitere anzeigen“, Detailansicht mit Lösung, Lerninhalten und Ausbilderangaben, Blättern;
- Übernahme in die eigene Praxisbibliothek (Zuordnung geprüft), Hinzufügen zu einer Einheit in beiden Varianten samt Ablaufzeile, neue Einheit aus einer Übung;
- Dozentenversion enthält Übung und Lösung, Teilnehmer-Handout nur die Übung ohne Lösung;
- Sicherung enthält die übernommenen Einträge; Löschen und Einspielen, Einspielen einer älteren 2.0-Sicherung, Neuladen;
- Ansicht in Handy- (400 px) und Desktopbreite, ohne seitliches Verschieben.

Ein Vergleich der alten und der neuen App-Datei ergibt 18 geänderte Originalzeilen (Name, Symbole, Version, Formatliste, Herkunftsvermerk, Praxisliste, Anleitung); alles Übrige wurde ausschließlich ergänzt.

---

## 4. Was ist beim Veröffentlichen zu tun?

1. Vorher in der bisherigen Fassung unter „Daten & Einstellungen“ eine **Sicherung herunterladen**.
2. Im GitHub-Repository:
   - **ersetzen:** `LW_index.html` durch die beiliegende **Weiterleitungsdatei** `LW_index.html`, `sw.js`, `README.md`, im Ordner `icons/` die Dateien `favicon.ico`, `icon-16.png`, `icon-32.png`, `icon-maskable-512.png`;
   - **neu hochladen:** `index.html`, `manifest.webmanifest`, `icons/icon-maskable-192.png`;
   - **löschen:** `manifest-2.webmanifest`;
   - unverändert lassen: `docs/`, `.nojekyll`, übrige Symbole.
   Diese Datei `AENDERUNGEN.md` muss nicht hochgeladen werden.
3. Die Seite einmal mit Internetverbindung aufrufen. In Chrome bzw. Edge erscheint danach das Installationssymbol in der Adressleiste.
4. Bei jeder künftigen Änderung an `index.html` (auch beim Nachtragen der Ausbilderfassungen) in `sw.js` die Konstante `CACHE` hochzählen, z. B. `lehrwerkstatt-v2.2`.

**Hinweis:** Die beiliegende `docs/Kurzanleitung.pdf` nennt noch den alten Namen „Unterlagenwerkstatt“ und enthält den Übungsbestand nicht; sie wurde nicht verändert.

