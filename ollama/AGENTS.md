# Ollama

## Purpose
Local LLM inference server. Runs large language models locally for AI tasks.

## Key Files
- `/media/BigSlave/Sandbox/ollama` → `/root/.ollama` (model storage)
- Custom app in `./src/` (FastAPI wrapper)

## Access
- Port: 7869 (API), 8000 (custom app), 5678 (debug)
- URL: http://server:7869

## Dependencies
- Open WebUI (chat interface)

## Important Notes
- `OLLAMA_KEEP_ALIVE=24h` keeps models loaded
- Models stored on BigSlave drive (large storage)
- Custom FastAPI app in `./src/` with hot reload
- Uses `ollama-docker` network for internal communication
- `pull_policy: always` ensures latest Ollama image
