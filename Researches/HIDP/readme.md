# HIDP: Hierarchical Intrusion Detection Pipeline for IEC-104 Smart-Grid Substations

This repository contains the implementation and processed experimental data associated with the manuscript:

**“A Hierarchical Intrusion Detection Pipeline for IEC 60870-5-104 Smart-Grid Substations with Unseen-Attack Detection”**

The project implements a four-stage intrusion detection pipeline for IEC 60870-5-104 smart-grid substation traffic. The pipeline is designed to identify normal traffic, classify known cyberattack patterns, and detect previously unseen attack behaviors using a combination of lightweight supervised models and reconstruction-based anomaly detection.

## Repository Contents

```text
.
├── HIDP.ipynb
└── README.md
```

The Jupyter notebook contains the experimental workflow, including data loading, preprocessing, feature preparation, model training, evaluation, result visualization, and unseen-attack analysis.

The processed train/test files used in the experiments are provided separately through Google Drive links because of file-size limitations on direct GitHub upload.

## Processed Dataset

The implementation expects the following processed files:

```text
final_train.csv
final_test.csv
```

The processed files used in the manuscript are available here:

- `final_train.csv`: https://drive.google.com/file/d/1vywbVHqNe12xEApRyNMWDlSZGxYPXZ2j/view?usp=drive_link
- `final_test.csv`: https://drive.google.com/file/d/1u-FsdFBP9F6SFgRggiUj2kAzqzrlF7UP/view?usp=drive_link

These files are the processed train/test datasets used for reproducing the experiments reported in the manuscript. They are derived from the IEC-104 smart-grid traffic dataset used in the study and are provided to support reproducibility of the reported results.

Users should download both files and update the dataset paths in the notebook before running the implementation.

Example path variables in the notebook may need to be changed to match the local or Google Drive location of the downloaded files:

```text
/path/to/final_train.csv
/path/to/final_test.csv
```

## Detection Pipeline

The implementation follows a four-stage hierarchical intrusion detection design.

### Stage 1: Initial Attack Detection

The first stage performs binary classification between normal and suspicious/malicious IEC-104 traffic windows.

### Stage 2: Coarse Attack Categorization

The second stage separates detected malicious traffic into coarse attack groups, particularly DoS and non-DoS categories.

### Stage 3: Known Attack Classification

The third stage performs fine-grained classification of known IEC-104 attack classes using supervised learning.

### Stage 4: Unseen-Attack Detection

The fourth stage detects previously unseen attack behaviors using reconstruction-based anomaly detection and Mahalanobis-distance scoring. This stage is intended to evaluate whether attack patterns excluded from the anomaly detector’s training process can still be identified as abnormal.

## Attack Classes

The supervised stages use the following IEC-104 attack classes.

### DoS attacks

- `c_ci_na_1_DoS`
- `c_se_na_1_DoS`
- `m_sp_na_1_DoS`

### Non-DoS attacks

- `c_rp_na_1`
- `c_sc_na_1`
- `c_se_na_1`

Normal network traffic is represented by the `NORMAL` label.

## Main Requirements

The notebook was developed in Python using common scientific computing and machine learning libraries, including:

- pandas
- NumPy
- scikit-learn
- LightGBM
- imbalanced-learn
- Matplotlib
- Seaborn

Depending on the notebook version, a deep-learning library may also be required for the autoencoder-based unseen-attack detection stage.

The main packages can be installed using:

```bash
pip install pandas numpy scikit-learn lightgbm imbalanced-learn matplotlib seaborn
```

If the notebook uses TensorFlow or PyTorch for the autoencoder stage, install the corresponding package as required by your runtime environment.

For TensorFlow:

```bash
pip install tensorflow
```

For PyTorch, follow the installation command recommended for your system from the official PyTorch website.

Google Colab is recommended for running the notebook.

## Running the Implementation

1. Clone this repository:

```bash
git clone https://github.com/AbolfazlRastgar/academic-portfolio.git
```

2. Navigate to the HIDP project directory:

```bash
cd academic-portfolio/Researches/HIDP
```

3. Download the processed dataset files:
  

- `final_train.csv`
  
- `final_test.csv`
  

4. Open `HIDP.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
  
5. Update the dataset paths in the data-loading cells.
  
6. Run the notebook cells sequentially from top to bottom.
  

The unseen-attack evaluation section may generate the following result file:

```text
stage4_loao_unseen_results.csv
```

## Reproducibility Notes

- The notebook is provided in its experimental research structure.
- Dataset paths must be updated before execution.
- Results may vary slightly depending on package versions, hardware configuration, and random initialization.
- Some stages may require substantial memory and processing time.
- Google Colab is recommended for easier execution with large CSV files.

## Data Availability Statement

The implementation code is available in this repository. The processed train/test files used in the experiments are available through the Google Drive links provided in the “Processed Dataset” section. The processed files are derived from the IEC-104 smart-grid traffic dataset used in the manuscript and are shared to support reproducibility of the reported experiments.

## Citation

The associated manuscript is currently under journal submission. Citation information will be added after publication.

## Contact

**Abolfazl Rastgar Moghadam Cheraghi**

- GitHub: https://github.com/AbolfazlRastgar
- Personal page: https://abolfazlrastgar.github.io/profile/
- LinkedIn: https://www.linkedin.com/in/abolfazl-rastgar/
