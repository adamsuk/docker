# Booklore

## Purpose
Modern ebook and comic reader with MariaDB backend. Alternative to Kavita with different UI.

## Key Files
- `data/` - Booklore application data
- `mariadb/config/` - MariaDB configuration
- `.env` - Database credentials (not tracked)

## Access
- Port: 6060
- URL: http://server:6060

## Media Mounts
- `/media/big_boi/Books/Books` → `/books`
- `/media/big_boi/Books/Comics` → `/comics`
- `./bookdrop` → `/bookdrop` (import folder)

## Dependencies
- MariaDB (included in compose)
- Ebook/comic files on big_boi drive

## Important Notes
- Uses MariaDB 11.4.5 for metadata storage
- Health checks configured for both services
- Environment variables from `.env` file (DB credentials)
- Bookdrop folder for automated imports
