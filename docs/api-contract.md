# API Contract (Initial Draft)

This document defines the first integration boundary between the React frontend and FastAPI backend. Update it with the team before considering the API stable.

## Base URL

The frontend reads the API base URL from `VITE_API_BASE_URL`. For local development, the backend is expected to run at `http://localhost:8000`.

## `GET /api/health`

Purpose: confirm the API is reachable and report readiness.

Example response:

```json
{
  "status": "ok",
  "model_loaded": false,
  "ocr_ready": false
}
```

The readiness fields must reflect actual component state; do not hard-code them as true.

## `POST /api/verify`

Content type: `multipart/form-data`

Initial request fields:

- `document_a`: required PDF or image upload
- `document_b`: required PDF or image upload

Allowed file formats for the first prototype: PDF, PNG, JPG/JPEG. The backend must validate file type and size, and should avoid logging document contents.

Example response shape (illustrative only; replace with actual extraction and model output):

```json
{
  "status": "needs_review",
  "decision": "inconclusive",
  "confidence": null,
  "documents": {
    "document_a": {"filename": "document_a.pdf", "ocr_confidence": null},
    "document_b": {"filename": "document_b.pdf", "ocr_confidence": null}
  },
  "comparisons": [
    {"field": "name", "value_a": null, "value_b": null, "result": "not_checked"},
    {"field": "date_of_birth", "value_a": null, "value_b": null, "result": "not_checked"},
    {"field": "registration_number", "value_a": null, "value_b": null, "result": "not_checked"},
    {"field": "address", "value_a": null, "value_b": null, "result": "not_checked"}
  ],
  "warnings": ["Illustrative schema; verification has not run"]
}
```

Possible `decision` values for the UI: `match_signal`, `mismatch_signal`, `inconclusive`. These are signals for review, not proof of identity.

## Error responses

Use appropriate HTTP status codes and a JSON response such as:

```json
{"detail": "A human-readable error message"}
```

The frontend should handle validation errors, unsupported formats, file-size limits, OCR failures, unavailable model artifacts, and server errors.

## Integration rules

- Mock responses are acceptable for frontend development before the backend is complete, but mark them clearly as demo data.
- Never claim verification succeeded if OCR, feature extraction, or model inference did not run.
- The current binary ML model expects a specific set of engineered numeric comparison features. Raw files cannot be sent directly to that model; OCR and field extraction plus matching feature engineering are required first.
- Store model files outside source control and load them on the backend.
- Use CORS settings limited to trusted development/production origins.
- Require authorized human review for uncertain or high-impact cases.