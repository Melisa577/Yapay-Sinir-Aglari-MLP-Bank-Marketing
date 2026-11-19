# Yapay Sinir Ağları — MLP ile Bank Marketing Sınıflandırması

Yüksek lisans ara sınav projesi. Öğrenci numarası son 5 hane: **12902**, temel seed: **14928**.

## Dataset
UCI Bank Marketing, **bank-additional.csv** (4,119 observations). `duration` excluded. Source: https://archive.ics.uci.edu/dataset/222/bank+marketing (DOI: 10.24432/C5K306).

## Execution
Recommended: open `MLP_Midterm_14928_Colab.ipynb` in Google Colab and run sequentially. `01_eda.ipynb`, `02_nested_cv.ipynb`, `03_final_test.ipynb` are sequential excerpts and require the **same active Colab runtime** (not independently restartable). Install packages listed in `requirements.txt` if necessary.

**Do not execute the final test scoring cell until the unlabeled predictions, final configuration and code have been committed to GitHub in a separate commit.** The test metrics and figures in this package were generated from the supplied run. The original commit chronology must be checked against the GitHub history; adding these files now cannot retroactively prove the lock.

## Method
80/20 stratified split; 3 outer folds, 3 inner folds; 6 predefined manual and 6 random candidates (2 per optimizer); PyTorch MLP with BCEWithLogitsLoss, early stopping and optional ReduceLROnPlateau; fold-local preprocessing. Test predictions locked for three fixed seeds. Independent test is evaluated only after lock.

## Structure
- `configs/`: fixed candidate settings
- `results/`: split, fold-level results, training logs, locked predictions, metrics
- `figures/`: generated plots
- `report.pdf`: Turkish report **draft requiring review**
- `requirements.txt`: required libraries (unpinned; actual versions recorded in `results/environment.json`)

## Reproducibility and limitations
- Compare `results/environment.json` with your runtime; library version changes can affect outputs.
- The dataset has no person identifier; random split does not prove customer-independent or temporal generalization.
- Do not select a model based on the independent test performance.
- `report.pdf` is a draft; inspect all tables and cross-references before submitting.

## Sources
- Moro, Rita, Cortez (2014), Bank Marketing, UCI, DOI 10.24432/C5K306.
- scikit-learn: https://scikit-learn.org/stable/
- PyTorch: https://pytorch.org/docs/stable/
