# Fragebogen-App

Webapp zum Ausfüllen eines Fragebogens (aus einem Buch digitalisiert). Antworten werden im Browser gespeichert und können als PDF exportiert werden.

## Live

https://michas2.github.io/fragebogen/

## Lokal starten

```bash
python3 -m http.server 8080
```

Dann http://localhost:8080 öffnen.

## Dateien

- `index.html` – Fragebogen ausfüllen + PDF-Export (mit Auswahl des Fragebogens)
- `scan.html` – Experimenteller OCR-Ansatz (Tesseract.js + OpenCV.js). Weniger zuverlässig; erkennt keine Formatierung (z. B. Unterstreichungen).
- `questions/` – Verzeichnis mit allen Fragebögen im YAML-Format
- `questions/index.json` – Liste der verfügbaren Fragebogen-Dateien

## Fragebögen erstellen

Die YAML-Dateien werden aus Buchfotos mit Claude erzeugt. Das funktioniert deutlich
zuverlässiger als die OCR in `scan.html` und übernimmt auch Formatierungen wie
Unterstreichungen (`<u>…</u>`) korrekt.

## Neuen Fragebogen hinzufügen

1. YAML-Datei in `questions/` ablegen.
2. Dateinamen in `questions/index.json` eintragen.

Der Titel im Auswahlmenü wird automatisch aus dem `title`-Feld der YAML gelesen.

## Inline-Formatierung

In `text`- und `description`-Feldern sind einige HTML-Tags erlaubt und werden
sowohl in der Web-Ansicht als auch im PDF umgesetzt:

- `<u>…</u>` – unterstrichen
- `<b>…</b>` / `<strong>…</strong>` – fett
- `<i>…</i>` / `<em>…</em>` – kursiv

Alle anderen HTML-Tags werden aus Sicherheitsgründen als reiner Text dargestellt.

## YAML-Struktur

```yaml
title: "Titel"
sections:
  - title: "Kapitelname"
    description: "Optionaler Text"
    questions:
      - id: eindeutige_id
        text: "Fragetext"
        type: text|textarea|yesno|choice
        options:  # nur bei choice
          - "Option A"
```
