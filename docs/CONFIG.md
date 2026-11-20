# Config & Lifecycle

## Grundprinzip

Die **aktive Config** ist immer eine versteckte interne Kopie der vom Anwender gewünschten Konfiguration.  
Die vom Anwender editierte Datei wird niemals direkt verwendet.

### Ablauf
1. Anwender ändert die sichtbare Config-Datei.
2. Beim Reload (SIGHUP, Admin-Socket oder expliziter Befehl) wird die Datei gelesen und validiert.
3. Bei **erfolgreicher** Validierung wird eine neue versteckte Kopie erstellt und atomar zur aktiven Config.
4. Bei **Fehler** wird der Fehler mit **Zeilennummer und genauer Begründung** ausgegeben. Die bisherige aktive Config bleibt unverändert aktiv (kein Abbruch wie bei manchen nginx-Setups).

### Reset
- Eigener Aufruf: `--resetconfig`
- Löscht die versteckte aktive Config und erzwingt beim nächsten Start eine Neuvalidierung der Anwender-Config.
- Nur explizit, niemals automatisch.

## Matching

Die Config unterstützt **reguläre Ausdrücke auf alle vom Client gesendeten Felder** (analog nginx):
- URI / Path
- Host / SNI
- Header (beliebige)
- Methode
- Query-Parameter (optional)
- Weitere Felder nach Bedarf

Regex werden beim Laden **vorab kompiliert** (Schutz vor ReDoS und bessere Performance).

## Fallback

Für alle Anfragen, die auf **keine** konfigurierte Location / Regel passen:
- Feste, im Binary eingebettete 404-Seite
- Keine externe Datei
- Immer verfügbar, auch bei Config-Problemen oder fehlenden Upstreams

## Weitere Regeln
- Fail-Closed: Ungültige Config → alte Config bleibt aktiv + klarer Fehler.
- Hot-Reload mit Connection Draining.
- Alle Limits, Upstreams, ACME-Einstellungen, Header-Filter usw. sind über die Config steuerbar.
