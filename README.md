# SeDat

**SeDat** (türkisch: „der Rechtschaffene“) – ein minimaler, hoch sicherer Reverse-Proxy und Static-Content-Server in Rust.

**Ziel:** Statische Inhalte (von internen Upstreams) mit kleinster Angriffsfläche, strikten Ressourcenlimits, eingebautem ACME (inkl. DNS-01), HTTP/1.1 + HTTP/2 + HTTP/3, Privilege Drop und non-blocking Betrieb ausliefern.

## Status

**Spezifikations- und Designphase.**  
Das Repository enthält die vollständigen Anforderungen, Architektur-Notizen, Security- und Betriebsideen sowie ein Projektskelett. Die Implementierung startet nach weiterer Überarbeitung der Dokumentation.

## Dokumentation

- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Security Model & Hardening](docs/SECURITY.md)
- [Operations & Monitoring](docs/OPERATIONS.md)
- [Config & Lifecycle](docs/CONFIG.md)
- [Additional Ideas](docs/IDEAS.md)
- [Configuration examples](examples/config.toml)

## Versionierung

Semantic Versioning. Eingebaute Versionsprüfung beim Start warnt vor neueren Releases (nur Anzeige, keine automatische Aktion).

## Lizenz

MIT oder Apache-2.0 (noch zu entscheiden)
