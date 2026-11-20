# SeDat & Seda

**SeDat** (türkisch: „der Rechtschaffene“) – minimaler, hoch sicherer Reverse-Proxy und Static-Content-Server in Rust.

**Seda** (türkisch/persisch: Echo / Stimme) – der zugehörige Proxy-Client für rein statische HTML-Seiten, die ausschließlich aus dem Speicher ausgeliefert werden.

Beide Projekte teilen denselben Sicherheits-, Betriebs- und Dokumentationsanspruch.

## Status

**Spezifikationsphase.** Vollständige Anforderungen für Code-Generierung durch andere KIs sind vorhanden.

## Dokumentation

### SeDat (Server)
- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Security](docs/SECURITY.md)
- [Operations](docs/OPERATIONS.md)
- [Config & Lifecycle](docs/CONFIG.md)
- [Ideas](docs/IDEAS.md)

### Seda (Client)
- [Seda Requirements](docs/SEDA_REQUIREMENTS.md)
- [Seda Architecture](docs/SEDA_ARCHITECTURE.md)
- [Seda Config](docs/SEDA_CONFIG.md)
- [Seda Security & Operations](docs/SEDA_SECURITY_OPS.md)

## Eingebaute Dokumentation

Beide Binaries enthalten die vollständige Dokumentation und können sie unter `/sedat` bzw. `/seda` ausliefern (konfigurierbar, Standard: aktiv).

## Versionierung

Semantic Versioning. Versionsprüfung beim Start (nur Warnung).
