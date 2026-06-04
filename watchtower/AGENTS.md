# Watchtower

## Purpose
Automatically updates Docker containers when new images are available.

## Key Files
- None (stateless)

## Dependencies
- Docker socket for container management

## Important Notes
- **Label-based**: Only updates containers with `com.centurylinklabs.watchtower.enable=true`
- `WATCHTOWER_CLEANUP=true` - removes old images after update
- `WATCHTOWER_LABEL_ENABLE=true` - opt-in mode (won't update everything)
- `WATCHTOWER_INCLUDE_RESTARTING=true` - includes restarting containers
- Update interval is commented out (defaults to 24h, or manual trigger)
