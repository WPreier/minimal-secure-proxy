# Security Model & Hardening Ideas

## Privilege & Sandbox
- Refuse to start as root (or drop immediately after bind).
- chroot + setuid/setgid + clear supplementary groups.
- NoNewPrivileges / PR_SET_NO_NEW_PRIVS.
- Optional Landlock (filesystem restrictions) after privilege drop.
- Optional seccomp-BPF filter (allow only necessary syscalls).
- Capability bounding set: only CAP_NET_BIND_SERVICE temporarily if needed.
- Close unnecessary file descriptors before drop.

## Resource & Attack Resistance
- Hard limits on connections, streams, memory, headers, body size, open files.
- Finite queues everywhere – overflow = drop.
- Rate limiting (IP-based, configurable down to very low rates).
- Protection against Slowloris, request smuggling, HTTP desync, compression bombs.
- Strict header whitelist / stripping of risky headers (Content-Disposition, Transfer-Encoding tricks, etc.).
- Upstream response validation (Content-Type whitelist, size limits, no dangerous headers).
- Optional mTLS or shared-secret to upstream.

## Further Ideas
- Quarantine mode: temporarily stricter limits for IPs showing suspicious patterns.
- Memory/FD pressure handling: automatically more aggressive dropping when resources are low.
- Certificate backup / fallback certificate if ACME fails.
- Request-ID propagation through the entire path for tracing (non-blocking).
