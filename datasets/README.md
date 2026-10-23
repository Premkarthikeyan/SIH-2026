# Dataset Notes

Use synthetic, licensed, or otherwise explicitly approved datasets for development.

- Do not commit real identity documents or datasets containing personal information.
- Do not add large files until the team chooses an appropriate storage method.
- Record each dataset's source, license, intended use, fields, generation method, and limitations in documentation.
- Separate train/validation/test splits and check for duplicate entities or scenario leakage.
- Do not merge unrelated datasets only to increase row count; use each dataset for the task its labels and schema actually support.