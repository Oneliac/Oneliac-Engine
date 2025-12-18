# Oneliac API

Privacy-preserving healthcare agents REST API with zero-knowledge proofs.

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run locally
uvicorn agents.api:app --reload --port 8000

# Open docs
open http://localhost:8000/docs
```

## Deploy to Render

1. Push this repo to GitHub
2. Connect to Render
3. It will auto-detect `render.yaml`

Or use the Render dashboard:
- **Type**: Web Service
- **Build Command**: `pip install -r requirements.txt`
- **Start Command**: `uvicorn agents.api:app --host 0.0.0.0 --port $PORT`

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/health` | GET | Health check |
| `/verify-eligibility` | POST | Check insurance eligibility |
| `/validate-prescription` | POST | Validate prescription safety |
| `/submit-federated-update` | POST | Submit FL training round |
| `/status` | GET | System status |
| `/docs` | GET | Interactive API docs |

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SOLANA_ENDPOINT` | `https://api.devnet.solana.com` | Solana RPC endpoint |
| `PORT` | `8000` | Server port |
