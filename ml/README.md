# Machine Learning Workstream

Store model training scripts, feature definitions, experiment notes, and evaluation code here. Keep model binaries and private datasets out of Git by default.

## Current model integration notes

The current binary model was trained on 16 engineered numeric comparison features rather than raw documents. The inference code must preserve the exact training feature names/order and training-time missing-value medians. Package the model, feature column list, and medians together as one artifact before backend integration.

## Evaluation cautions

- The dataset is synthetic and scenarios may encode clues about the target.
- High synthetic validation/test scores are not proof of real-world performance.
- Keep a held-out set and test independently authored examples.
- Report confusion matrix, precision, recall, F1, false-match rate, and false-rejection rate.
- Missing fields and expiry/status checks may need explicit rules or a separate model; the current binary model does not automatically solve every verification outcome.