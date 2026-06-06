# Matter Server

## Purpose
Python Matter server for Home Assistant. Enables Matter/Thread device integration.

## Key Files
- `data/` - Matter server database and state

## Access
- Port: 5580 (host network mode)
- No web UI (backend service for HA)

## Dependencies
- Home Assistant (integrates as a device)
- dbus (mounted from `/run/dbus`)

## Important Notes
- Uses `network_mode: host` for mDNS discovery (required for Matter)
- Mounts `/run/dbus` for Bluetooth/Thread support
- Devices pair through HA's Matter integration
