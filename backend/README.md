# Backend Workstream

This folder is reserved for the FastAPI service, OCR/file handling, field extraction, feature engineering, and model inference.

## Planned endpoints

- `GET /api/health`
- `POST /api/verify`

## Requirements

- Validate uploaded files and enforce size limits.
- Extract fields from each document with OCR/document parsing.
- Build the exact numeric features expected by the trained model.
- Return explicit `match_signal`, `mismatch_signal`, or `inconclusive`-style results only when supported by the implementation.
- Report OCR/model readiness truthfully; do not return fabricated results on pipeline failures.
- Do not log or persist sensitive document contents by default.

See [`../docs/api-contract.md`](../docs/api-contract.md) before implementing the endpoints.