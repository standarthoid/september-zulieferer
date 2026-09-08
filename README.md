# September — Zulieferer & Drehplan

Kleines Organisations-Tool für die Produktion **„September" (AT)**, W&B TV.

Trägt Zulieferer, ihre Kontaktdaten, Termine und Foto-Belege der gelieferten Produkte ein,
verknüpft das Ganze mit einer Kalender-Übersicht und zeigt zu jedem Tag den aktuellen
Drehplan (Drehtag-Nummer, Drehort, Motivwechsel).

Läuft komplett statisch als eine einzige HTML-Datei (`index.html`) — kein Server, keine
Datenbank, kein Build-Schritt. Kann direkt über GitHub Pages gehostet werden.

## Funktionen

- **Übersicht**: Monatskalender, der bei jedem Tag automatisch den Drehort aus dem
  Drehplan sowie alle Zulieferer-Termine dieses Tages anzeigt.
- **Zulieferer**: Kontaktdaten (Ansprechpartner, Telefon, E-Mail, Adresse, Website),
  freie Notizen ("was ist ausgemacht"), Termine, und Fotos der gelieferten Produkte
  (Drag & Drop oder Klick zum Hochladen).
- **Termine**: Liste aller Zulieferer-Termine, filter- und durchsuchbar.
- **Drehplan**: Editierbare Tabelle (Tag, Datum, Drehort, Zusatzmotive bei
  Motivwechsel, Notiz) — beim ersten Start mit dem Stand vom Drehplan-PDF
  (04.09.2026) vorbefüllt.
- **Kalender-Export**: Jeder Termin und der gesamte Drehplan lassen sich als
  `.ics`-Datei exportieren und in Google-/Apple-/Outlook-Kalender importieren.
- **Dropbox-Sync** (optional): Hält alle Daten inkl. Fotos zwischen mehreren
  Geräten synchron — ohne eigenen Server, per Dropbox-App-Key im Browser
  (PKCE-OAuth). Siehe Einstellungen → Dropbox-Sync für die Einrichtung
  (5 Minuten, einmalig).
- **Backup**: Alle Daten lassen sich jederzeit als JSON-Datei sichern und
  wiederherstellen (Einstellungen → Daten & Backup).

## Ohne Dropbox nutzen

Ohne Dropbox-Verbindung speichert die App alle Daten lokal im Browser
(IndexedDB). Das funktioniert sofort, ohne Einrichtung — die Daten bleiben
dann aber auf dem jeweiligen Gerät/Browser. Für Zugriff von mehreren Geräten
aus (Handy + Laptop) lohnt sich die einmalige Dropbox-Einrichtung.

## Lokal öffnen / testen

Einfach `index.html` im Browser öffnen, oder z.B. mit:

```bash
python3 -m http.server 8000
```

und dann `http://localhost:8000` aufrufen.

## Deployment (GitHub Pages)

1. Dieses Repo auf GitHub pushen.
2. In den Repo-Einstellungen → **Pages** → als Quelle den `main`-Branch,
   Ordner `/ (root)` auswählen.
3. Die Seite ist danach unter `https://<username>.github.io/<repo>/` erreichbar.

## Hinweis zum Drehplan-Seed

Die Drehplan-Tabelle wird beim allerersten Start mit dem Inhalt aus
`SEP_Drehplan 2.0 vom 4.9._20260904.pdf` vorbefüllt (Tag, Datum, Hauptmotiv,
Motivwechsel-Zusatzmotive, kurze Notiz — keine Szenen-/Shot-Details). Danach
ist die Tabelle frei editierbar und wird wie alle anderen Daten gespeichert
bzw. synchronisiert.
