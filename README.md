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

- `index.html` – Fragebogen ausfüllen + PDF-Export
- `scan.html` – Buchseiten per OCR (Tesseract.js + OpenCV.js) in YAML umwandeln
- `questions.yaml` – Alle Fragen im YAML-Format

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
