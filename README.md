# Lehrwerkstatt

*(vormals „Unterlagenwerkstatt“)*

<img src="icon-192.png" alt="" width="96" align="right">

Die Lehrwerkstatt hilft Lehrenden, Trainerinnen und Trainern, über Jahre gewachsene Lehr- und Schulungsunterlagen zu ordnen und daraus einheitliche Unterrichtseinheiten zu machen – für jedes Fachgebiet.

- **Einlesen** von Word (DOCX), PowerPoint (PPTX), PDF mit Textschicht, TXT, Markdown und HTML – einzeln oder als ganzer Ordner
- **Ordnen** nach frei definierbaren Themen, mit Volltextsuche
- **Dopplungen finden**: identische Dateien, wortgleiche Passagen, ähnliche Inhalte; Gegenüberstellung zweier Unterlagen
- **Zusammenführen** mehrerer Unterlagen zu einer Rohfassung ohne doppelte Zeilen
- **Unterrichtseinheiten** von 1 UE bis zum ganzen Schulungstag, mit Ablaufplan, Pausen und Uhrzeiten; Länge einer UE einstellbar
- **Ausgabe** als Dozentenversion und Teilnehmer-Handout (Word oder PDF), als PowerPoint-Präsentation oder als Komplettpaket (ZIP)
- **Praxisbibliothek** für Planspiele, Fallbeispiele, Stationslernen und Hausaufgaben
- **Übungsbestand (Grundbestand)** – fest eingebaute, schreibgeschützte Übungssammlung (32 Module, 420 Übungen) mit Lösungen, Lerninhalten und Ausbilderangaben; Filter, Volltextsuche, Übernahme in die eigene Praxisbibliothek oder direkt in eine Unterrichtseinheit. Nur für Ausbilderinnen und Ausbilder bestimmt.
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
| `index.html` | die vollständige App (eine Datei, keine Build-Schritte; enthält auch den Übungsbestand) |
| `LW_index.html` | Weiterleitung für alte, gespeicherte Links auf `LW_index.html` – leitet auf `./` (= `index.html`) um |
| `manifest.webmanifest` | App-Beschreibung für die Installation (Name, Symbole, Startadresse) |
| `sw.js` | Offline-Unterstützung (Service Worker) |
| Symboldateien (im Hauptordner) | App-Symbole: `icon-192.png`, `icon-512.png` (normal), `icon-maskable-192.png`, `icon-maskable-512.png` (mit Schutzrand für runde/abgerundete Symbolformen), `apple-touch-icon.png` (iPhone/iPad), `favicon.ico`, `icon-16.png`, `icon-32.png` (Browser-Tab), `Lehrwerkstatt_Original.png` (Vorlage, wird von der App nicht geladen) |
| `docs/Kurzanleitung.pdf` | Kurzanleitung zum Weitergeben |
| `.nojekyll` | GitHub Pages liefert die Dateien unverändert aus |

**Wichtig:** Die Dateinamen müssen genau so lauten. Manifest, Service Worker und die Startadresse `./` erwarten `index.html` und `manifest.webmanifest`; fehlt eine der Dateien, die `sw.js` beim Installieren vorab speichert, scheitert die Installation als App.

## Veröffentlichen mit GitHub Pages

### Erstmals veröffentlichen

1. Neues öffentliches Repository anlegen, z. B. `lehrwerkstatt`.
2. Alle Dateien dieses Ordners hochladen („Add file“ → „Upload files“). Ab Version 2.2 liegen auch die Symbole im Hauptordner; es muss kein Unterordner angelegt werden (Ausnahme: `docs/`).
3. „Settings“ → „Pages“ → unter „Build and deployment“ als Quelle „Deploy from a branch“, Branch `main`, Ordner `/ (root)` wählen und speichern.
4. Nach kurzer Zeit ist die App unter `https://<benutzername>.github.io/<repository>/` erreichbar.

### Umstellung auf Version 2.2

1. `index.html`, `sw.js`, `manifest.webmanifest`, `LW_index.html` und `README.md` hochladen und ersetzen.
2. Die Symboldateien (`icon-*.png`, `apple-touch-icon.png`, `favicon.ico`) bleiben im Hauptordner. Ein Ordner `icons/` wird nicht mehr gebraucht.
3. Bereits gespeicherte Daten der Lehrwerkstatt übernimmt die App beim ersten Start einmalig in ihren neuen, eigenen Speicher. Der alte Speicher bleibt unverändert. Die Ausbildungsbibliothek auf derselben Adresse wird nicht berührt.

### Umstellung eines bestehenden Repositorys (Version 2.0 → 2.1)

Im bisherigen Repository lagen `LW_index.html` und `manifest-2.webmanifest`. So stellen Sie um:

| Bisher im Repository | Aktion |
|---|---|
| `LW_index.html` (die App) | durch die **neue `index.html`** ersetzen. Die alte App-Datei **nicht** unter ihrem Namen weiterführen. Stattdessen die beiliegende kleine **`LW_index.html` (Weiterleitung)** hochladen – sie überschreibt die alte Datei, und gespeicherte Lesezeichen oder Links funktionieren weiter. Wer keine alten Links hat, kann `LW_index.html` auch ganz löschen. |
| `manifest-2.webmanifest` | **löschen** und die neue **`manifest.webmanifest`** hochladen. |
| `sw.js` | durch die neue Fassung **ersetzen** (Cache `lehrwerkstatt-v2.1`). |
| `icons/` | `favicon.ico`, `icon-16.png`, `icon-32.png`, `icon-maskable-512.png` **ersetzen**, `icon-maskable-192.png` **neu** hochladen. Die übrigen Symbole bleiben unverändert. |
| `README.md` | ersetzen. |
| `docs/`, `.nojekyll` | unverändert lassen. |

Die gespeicherten Daten (IndexedDB) bleiben erhalten: Sie gehören zur Adresse `https://<benutzername>.github.io` und nicht zum Dateinamen. Bitte trotzdem vorher unter „Daten & Einstellungen“ eine Sicherung herunterladen. Bleibt der Repository-Name gleich, bleibt auch die Web-Adresse gleich; ein neuer Repository-Name ergibt eine neue Adresse – dann die Sicherung dort einspielen.

Falls die App bereits als „Unterlagenwerkstatt“ installiert war: Nach dem Hochladen die Seite einmal mit Internetverbindung öffnen. Name und Symbol der installierten App aktualisiert der Browser in der Regel selbstständig (das kann einige Tage dauern, teils mit Rückfrage). Schneller geht es, wenn Sie die installierte App entfernen und neu installieren – vorher eine Sicherung herunterladen und beim Entfernen **nicht** „Daten löschen“ ankreuzen.

**Neue Version veröffentlichen:** `index.html` ersetzen und in `sw.js` die Konstante `CACHE` hochzählen (z. B. `lehrwerkstatt-v2.2`). Installierte Apps holen sich die neue Fassung beim nächsten Start mit Internetverbindung.

### Ausbilderfassungen nachtragen

In `index.html` steht vor dem Hauptprogramm ein markierter Datenblock:

```
window.LW_AUSBILDERFASSUNG=/*AUSBILDERFASSUNG_START*/{}/*AUSBILDERFASSUNG_END*/;
```

Zwischen den beiden Markierungen wird ein JSON-Objekt „Übungs-ID → Ausbilderfassung“ eingesetzt. Beim Laden wird es in die Übungen des Grundbestands gemischt. Danach `CACHE` in `sw.js` hochzählen.

## Verwendete Bibliotheken

Zur Laufzeit von einem CDN geladen: [mammoth.js](https://github.com/mwilliamson/mammoth.js) (DOCX lesen), [PDF.js](https://github.com/mozilla/pdf.js) (PDF lesen), [JSZip](https://github.com/Stuk/jszip) (PPTX lesen, DOCX und ZIP erzeugen), [PptxGenJS](https://github.com/gitbrent/PptxGenJS) (PowerPoint erzeugen). Es gelten die Lizenzen der jeweiligen Projekte.

## Lizenz

Noch festzulegen.
