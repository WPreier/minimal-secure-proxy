# Additional Ideas & Open Points

## SeDat + Seda gemeinsam

- Beide Binaries enthalten die Dokumentation des jeweils anderen.
- Gemeinsame Config-Philosophie (versteckte Kopie, Fail-Closed, Zeilenfehler).
- Gemeinsames Logging-Format.
- Optionale gemeinsame Admin-API.

## Seda-spezifisch

- Eingebettete Seiten können zur Compile-Zeit aus einem `pages/`-Verzeichnis generiert werden.
- Optionaler Build-Step, der die Markdown-Docs in HTML umwandelt.
- Health-Endpoint `/health` (eingebettet).

## Offen für weitere Überarbeitung

Diese Spezifikation ist bewusst so geschrieben, dass andere KIs (Cursor, Claude, GPT, etc.) daraus direkt Code generieren können.
