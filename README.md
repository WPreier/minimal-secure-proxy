# Minimal Secure Proxy (MSP)

A minimal, highly secure reverse proxy and static content server written in Rust.

**Goal**: Serve static content (proxied from internal upstreams) with the smallest possible attack surface, strict resource limits, built-in ACME (including DNS-01), HTTP/1.1 + HTTP/2 + HTTP/3, privilege dropping, and non-blocking operation.

## Status

**Specification & design phase.**  
The repository contains the complete requirements, architecture notes, security and operations ideas, and a project skeleton. Implementation will start after further review and refinement of the documentation.

## Documentation

- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Security Model & Hardening](docs/SECURITY.md)
- [Operations & Monitoring](docs/OPERATIONS.md)
- [Additional Ideas (open for refinement)](docs/IDEAS.md)
- [Configuration examples](examples/config.toml)

## Versioning & Releases

Semantic versioning. Built-in version check on startup warns about newer releases (display only, no automatic action).

## License

MIT or Apache-2.0 (to be decided)
