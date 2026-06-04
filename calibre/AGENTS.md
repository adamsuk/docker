# Calibre

## Purpose
Ebook management application. Organizes, converts, and serves ebook libraries.

## Key Files
- `/media/BigSlave/Books` → `/config` (library location)

## Access
- Port: 8080 (web UI), 8081 (content server)
- URL: http://server:8080

## Dependencies
- Ebook files on BigSlave drive

## Important Notes
- PUID/PGID use placeholder syntax `{PUID}` (may need fixing)
- Restart policy is commented out (not auto-restarting)
- Web UI for managing library
- Content server at 8081 for reading/downloading books
