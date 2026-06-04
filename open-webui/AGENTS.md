# Open WebUI

## Purpose
Chat interface for Ollama LLMs. Web-based UI for interacting with local AI models.

## Key Files
- `open-webui/` - Application data and user data
- `mcpo-config.json` - MCP (Model Context Protocol) configuration

## Access
- Port: 8089 (WebUI), 8088 (MCP)
- URL: http://server:8089

## Dependencies
- Ollama (LLM backend)

## Important Notes
- Two services: open-webui (chat) and mcpo (MCP server)
- MCP server uses API key: `ToP-SeCReT`
- Uses `openui-docker` network
- Can connect to multiple Ollama instances
- Auth can be enabled/disabled via environment
