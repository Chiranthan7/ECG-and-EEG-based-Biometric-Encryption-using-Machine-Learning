# Dataset

This project uses a 5-subject multimodal physiological dataset combining ECG (Electrocardiogram) and EEG (Electroencephalogram) recordings.

## Source

The ECG signals were sourced and processed using the [PhysioNet WFDB toolkit](https://physionet.org/about/software/) (Moody, Mark, and Goldberger, 2001). The EEG features used here are realistic synthetic features generated to align per-beat with the ECG records, prepared specifically for this prototype.

The full dataset zip (`ECG_EEG_DATASET.zip`) is available in the project directory of the original Google Drive workspace. For reproduction, place the extracted folder at the path referenced by `BASE_DIR` in the notebook.

## Dataset Statistics

| Property | Value |
| --- | --- |
| Number of subjects | 5 |
| Beats per subject | 40 |
| Total beats | 200 |
| ECG sampling rate | 500 Hz |
| ECG beat window | 200 samples pre-R + 200 samples post-R (400 total) |
| ECG records per subject | 2 (`rec_1`, `rec_2`) |
| EEG features per beat | 38 (pre-extracted, CSV) |
| Fused feature vector | 89 dimensions (51 ECG + 38 EEG) |

## Expected Folder Structure

After extracting the dataset zip, the folder layout should look like:

```
ECG_EEG_DATASET/
├── Person_01/
│   ├── rec_1.dat
│   ├── rec_1.hea
│   ├── rec_1.atr
│   ├── rec_2.dat
│   ├── rec_2.hea
│   ├── rec_2.atr
│   └── EEG_person_1_realistic.csv
├── Person_02/
│   ├── rec_1.dat
│   ├── rec_1.hea
│   ├── rec_1.atr
│   ├── rec_2.dat
│   ├── rec_2.hea
│   ├── rec_2.atr
│   └── EEG_person_2_realistic.csv
├── Person_03/
│   └── ...
├── Person_04/
│   └── ...
└── Person_05/
    └── ...
```

The notebook expects `BASE_DIR` to point to the `ECG_EEG_DATASET/` root.

## File Formats

- **`.dat`** — raw ECG signal data in WFDB binary format
- **`.hea`** — WFDB header file describing channel count, sampling rate, gain, etc.
- **`.atr`** — WFDB annotation file containing R-peak locations (used for beat segmentation)
- **`EEG_person_X_realistic.csv`** — per-beat EEG feature matrix; rows correspond to ECG beats (with synchronization performed at runtime), columns are the 38 EEG features. Optionally contains a `person_label` column which is dropped before fusion.

## Important Notes

- **Privacy:** ECG and EEG are biometric health data. The dataset in this repository is for academic research and demonstration only.
- **Scale:** The 5-subject scope is a deliberate proof-of-concept boundary. For benchmark evaluation, see the public datasets recommended in the main `README.md` under [Limitations](../README.md#limitations) — PhysioNet ECG-ID, MIT-BIH, PTB, BED, and DEAP.
- **Reproducibility:** The notebook fixes `random_state=42` for the train-test split and Random Forest, so reported numbers are reproducible end-to-end given the same dataset.
