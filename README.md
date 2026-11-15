# Burmese Classical Poetry Generation

An experimental deep-learning project for generating Burmese classical-style poetry from one or more complete poetic phrases.

The project uses Burmese orthographic syllable-like units rather than English-style word tokenisation. Phrase and stanza boundaries are represented explicitly with `<PHRASE_END>` and `<STANZA_END>`, allowing the models to learn flexible continuation lengths instead of enforcing a fixed 4-3-2 template.

## Project status

The notebook currently includes:

- Unicode cleaning and Burmese syllable-like segmentation
- leakage-safe stanza-level 80/10/10 train, validation and test splits
- matched LSTM and GRU encoder-decoder baselines
- a four-phrase-context GRU with additive attention
- prosody-aware and auxiliary-task ablation experiments
- structured rhyme analysis using rhyme core, coda and tone components
- a separate stanza-ending controller
- a hybrid candidate reranker for rhyme, rhythm and repetition control
- automatic and qualitative validation comparisons

This is an experimental research project. Generated poems may contain semantic drift, imperfect rhyme, repetition, or inappropriate stanza endings.

## Repository contents

| File | Purpose |
|---|---|
| `poem.ipynb` | Complete analysis, preprocessing, training and evaluation notebook |
| `burmese_classical_poetry_chunked.xlsx` | Phrase-chunked poetry dataset used by the notebook |
| `requirements.txt` | Python dependencies matching the original environment |
| `CONTRIBUTING.md` | Suggested collaboration workflow |

Model checkpoints are intentionally excluded because they are generated artifacts and make the repository unnecessarily large. They can be recreated by running the corresponding training sections.

## Environment setup

The original experiment used Python 3.10 and TensorFlow 2.10.1.

```bash
python -m venv .venv
```

Activate the environment and install dependencies:

```bash
pip install -r requirements.txt
```

Then register or start Jupyter:

```bash
python -m ipykernel install --user --name burmese-poetry
jupyter notebook poem.ipynb
```

### Native Windows GPU note

TensorFlow 2.10 is the last TensorFlow release with native-Windows NVIDIA GPU support. The original setup used compatible CUDA and cuDNN libraries. Contributors who use newer TensorFlow versions should use a currently supported platform and record any compatibility changes separately.

## Dataset structure

The workbook has no heading row. Each row contains up to five phrase cells plus a boundary field. Rows belonging to the same original poem or stanza remain in order. The notebook reconstructs complete sequences before splitting the data, preventing phrases from one reconstructed sequence from leaking between training, validation and test partitions.

## Current research priorities

- improve phonological rhyme-family mapping beyond orthographic similarity
- learn rhythm without hard-coding an exact phrase-length pattern
- reduce semantic drift over distant phrases
- preserve valid poetic repetition while preventing persistent loops
- improve stanza-ending decisions
- expand and manually verify the poetry dataset

## Reproducibility

Use the fixed random seed already defined in the notebook. Fit vocabularies and preprocessing thresholds using the training partition only. Use validation data for model selection and decoding decisions, and inspect the test partition only after the final configuration has been selected.

## Contributions

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

