# Additional Ideas & Open Points (for iterative refinement)

## Security
- Landlock + seccomp combination after drop.
- Optional request fingerprinting resistance or deliberate TLS fingerprint.
- Content-Integrity checks or SRI header injection.
- Strict PROXY Protocol validation.

## Performance & Protocols
- Early Hints (103) support.
- Explicit non-support of HTTP/2 Server Push.
- Configurable Alt-Svc max-age.
- IPv6 Happy Eyeballs on upstream side.

## Observability
- Request-ID in all logs and upstream headers.
- Latency histograms in admin metrics.
- Log sampling under high load.

## Operations
- Multiple certificates per listener (SNI) with different ACME accounts/providers.
- Optional CT log monitoring.
- Graceful shutdown with connection draining.
- Self-watchdog that exits cleanly on event-loop hang (for systemd restart).

## Documentation & Process
- Step-by-step practical examples for every major feature.
- Architecture diagrams.
- Threat model document.
- Upgrade and rollback procedures.

These points are intentionally open for discussion and refinement before implementation starts.
