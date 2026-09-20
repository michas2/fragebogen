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
- `scan.html` – Buchseiten per OCR (Tesseract.js + OpenCV.js) in YAML umwandeln
- `questions/` – Verzeichnis mit allen Fragebögen im YAML-Format
- `questions/index.json` – Liste der verfügbaren Fragebogen-Dateien

## Neuen Fragebogen hinzufügen

1. YAML-Datei in `questions/` ablegen.
2. Dateinamen in `questions/index.json` eintragen.

Der Titel im Auswahlmenü wird automatisch aus dem `title`-Feld der YAML gelesen.

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
