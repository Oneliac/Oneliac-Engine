# AGENTS.md

## Commands
- **Run server**: `uvicorn agents.api:app --reload --port 8000`
- **Install deps**: `pip install -r requirements.txt`
- **Type check**: `mypy agents/` (if installed)
- **Test**: `pytest` (no tests exist yet)

## Architecture
- **Framework**: FastAPI (Python 3.11) with Pydantic v2 for request/response models
- **Entry point**: `agents/api.py` - REST API with endpoints at `/health`, `/verify-eligibility`, `/validate-prescription`, `/submit-federated-update`, `/status`
- **Core logic**: `agents/main.py` - Healthcare agents (EligibilityAgent, PrescriptionAgent), ZK proof generator, federated learning coordinator, DiagnosisModel (PyTorch)
- **Dependencies**: FastAPI, uvicorn, pydantic, numpy, cryptography, aiohttp, tenacity

## Code Style
- Use dataclasses for data structures (e.g., `PatientData`)
- Use Pydantic `BaseModel` with `Field()` descriptions for API request/response models
- Async functions for I/O operations; use `tenacity` for retries
- Type hints required on all function signatures and class attributes
- Imports: stdlib first, then third-party, then local (relative imports within `agents/`)
- Handle optional PyTorch gracefully with try/except fallback to `torch_mock`
- HTTPException for API errors with descriptive messages
