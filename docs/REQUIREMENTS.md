# Requirements – Minimal Secure Proxy

See the conversation history for the full iterative requirements. This document consolidates them.

## Core
- Reverse proxy for static content from internal upstreams
- HTTP/1.1, HTTP/2, HTTP/3 (QUIC)
- TLS 1.3 only
- Built-in ACME (no external ACME library for the core flow)
- DNS-01 mandatory (Cloudflare + BIND + manual + generic hook)
- ARI support if offered by provider
- Multiple backends with precompiled regex location matching
- Config reload without restart
- Dual-stack IPv4/IPv6
- Nginx-compatible access + error logs (non-blocking)
- Rate limiting, finite queues, hard resource limits
- chroot + privilege drop, refuse to start as root
- Admin Unix socket / Named Pipe for status + reload
- systemd notify + watchdog
- gzip + brotli with strict limits and bomb protection
- Header filtering (whitelist / strip risky headers)
- PROXY Protocol v1 + v2
- Alt-Svc for HTTP/3
- Max 5 concurrent ACME renewals
- Version check on startup (warn only)

## ACME Providers (minimum)
- Let's Encrypt
- ZeroSSL
- Google Trust Services
- Custom RFC 8555 directory

## Security Priorities
- Memory safety
- Resource exhaustion resistance
- Request smuggling / desync protection
- Upstream response validation
- Non-blocking everything critical
