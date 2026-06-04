# Grott

## Purpose
Growatt solar inverter data logger. Intercepts and logs data from Growatt inverters.

## Key Files
- `grott/config/grott.ini` - Main configuration (tracked in git)
- `grott/output/` - Log output files

## Access
- Ports: 5279, 5781, 5782 (Growatt protocol ports)
- Protocol: Custom TCP (not HTTP)

## Dependencies
- Growatt inverter (configured to send data to this server)

## Important Notes
- Uses `network_mode: host` for port binding
- Config file is tracked in git (exception to usual pattern)
- `gblockcmd=True` and `gincludeall=True` for full data capture
- Logs to `/tmp/grottlog/` mapped to `grott/output/`
- Timezone synced via `/etc/localtime` and `/etc/timezone`
