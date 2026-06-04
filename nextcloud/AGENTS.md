# Nextcloud

## Purpose
Self-hosted file sync, contacts, calendar, and collaboration platform. Like a private Dropbox/Google Drive.

## Key Files
- `config/` - Nextcloud application config
- `data/` - User files and database

## Access
- Port: 8200 (HTTPS)
- URL: https://server:8200

## Mounts
- `/media/small_boi/docker/nextcloud/config` → `/config`
- `/media/small_boi/docker/nextcloud/data` → `/data`
- `/media/small_boi/Users` → `/Users`

## Dependencies
- None (standalone)

## Important Notes
- Watchtower enabled for auto-updates
- SWAG proxy network is commented out (direct access only)
- Phone backup app for photos
- Can sync contacts and calendars
- User directories mounted from small_boi/Users
