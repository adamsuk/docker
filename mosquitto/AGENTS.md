# Mosquitto (MQTT Broker)

## Purpose
MQTT message broker for IoT device communication. Used by Home Assistant and other services.

## Key Files
- `config/mosquitto.conf` - Broker configuration
- `config/passwd` - User credentials (not tracked)
- `data/` - Persistent message store
- `log/` - Broker logs

## Access
- Port: 1883 (host network mode)
- Protocol: MQTT (not HTTP)

## Dependencies
- Home Assistant (MQTT integration)
- Other MQTT clients (ESPHome, Node-RED, etc.)

## Important Notes
- Uses `network_mode: host` for reliable client connections
- Authentication required (passwd file)
- Used for real-time device communication
