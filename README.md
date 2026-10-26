# Rasi

Rasi is a free-first, browser-based AI assistant starter with a FastAPI backend, a configurable model gateway, and a custom MCP server.

## Features
- Browser chat UI
- FastAPI backend
- Model gateway supporting `mock`, local `ollama`, and optional Hugging Face inference
- Custom MCP server with workspace file tools
- Explicit confirmation for file creation
- Health endpoint and basic tests

## Important
- `mock` mode lets you test the site but is not real AI.
- Ollama is optional. If used locally, the computer running it must remain on while serving requests.
- Cloud inference free tiers, availability, and quotas can change. This project cannot guarantee free inference forever.
- Free web hosting may sleep or limit resources. Add authentication and rate limiting before making tools available to the public.
- This is a starter project, not a security-audited production service.

## Run on Windows
```powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
Copy-Item .env.example .env
.\.venv\Scripts\python.exe -m uvicorn app.main:app --reload
```
Open http://127.0.0.1:8000

Default provider is `mock`. To use local Ollama, install it separately, pull a model such as `qwen2.5:3b`, and set `MODEL_PROVIDER=ollama` in `.env`.
To use Hugging Face inference, set `MODEL_PROVIDER=huggingface`, `HF_TOKEN`, and `HF_MODEL`. Provider access and free quotas depend on current terms.

## Run tests
```powershell
.\.venv\Scripts\python.exe -m pytest
```

## Run the custom MCP server
```powershell
.\.venv\Scripts\python.exe mcp_server\server.py
```
It uses stdio transport and waits for an MCP client.

## GitHub
Create an empty repository, then:
```powershell
git init
git add .
git commit -m "Initial Rasi implementation"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

## Deployment
`render.yaml` is an example deployment configuration, not a guarantee of always-on free hosting. Set secrets in the hosting provider's environment settings, never commit `.env`.
