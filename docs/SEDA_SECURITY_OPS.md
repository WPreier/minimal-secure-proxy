# Seda – Security & Operations

## Security (gleicher Anspruch wie SeDat)

- Privilege Drop + chroot
- Landlock / seccomp (optional, Linux)
- Strikte Limits (Connections, Memory, Headers)
- Rate Limiting
- Header-Filterung
- Kein Dateisystem-Zugriff für Content
- Fail-Closed Config
- Non-blocking alles Kritische

## Operations

- Hot Reload mit Connection Draining
- Admin Unix Socket (Status, Reload, Metrics)
- systemd Type=notify + Watchdog
- Nginx-kompatibles Logging (Drop-on-Full)
- Versionsprüfung beim Start (Warnung only)
- Single Binary

## Eingebaute Docs

- Vollständige Markdown-Dokumentation von SeDat und Seda ist im Binary.
- Wird als HTML oder raw Markdown unter `/sedat` und `/seda` ausgeliefert.
- Aktivierung über Config (Standard: an).

## Deployment

- Läuft typischerweise hinter SeDat auf localhost oder internem Netz.
- Kann auch standalone mit TLS laufen (optional).
- systemd Unit analog zu SeDat.
