# Contributing

Thank you for helping improve the Burmese classical poetry generation project.

## Recommended workflow

1. Create a new branch from `main`.
2. Make one focused change per branch.
3. Do not modify the fixed train, validation and test assignments unless the contribution specifically studies data splitting.
4. Do not use test results to tune model architecture, decoding parameters or preprocessing rules.
5. Record new dependencies in `requirements.txt`.
6. Clear accidental interactive input prompts before committing a notebook.
7. Explain the experiment, validation evidence and limitations in the pull request.

## Dataset contributions

- Preserve poem and phrase order.
- Keep one phrase per cell and use the existing boundary convention.
- Use valid Burmese Unicode rather than visually similar legacy encodings.
- Remove citation markers, Latin punctuation and unrelated annotations.
- Do not add copyrighted or private material without permission.
- Document the source and any uncertain stanza boundary in the pull request.

## Model contributions

Compare changes against the same validation examples and metrics. Useful measures include token loss, continuation MRR, Recall@5, phrase-length distribution, rhyme consistency, repetition-loop rate, termination precision/recall/F1, and qualitative relevance.

Exact agreement with a reference continuation is not required: a different continuation may still be a valid poem. Include generated examples alongside aggregate measurements.

## Generated files

Do not commit:

- model checkpoints or weight files
- notebook autosave folders
- local virtual environments
- private human-feedback responses
- temporary inspection exports
- local CUDA or environment files

