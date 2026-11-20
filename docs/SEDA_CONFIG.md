# Seda – Config & Lifecycle

## Grundprinzip (identisch zu SeDat)

- Aktive Config = versteckte interne Kopie.
- Anwender-Config wird nur nach erfolgreicher Validierung übernommen.
- Bei Fehler: Zeilennummer + Grund, alte Config bleibt aktiv.
- Explizites `--resetconfig` zum Löschen der versteckten Kopie.

## Spezielle Optionen

```toml
[embedded_docs]
enabled = true          # Standard: true
# Wenn false: /sedat und /seda liefern 404

[proxy]
protocol = "proxy_v2"   # proxy_v1 | proxy_v2 | http
trusted_proxies = ["127.0.0.1", "::1"]

[server]
listen = ["127.0.0.1:8080"]
max_connections = 100

[[page]]
path = "/"
content = "index"       # Referenz auf eingebettete Seite

[[page]]
path = "/about"
content = "about"
```

## Matching

- Regex auf Path, Host, Header (wie SeDat).
- Fallback: eingebettete 404-Seite.

## Dokumentation ausliefern

- `/sedat` und `/seda` sind spezielle Locations.
- Nur aktiv, wenn `embedded_docs.enabled = true`.
- Content kommt aus dem Binary (kein externes File).
