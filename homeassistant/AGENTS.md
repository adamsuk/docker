# Home Assistant

## Purpose
Core home automation hub. Manages devices, automations, scenes, and integrations.

## Key Files
- `config/configuration.yaml` - Main HA config
- `config/automations.yaml` - All automations (YAML mode)
- `config/scenes.yaml` - Scenes (currently empty, scenes managed via UI)
- `config/scripts.yaml` - Scripts
- `config/.storage/` - HA internal state (entity registry, device registry, etc.)
- `homeassistant-` - Git submodule for HA config versioning

## Access
- Port: 8123 (host network mode)
- URL: http://server:8123 or https://homeassistant.sradams.co.uk

## Dependencies
- ESPHome (for ESP device management)
- Matter server (for Matter devices)
- Mosquitto (MQTT broker)
- Music Assistant (for music)

## Important Notes
- Uses `network_mode: host` for mDNS/discovery
- Automations are in YAML mode (not UI-managed)
- Entity area assignment: UI shows device-level assignment, but `area_entities()` requires entity-level `area_id` in registry
- Watchtower label is commented out (manual updates)
- Extra host mapping: `localhost:192.168.86.250`
