# Ubooquity

## Purpose
Lightweight ebook and comic server. Simple web-based reader.

## Key Files
- `config/` - Ubooquity settings and database

## Access
- Port: 2202 (web UI), 2203 (admin)
- URL: http://server:2202

## Media Mounts
- `/media/BigSlave/Books/Books` → `/books`
- `/media/BigSlave/Books/Comics` → `/comics`

## Dependencies
- Ebook/comic files on BigSlave drive

## Important Notes
- Watchtower enabled for auto-updates
- Uses `swag_proxy` network (reverse-proxied)
- MAXMEM: 2048MB
- Simpler alternative to Kavita/Booklore
- Admin interface at port 2203
