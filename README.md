# Lehrwerkstatt

<img src="icons/icon-192.png" alt="" width="96" align="right">

Die Lehrwerkstatt ist das Arbeitsmittel der Ausbilderinnen und Ausbilder der DRK Rettungshundestaffel Region Kassel: Ausbildung planen, durchführen und dokumentieren. Sie baut auf der Unterlagenwerkstatt 2.0 auf; deren Funktionen bleiben vollständig erhalten.

- **Ausbildung:** Übersicht, Kalender ab 12.10.2026 (bearbeitbar, Kalenderdatei .ics für Mitglieder), Termin durchführen mit Theorie-Impuls und Anwesenheit, Dreijahresplan 2027–2029, Trainingsgebiete und Gelegenheitsflächen
- **Lehren:** Lehrstoff aller Lehrpakete K01–R31 mit Folien, Sprechernotizen, Kursbuch und Selbsttest (offline, mit Volltextsuche und Korrekturliste), Ideen für die Lehrstunde, Übungsbestand mit 655 Übungen
- **Dateien:** Original-Dateien der Lehrpakete einmal einlesen (ganzer Ordner, mehrere Dateien oder ZIP), automatische Zuordnung zum Lehrpaket, Prüfung auf Doppelungen mit Entscheidung, danach offline öffnen
- **Glücksrad:** Helferbild für die Versteckperson, Aufgabe für den Hundeführer, Impulsaufgabe, Kurztheorie (10–15 Minuten, mit Unterlagen und Referentenblatt) und Spaßeinheit; Ziehungen werden je Person, Hund und Termin gespeichert
- **Dokumentation:** Personen (auch aus BARRY übernehmen: Name, Hund, Sparte, Prüfungen, Seminare – ohne Kontakt- und Gesundheitsdaten), Nachweise (Pflichtthemen, Ausbildungsstand, Fachdienstausbildung, San-Fortbildung) mit Nachweisblatt zum Drucken
- **Austausch zwischen Ausbildern:** Termin- und Planpakete, optional mit Passwort verschlüsselt; gemeinsamer Ordner am Rechner, „Teilen“ am Handy
- **Unterlagen:** Einlesen, Ordnen, Dopplungen finden, Unterrichtseinheiten mit Dozentenversion, Handout und Präsentation, Praxisbibliothek, KI-Auftrag zum Kopieren

## Nutzung

**Online:** Die veröffentlichte Seite im Browser öffnen und als App installieren:
- Android (Chrome): Menü → „App installieren“ bzw. „Zum Startbildschirm hinzufügen“
- iPhone/iPad (Safari): Teilen → „Zum Home-Bildschirm“
- Rechner (Chrome, Edge): Installationssymbol in der Adressleiste

Nach dem ersten Aufruf funktioniert die App auch ohne Internetverbindung.

**Als einzelne Datei:** `index.html` herunterladen und per Doppelklick öffnen. Für das erste Einlesen von Word-, PowerPoint- und PDF-Dateien sowie für die erste Ausgabe wird eine Internetverbindung benötigt.

Eine ausführliche Anleitung ist in die App integriert (Menüpunkt „Anleitung“).

## Datenschutz

- Personen, Anwesenheit, Nachweise, Ziehungen und eingelesene Unterlagen bleiben **ausschließlich im Browser des eigenen Geräts** (IndexedDB). Es gibt keinen Server, kein Konto und keine automatische Übertragung.
- Daten verlassen das Gerät nur, wenn Sie selbst ein Paket oder eine Sicherung erzeugen und weitergeben.
- Bitte keine Gesundheitsdaten der Mitglieder erfassen. Ob und wie Nachweise digital geführt werden, mit dem Kreisverband abstimmen.
- Die veröffentlichte Seite selbst (Lehrstoff, Ausbildungsplan, Trainingsgebiete) ist **für jeden mit der Adresse abrufbar**.
- Zum Lesen und Erzeugen von Office-Dateien werden beim ersten Gebrauch Programmbibliotheken von `cdnjs.cloudflare.com` bzw. `cdn.jsdelivr.net` geladen. Dabei werden keine Nutzerdaten übertragen; die Anbieter erhalten technisch bedingt die IP-Adresse.

## Sichern und Umziehen

Unter „Daten & Einstellungen“ → „Vollständige Sicherung herunterladen“ entsteht eine JSON-Datei mit allen Daten, ab Version 3 einschließlich Personen und Terminen. Die eingelesenen Dateien gehören wegen ihrer Größe nicht dazu; sie werden unter „Dateien“ getrennt als ZIP gesichert. Beim Einspielen einer Sicherung wird der vorhandene Bestand **vollständig ersetzt**. Für den Austausch zwischen mehreren Ausbildern dienen die Termin- und Planpakete unter „Austausch“.

## Aufbau des Repositorys

| Datei | Zweck |
|---|---|
| `index.html` | die vollständige App (eine Datei, keine Build-Schritte) |
| `manifest.webmanifest` | App-Beschreibung für die Installation |
| `sw.js` | Offline-Unterstützung (Service Worker) |
| `icons/` | App-Symbole |
| `docs/Kurzanleitung.pdf` | Kurzanleitung zur Unterlagenwerkstatt 2.0 |
| `.nojekyll` | GitHub Pages liefert die Dateien unverändert aus |

## Veröffentlichen mit GitHub Pages

1. Repository anlegen und alle Dateien hochladen („Add file“ → „Upload files“), dabei die Ordnerstruktur beibehalten.
2. „Settings“ → „Pages“ → „Deploy from a branch“, Branch `main`, Ordner `/ (root)`.
3. Nach kurzer Zeit ist die App unter `https://<benutzername>.github.io/<repository>/` erreichbar.

**Neue Version veröffentlichen:** `index.html` ersetzen und in `sw.js` die Konstante `CACHE` hochzählen (z. B. `lehrwerkstatt-v3.1`). Installierte Apps holen sich die neue Fassung beim nächsten Start mit Internetverbindung. Den Repository-Namen nicht ändern – sonst ändert sich die Adresse, und installierte Apps müssen neu eingerichtet werden.

## Verwendete Bibliotheken

Zur Laufzeit von einem CDN geladen: [mammoth.js](https://github.com/mwilliamson/mammoth.js) (DOCX lesen), [PDF.js](https://github.com/mozilla/pdf.js) (PDF lesen), [JSZip](https://github.com/Stuk/jszip) (PPTX lesen, DOCX und ZIP erzeugen), [PptxGenJS](https://github.com/gitbrent/PptxGenJS) (PowerPoint erzeugen). Es gelten die Lizenzen der jeweiligen Projekte.

## Lizenz

Noch festzulegen.
