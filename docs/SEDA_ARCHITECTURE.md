# Seda – Architecture

## Rolle

Seda ist der **Client / Backend**, der von SeDat (oder einem anderen Proxy) angesprochen wird.

```
Client → SeDat (Proxy) → Seda (Static Memory Server)
```

## Auslieferung

- Alle HTML-Seiten sind zur Compile-Zeit eingebettet (`include_str!` oder ähnlich).
- Kein Dateisystem-Zugriff für Content zur Laufzeit.
- Dokumentation von SeDat und Seda ist ebenfalls eingebettet und unter `/sedat` und `/seda` erreichbar (wenn aktiviert).

## Proxy-Protokoll

Empfohlen: **PROXY Protocol v1/v2**
- Seda liest die echte Client-IP aus dem PROXY-Header.
- Danach normales HTTP/1.1 oder HTTP/2.

Alternativ: reine HTTP-Kommunikation mit vertrauenswürdigen Headern (nur hinter SeDat).

## Gemeinsame Prinzipien mit SeDat

- Tokio Runtime mit begrenzten Worker-Threads
- rustls (falls TLS)
- Bounded Channels
- Privilege Drop nach Bind
- Non-blocking Logging-Task
- Precompiled Regex
- Fail-Closed Config-Reload

## Module (vorgeschlagen)

- `config` – Laden, Validierung, versteckte Kopie
- `embedded` – Statische Seiten + Dokumentation
- `proxy_proto` – PROXY Protocol Parser
- `http` – Request-Handling und Matching
- `admin` – Unix Socket
- `logging` – Non-blocking nginx-style
