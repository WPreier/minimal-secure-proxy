# Operations, Reliability & Monitoring Ideas

## Config & Lifecycle
- Hot config reload without restart (connection draining: old connections finish with old config).
- Fail-closed on invalid config.
- Dry-Run / Check mode: validate config and ACME flow without binding ports or requesting real certificates.

## ACME & Certificates
- Max 5 concurrent renewals.
- ARI support when provider offers it.
- Timely renewal start with jitter.
- Manual TXT record mode + Cloudflare + BIND (nsupdate/TSIG) + generic hook.
- Cleanup of challenge records.

## Monitoring (must never block the server)
- Admin Unix socket / Named Pipe: status, metrics, reload, graceful shutdown.
- Non-blocking nginx-compatible access + error logs (drop on full disk).
- Optional structured debug logs only on demand.
- systemd Type=notify + Watchdog.
- Lightweight upstream health checks (non-blocking) with automatic exclusion of unhealthy backends.
- Version check on startup (warn only, no auto-update).

## Deployment
- Single binary, minimal files.
- systemd unit with strong sandboxing directives (ProtectSystem=strict, PrivateTmp, etc.).
- Read-only root filesystem friendly.
- Clear upgrade path with semantic versioning and release notes.
