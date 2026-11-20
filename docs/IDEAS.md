# Additional Ideas & Open Points (for iterative refinement)

## Config & Lifecycle (neu)
- Versteckte aktive Config-Kopie
- `--resetconfig`
- Fehler mit Zeile + Grund, alte Config bleibt aktiv
- Regex auf alle Client-Felder
- Eingebettete 404-Seite

## Security
- Landlock + seccomp nach Privilege Drop
- Quarantine-Modus bei verdächtigen Mustern
- Memory/FD-Pressure-Handling
- Zertifikats-Backup / Fallback-Zertifikat
- Request-ID durch den gesamten Pfad

## Operations
- Dry-Run / Check-Mode
- Connection Draining bei Reload und Shutdown
- Lightweight Upstream Health Checks
- systemd Sandboxing-Direktiven

## Weitere offene Punkte
- Early Hints (103)
- Mehrere Zertifikate pro Listener (SNI)
- Log-Sampling
- CT-Log-Überwachung (optional)

Diese Liste ist bewusst offen für weitere Überarbeitung vor Implementierungsstart.
