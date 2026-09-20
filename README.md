# Fragebogen-App

Webapp zum Ausfüllen eines Fragebogens (aus einem Buch digitalisiert). Antworten
werden im Browser gespeichert und können als PDF exportiert werden.

## Live

https://michas2.github.io/fragebogen/

## Lokal starten

```bash
python3 -m http.server 8080
```

Dann http://localhost:8080 öffnen (bei belegtem Port einen anderen wählen).

## Dateien

- `index.html` – Fragebogen ausfüllen + PDF-Export
- `questions/` – Fragebögen im YAML-Format (`default.yaml` ist das Beispiel)

## Inline-Formatierung

In `text`- und `description`-Feldern sind einige HTML-Tags erlaubt und werden
in der Web-Ansicht **und** im PDF umgesetzt:

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
