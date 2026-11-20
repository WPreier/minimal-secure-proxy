# Minimal Secure Proxy (MSP)

A minimal, highly secure reverse proxy and static content server written in Rust.

**Goal**: Serve static content (proxied from internal upstreams) with the smallest possible attack surface, strict resource limits, built-in ACME (including DNS-01), HTTP/1.1 + HTTP/2 + HTTP/3, privilege dropping, and non-blocking operation.

## Status

**Early development / specification phase.** This repository currently contains the complete requirements, architecture design, documentation structure, and a project skeleton. Full implementation is ongoing.

## Key Design Principles

- Memory-safe by default (Rust)
- Minimal external dependencies
- Fail-closed configuration
- No root after startup (chroot + privilege drop)
- Strict resource limits (connections, memory, queues, threads)
- Non-blocking logging and monitoring
- Built-in ACME with DNS-01 (Cloudflare + BIND/nsupdate + manual)
- Config reload without restart
- Nginx-compatible logging

## Quick Start (planned)

```bash
# After implementation
cargo build --release
./target/release/msp --config /etc/msp/config.toml
```

## Documentation

- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Configuration](docs/CONFIGURATION.md)
- [Installation & Operation](docs/INSTALLATION.md)
- [ACME & DNS-01](docs/ACME.md)
- [Security Model](docs/SECURITY.md)
- [Monitoring & Debugging](docs/MONITORING.md)

## Versioning

Semantic versioning with patch numbers. Built-in version check on startup warns about newer releases (display only).

## License

MIT or Apache-2.0 (to be decided)
