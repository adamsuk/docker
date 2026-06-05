# Uptime Kuma

Uptime monitoring, status pages, and alerting for all your services.

## Access
- **URL**: http://192.168.86.250:3002
- **First run**: Create an admin account, then start adding monitors

## Integration with Home Assistant

### Option 1: REST API Command (Simplest)
1. Add this to your `configuration.yaml`:
```yaml
rest_command:
  uptime_kuma_alert:
    url: "http://192.168.86.250:3002/api/push/your-push-token"
```

### Option 2: Webhook Automation (Recommended)
1. In Uptime Kuma, add a monitor, then go to its Notifications → Setup → Webhook
2. Set the webhook URL to:
   ```
   http://192.168.86.250:8123/api/webhook/uptime-kuma
   ```
3. In Home Assistant, create an automation with webhook trigger:
   - Go to Settings → Automations & Scenes → Create Automation
   - Trigger type: "Webhook"
   - Webhook ID: `uptime-kuma`
   - Then add your desired action (e.g., send notification, TTS on speaker)

### Option 3: Push Monitor (Uptime Kuma monitors itself via push)
- Create a "Push" type monitor in Uptime Kuma
- HA can call the push URL via rest_command to report it's alive

## Homepage Widget
Already configured in `homepage/config/widgets.yaml` - shows all monitor statuses live.

## Recommended Monitors to Add
| Service | URL/Port | Type |
|---------|----------|------|
| Home Assistant | http://192.168.86.250:8123 | HTTP |
| Plex | http://192.168.86.250:32400/web | HTTP |
| Nextcloud | https://192.168.86.250:8200 | HTTP |
| Open WebUI | http://192.168.86.250:8089 | HTTP |
| SWAG | https://192.168.86.250 | HTTP |
| Portainer | http://192.168.86.250:9000 | HTTP |
| Mosquitto | 192.168.86.250:1883 | Port |
| Internet | 1.1.1.1 | Ping |
| DNS | 192.168.86.250:53 | Port |
