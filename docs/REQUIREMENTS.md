# Requirements – SeDat

## Namensgebung
SeDat (türkisch: „der Rechtschaffene“)

## Kern
- Reverse Proxy für statische Inhalte von internen Upstreams
- HTTP/1.1, HTTP/2, HTTP/3 (QUIC)
- TLS 1.3 only
- Eingebaute ACME-Implementierung (kein externes ACME-Crate für den Kern-Flow)
- DNS-01 Pflicht (Cloudflare + BIND/nsupdate + manuell + generischer Hook)
- ARI-Unterstützung wenn vom Provider angeboten
- Mehrere Backends mit vorab kompilierten Regex auf alle Client-Felder
- Config-Reload ohne Restart, Fail-Closed mit Zeilenangabe
- Aktive Config = versteckte Kopie; `--resetconfig` zum expliziten Zurücksetzen
- Dual-Stack IPv4/IPv6
- Nginx-kompatibles Access- und Error-Log (non-blocking)
- Rate-Limiting, endliche Queues, harte Ressourcenlimits
- chroot + Privilege Drop, kein Start als root
- Admin-Socket für Status + Reload
- systemd notify + Watchdog
- gzip + brotli mit strikten Limits und Bomb-Schutz
- Header-Filterung
- PROXY Protocol v1 + v2
- Alt-Svc für HTTP/3
- Max. 5 gleichzeitige ACME-Renewals
- Eingebettete 404-Seite (kein externes File) als Fallback
- Versionsprüfung beim Start (nur Warnung)

## ACME-Provider (Minimum)
- Let's Encrypt
- ZeroSSL
- Google Trust Services
- Custom RFC-8555 Directory
