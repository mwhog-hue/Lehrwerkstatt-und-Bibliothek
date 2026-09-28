# Unterlagenwerkstatt

<img src="icons/icon-192.png" alt="" width="96" align="right">

Die Unterlagenwerkstatt hilft Lehrenden, Trainerinnen und Trainern, über Jahre gewachsene Lehr- und Schulungsunterlagen zu ordnen und daraus einheitliche Unterrichtseinheiten zu machen – für jedes Fachgebiet.

- **Einlesen** von Word (DOCX), PowerPoint (PPTX), PDF mit Textschicht, TXT, Markdown und HTML – einzeln oder als ganzer Ordner
- **Ordnen** nach frei definierbaren Themen, mit Volltextsuche
- **Dopplungen finden**: identische Dateien, wortgleiche Passagen, ähnliche Inhalte; Gegenüberstellung zweier Unterlagen
- **Zusammenführen** mehrerer Unterlagen zu einer Rohfassung ohne doppelte Zeilen
- **Unterrichtseinheiten** von 1 UE bis zum ganzen Schulungstag, mit Ablaufplan, Pausen und Uhrzeiten; Länge einer UE einstellbar
- **Ausgabe** als Dozentenversion und Teilnehmer-Handout (Word oder PDF), als PowerPoint-Präsentation oder als Komplettpaket (ZIP)
- **Praxisbibliothek** für Planspiele, Fallbeispiele, Stationslernen und Hausaufgaben
- **KI-Unterstützung ohne Datenabfluss im Hintergrund**: Die Werkstatt erstellt einen Auftrag für Claude oder ChatGPT, den Sie selbst kopieren; die Antwort wird automatisch auf alle Felder der Einheit verteilt

## Nutzung

**Online:** Die veröffentlichte Seite im Browser öffnen. In Chrome und Edge lässt sich die Werkstatt über das Installationssymbol in der Adressleiste als App installieren; nach dem ersten Aufruf funktioniert sie auch ohne Internetverbindung.

**Als einzelne Datei:** `index.html` herunterladen und per Doppelklick öffnen. Alle Funktionen stehen zur Verfügung; für das erste Einlesen von Word-, PowerPoint- und PDF-Dateien sowie für die erste Ausgabe wird eine Internetverbindung benötigt.

Geeignet sind aktuelle Versionen von Microsoft Edge, Google Chrome und Mozilla Firefox. Im privaten Modus werden keine Daten dauerhaft gespeichert.

Eine ausführliche Anleitung ist in die App integriert (Menüpunkt „Anleitung“). Eine zweiseitige [Kurzanleitung als PDF](docs/Kurzanleitung.pdf) eignet sich zum Weitergeben.

## Datenschutz

- Alle Daten – eingelesene Texte, Unterrichtseinheiten, Einstellungen – bleiben **ausschließlich im Browser des eigenen Geräts** (IndexedDB). Es gibt keinen Server, kein Konto und keine Übertragung an Dritte.
- Die Originaldateien werden nicht verändert; gespeichert wird nur ihr Text.
- Die Werkstatt sendet nichts an KI-Dienste. Was Sie in Claude oder ChatGPT einfügen, entscheiden Sie selbst.
- Zum Lesen und Erzeugen von Office-Dateien werden beim ersten Gebrauch Programmbibliotheken von `cdnjs.cloudflare.com` bzw. `cdn.jsdelivr.net` geladen. Dabei werden keine Nutzerdaten übertragen; die Anbieter erhalten technisch bedingt die IP-Adresse.

## Sichern und Umziehen

Unter „Daten & Einstellungen“ → „Vollständige Sicherung herunterladen“ entsteht eine JSON-Datei mit allen Daten. Beim Einspielen einer Sicherung wird der vorhandene Bestand **vollständig ersetzt**. Auf diesem Weg ziehen Daten auf ein anderes Gerät um oder werden im Team weitergegeben. Einen automatischen Abgleich zwischen mehreren Personen gibt es nicht.

## Aufbau des Repositorys

| Datei | Zweck |
|---|---|
| `index.html` | die vollständige App (eine Datei, keine Build-Schritte) |
| `manifest.webmanifest` | App-Beschreibung für die Installation |
| `sw.js` | Offline-Unterstützung (Service Worker) |
| `icons/` | App-Symbole |
| `docs/Kurzanleitung.pdf` | Kurzanleitung zum Weitergeben |
| `.nojekyll` | GitHub Pages liefert die Dateien unverändert aus |

## Veröffentlichen mit GitHub Pages

1. Neues öffentliches Repository anlegen, z. B. `unterlagenwerkstatt`.
2. Alle Dateien dieses Ordners hochladen („Add file“ → „Upload files“), dabei die Ordnerstruktur beibehalten.
3. „Settings“ → „Pages“ → unter „Build and deployment“ als Quelle „Deploy from a branch“, Branch `main`, Ordner `/ (root)` wählen und speichern.
4. Nach kurzer Zeit ist die App unter `https://<benutzername>.github.io/unterlagenwerkstatt/` erreichbar.

**Neue Version veröffentlichen:** `index.html` ersetzen und in `sw.js` die Konstante `CACHE` hochzählen (z. B. `unterlagenwerkstatt-v2.1`). Installierte Apps holen sich die neue Fassung beim nächsten Start mit Internetverbindung.

## Verwendete Bibliotheken

Zur Laufzeit von einem CDN geladen: [mammoth.js](https://github.com/mwilliamson/mammoth.js) (DOCX lesen), [PDF.js](https://github.com/mozilla/pdf.js) (PDF lesen), [JSZip](https://github.com/Stuk/jszip) (PPTX lesen, DOCX und ZIP erzeugen), [PptxGenJS](https://github.com/gitbrent/PptxGenJS) (PowerPoint erzeugen). Es gelten die Lizenzen der jeweiligen Projekte.

## Lizenz

Noch festzulegen.
