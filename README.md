# SIH 2026 — AI-Powered Cross-Document Verification

A Smart India Hackathon project exploring cross-document verification using OCR, machine learning, and a web application.

> **Current status:** Project setup and integration are in progress. Model performance observed on synthetic data is preliminary and must not be treated as validated real-world accuracy.

## Project goals

- Accept two documents for verification.
- Extract relevant fields from document images/PDFs using OCR.
- Compare fields such as name, date of birth, registration number, and address.
- Return a structured result showing potential matches, differences, OCR confidence, and cases requiring manual review.
- Keep an auditable human-review step for important decisions.

## Planned structure

```text
SIH-2026/
├── frontend/          # React user interface
├── backend/           # FastAPI API, OCR and verification workflow
├── ml/                # Training scripts, feature definitions and evaluation notes
├── docs/              # Architecture, API contract and project documentation
├── datasets/          # Dataset documentation and safe, synthetic sample data only
├── .gitignore
└── README.md
```

These directories will be populated as each workstream is added.

## Team work split

- **Frontend:** build the upload and results UI; use mocked API responses until the backend is ready.
- **Backend:** expose health and verification endpoints; handle uploads, OCR, field extraction, feature engineering and inference.
- **ML:** maintain reproducible training/evaluation code and document the exact input feature schema and preprocessing.
- **Integration:** agree on request/response JSON and test the complete flow with synthetic examples.

## Planned API contract

- `GET /api/health` — report whether the API is running and required components are loaded.
- `POST /api/verify` — accept two uploaded files and return a structured verification result.

Document the exact request fields and response schema in `docs/api-contract.md` before frontend/backend integration.

## Getting started

1. Install Git.
2. Clone this repository:

   ```bash
   git clone https://github.com/Premkarthikeyan/SIH-2026.git
   cd SIH-2026
   ```

3. Create a task branch, for example:

   ```bash
   git checkout -b frontend
   ```

4. Add your work in the matching directory and commit regularly.
5. Push your branch and open a pull request for review before merging into `main`.

## Team collaboration

Invite teammates through **Settings → Collaborators** in GitHub. Since the repository is private, each teammate needs access before cloning it.

Suggested branches:

- `frontend` — React interface
- `backend` — FastAPI and OCR/integration
- `ml` — model and evaluation work

Agree on the API contract and model feature schema early. Avoid different people editing the same files on separate branches without coordinating.

## Data, model and security

- Use synthetic or otherwise approved test documents during development.
- Do not commit real identity documents, personal information, access tokens, `.env` files, or credentials.
- Do not commit large model binaries or datasets directly without agreeing on a secure artifact-storage approach.
- Add secrets through environment variables in each development/deployment environment.
- Treat model output as a preliminary signal, not proof of identity or a final institutional decision. Route uncertain or high-impact cases to authorized human review.

## Evaluation note

High metrics on synthetic data do not establish real-world performance. Evaluate against independently created test examples and document data limitations, false matches, false rejections, and missing-field handling.

## License

No license has been specified yet. Decide on a license before distributing the source code publicly.