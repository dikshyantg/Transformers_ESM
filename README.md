# Transformers_ESM

Utilities for building a chlorophyll-binding protein classifier from ESM embeddings.

## Repository contents

- `chlorophyll_binding_classifier`: Main Python module with a cleaned workflow for:
  - loading and filtering embedding files,
  - sampling balanced class data,
  - padding/truncating sequence embeddings,
  - splitting train/test tensors,
  - visualizing model attention heatmaps for one batch.
- `git_Chlorophyll_binding_classsifier.ipynb`: Notebook version of exploratory/training work.

## Requirements

The script expects a Python environment with at least:

- `torch`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

It also relies on a project-local helper module:

- `cus_load_embedd` (provides `create_dataloader`)

## Usage

1. Update dataset paths in `main()` inside `chlorophyll_binding_classifier`:
   - `ps_with_cl`
   - `biosynt_lst`
   - `ps_without_cl`
   - `non_ph_biosynt`
2. Ensure the model class `Chl_Classifier_5` is importable in your environment.
3. Set `model_dict_path` to your trained checkpoint (`.pt`).
4. Run:

```bash
python chlorophyll_binding_classifier
```

## Notes

- The script raises a `ValueError` if no embedding directories are configured.
- Attention visualization is produced for the first batch from the dataloader.
- Embeddings are filtered to remove labels containing `hypothetical` or `proteobact`, and to enforce a max sequence length threshold.
