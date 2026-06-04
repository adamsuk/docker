# Node-RED

## Purpose
Visual automation and flow programming tool. Alternative to HA automations for complex logic.

## Key Files
- Volume: `node-red-data` (Docker named volume)
- Flows stored in volume, not file-based

## Access
- Port: 1880 (host network mode)
- URL: http://server:1880

## Dependencies
- Home Assistant (HA integration nodes)
- MQTT broker (for device communication)

## Important Notes
- Uses `network_mode: host`
- Uses Docker named volume (not bind mount)
- TZ set to Europe/Amsterdam (inconsistency with other services)
- Flows can call HA services, listen to events, and control devices
