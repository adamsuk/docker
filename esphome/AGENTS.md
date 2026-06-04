# ESPHome

## Purpose
Manages ESP8266/ESP32 devices for Home Assistant. Compiles and uploads firmware to ESP devices.

## Key Files
- `config/` - ESPHome device configurations (YAML files per device)
- `config/secrets.yaml` - WiFi passwords, API keys (not tracked)

## Access
- Port: 6052 (host network mode)
- URL: http://server:6052

## Dependencies
- Home Assistant (devices integrate into HA)
- Network access to ESP devices

## Important Notes
- Uses `network_mode: host` for device discovery
- `privileged: true` for USB serial access
- Config files define each ESP device's behavior
- Devices can be OTA-updated from the web UI
