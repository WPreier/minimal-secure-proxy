# Seda – Requirements

**Seda** (Echo / Stimme) ist der Proxy-Client zu SeDat. Er liefert ausschließlich statische HTML-Seiten aus dem Arbeitsspeicher.

## Kernanforderungen

- Rein statische HTML-Seiten (kein dynamischer Content, keine Templates zur Laufzeit).
- Alle Seiten liegen im Binary eingebettet und werden ausschließlich aus dem Speicher ausgeliefert.
- Kommunikation mit SeDat (oder kompatiblem Upstream) über ein bekanntes Proxy-Protokoll:
  - PROXY Protocol v1 und/oder v2 (empfohlen)
  - Alternativ HTTP/1.1 oder HTTP/2 mit klar definierten Headern
- Dieselben Sicherheits- und Betriebsprinzipien wie SeDat:
  - Privilege Drop / chroot
  - Strikte Ressourcenlimits
  - Non-blocking Logging
  - Fail-Closed Config
  - Hot Reload
  - systemd-Integration

## Eingebaute Dokumentation

- Das Binary enthält die **komplette Dokumentation** von SeDat und Seda.
- Auslieferung unter:
  - `https://<beliebiger-hostname>/sedat` → SeDat-Dokumentation
  - `https://<beliebiger-hostname>/seda` → Seda-Dokumentation
- In der Config aktivier-/deaktivierbar.
- **Standard: aktiv.**

## Config-Verhalten

Identisch zu SeDat:
- Aktive Config = versteckte Kopie
- `--resetconfig`
- Fehlerhafte Config → Zeilennummer + Grund, alte Config bleibt aktiv
- Regex-Matching auf relevante Felder

## Weitere Pflichtpunkte

- TLS 1.3 only (wenn Seda selbst TLS terminiert) oder Klartext hinter SeDat
- HTTP/1.1 + HTTP/2 (HTTP/3 optional)
- Rate Limiting und endliche Queues
- Header-Filterung
- Nginx-kompatibles Logging
- Admin-Socket für Status und Reload
- Versionsprüfung beim Start (Warnung only)
- Single Binary, minimale Abhängigkeiten
