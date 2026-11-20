# Architecture Overview

## High-Level Design

- Single binary
- Tokio runtime with strictly limited worker threads
- rustls for TLS (no OpenSSL)
- quinn / h3 or minimal custom for HTTP/3 (to be decided for minimal deps)
- Custom ACME state machine
- Precompiled regex for locations
- Bounded channels / queues everywhere
- Separate non-blocking logging task
- Admin control plane over Unix socket

## Privilege Model

1. Start (may need CAP_NET_BIND_SERVICE or temporary root for ports < 1024)
2. Bind listeners
3. chroot (if configured)
4. Drop all privileges (setuid/setgid + clear groups)
5. Refuse any further privilege gain

## Resource Limits

- Max connections / streams
- Max memory per connection and global
- Max header size / count
- Finite request queues (drop on overflow)
- Rate limits per IP

Detailed diagrams and module breakdown to be added during implementation.
