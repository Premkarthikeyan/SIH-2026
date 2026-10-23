# Frontend Workstream

This folder is reserved for the React UI. The frontend can be developed independently while the backend is being built.

## Responsibilities

- Two-document upload interface
- File type and size feedback
- OCR/extraction and field comparison results
- Clear loading, empty, error, and manual-review states
- API integration through `VITE_API_BASE_URL`

## Development notes

1. Scaffold a React app in this folder (Vite is recommended).
2. Create a `.env.example` with `VITE_API_BASE_URL=http://localhost:8000`.
3. Use clearly labelled mock responses until the real FastAPI endpoint is available.
4. Never put the model file, secrets, or OCR credentials in frontend code.

See [`../docs/api-contract.md`](../docs/api-contract.md) for the current API draft.