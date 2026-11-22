# Dementia Speech Analysis

**UMBC DATA 606 capstone · Nayan Allam**

A research project exploring acoustic speech features, transcripts, and machine learning for dementia-related classification. The project combines audio analysis with tabular modeling and an exploratory Streamlit interface.

**Start here:** [Project report](docs/report.md) · [Analysis notebook](<notebook/Untitled7 (1).ipynb>) · [Recorded demo](https://youtu.be/hfkRF2D4S20)

This is an educational research prototype, not a clinically validated screening or diagnostic tool.

## Project overview

The project report describes a workflow that:

1. Processes speech recordings and extracts acoustic features such as MFCC statistics and spectral measures.
2. Generates transcripts using Whisper.
3. Explores and engineers tabular features.
4. Compares classification models and evaluates precision, recall, F1, and ROC-AUC.

See the [full report](docs/report.md) for the experimental narrative, reported results, limitations, and future work. Reported metrics have not been independently reproduced as part of this documentation update.

## What is in this repository?

| Location | Contents |
| --- | --- |
| [notebook/](notebook/) | Main analysis notebook |
| [data/combined_audio_features_transcripts.csv](data/combined_audio_features_transcripts.csv) | Combined acoustic features, labels, and transcripts |
| [app/app.py](app/app.py) | Streamlit application source, currently stored in notebook JSON format |
| [docs/report.md](docs/report.md) | Project report |
| [docs/Proposal.md](docs/Proposal.md) | Original proposal |

Raw audio recordings and a serialized inference model are not included in the current repository tree.

## Application workflow in the checked-in source

The code contained in `app/app.py` defines a feature-table demonstration:

- Load a CSV containing `feature_...` columns and a class label.
- Show dataset and class-distribution summaries.
- Train a Random Forest with an adjustable train/test split and model settings.
- Display classification metrics, a confusion matrix, and feature importance.
- Accept another feature CSV for predictions and export the results.

The `transcript` column is present in the dataset; the checked-in app selects the numeric `feature_...` columns for modeling.

## Current setup status

The application needs a small packaging repair before it can be launched as a Python script:

1. Export the code cells currently stored in `app/app.py` into a real Python file. Renaming a notebook to `.py` does not convert its contents.
2. Set its dataset path to `data/combined_audio_features_transcripts.csv` when running from the repository root. The current default only contains the filename.
3. Add and validate an application dependency file and a reproducible launch command.

The report describes an audio-upload interface with a saved model, while the checked-in application source implements a feature-CSV interface that trains a Random Forest. These should be reconciled before presenting the repository as an end-to-end audio inference app.

## Technologies

**Application source:** Python, pandas, NumPy, scikit-learn, Plotly, Streamlit  
**Additional tools described in the report:** librosa, Whisper, imbalanced-learn, Jupyter Notebook

## Research limitations

The report identifies a small dataset, correlated features, limited use of linguistic information, and variation in recordings. A stronger evaluation should also document dataset provenance, participant-level train/test separation, and external validation before making screening claims.

## Author

**Nayan Allam**  
[LinkedIn](https://linkedin.com/in/nayan-allam-ba1411122)
