# Unseen-Attack-Aware Intrusion Detection for IEC-104 Traffic

This repository contains the implementation associated with the manuscript:

**“Unseen-Attack-Aware Intrusion Detection for Smart-Grid IEC-104: A Four-Stage Hierarchical and Edge-Efficient HIDS”**

The implementation provides a hierarchical intrusion detection pipeline for identifying normal traffic, known cyberattacks, and previously unseen attacks in IEC-104 smart-grid network traffic.

## Repository Contents

```text
.
├── HIDP.ipynb
└── README.md
```

The Jupyter notebook contains the complete experimental pipeline, including data preprocessing, model training, evaluation, result visualization, and unseen-attack analysis.

## Detection Pipeline

The implementation is organized into four main stages:

1. **Attack Detection**
   Binary classification of normal and malicious traffic using a Random Forest classifier.

2. **Attack-Group Classification**
   Classification of detected attacks into DoS and non-DoS groups using feature selection, behavioral feature engineering, PCA, SMOTE, TF-IDF-based feature representation, and LightGBM.

3. **Known Attack Classification**
   Fine-grained classification of known IEC-104 attack types within the identified attack groups.

4. **Unseen-Attack Detection**
   Detection of previously unseen attack types using reconstruction-based anomaly detection and Mahalanobis-distance analysis. Leave-One-Attack-Out evaluation is used to assess generalization to attack types excluded from training.

## Attack Classes

The supervised classification stages use the following six attack classes:

### DoS attacks

* `c_ci_na_1_DoS`
* `c_se_na_1_DoS`
* `m_sp_na_1_DoS`

### Non-DoS attacks

* `c_rp_na_1`
* `c_sc_na_1`
* `c_se_na_1`

Normal network traffic is represented by the `NORMAL` label.

## Main Requirements

The notebook was developed in Python using the following main libraries:

* pandas
* NumPy
* scikit-learn
* LightGBM
* imbalanced-learn
* TensorFlow
* Matplotlib
* Seaborn

The required packages can be installed using:

```bash
pip install pandas numpy scikit-learn lightgbm imbalanced-learn tensorflow matplotlib seaborn
```

Google Colab is recommended for running the notebook.

## Dataset

The implementation expects the following training and testing files:

```text
final_train.csv
final_test.csv
```

The dataset is not included in this repository. Users must obtain the corresponding IEC-104 dataset separately and update the dataset paths in the data-loading cells of the notebook.

The original implementation uses Google Drive paths similar to:

```text
/content/drive/MyDrive/Dataset/.../final_train.csv
/content/drive/MyDrive/Dataset/.../final_test.csv
```

These paths should be replaced with the local or Google Drive locations of the downloaded dataset files.

## Running the Implementation

1. Download or clone this repository.

```bash
git clone https://github.com/USERNAME/unseen-attack-aware-iec104-ids.git
```

2. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab.

3. Install the required Python packages.

4. Place the dataset files in the desired directory.

5. Update the paths to `final_train.csv` and `final_test.csv` in the notebook.

6. Run the notebook cells sequentially from top to bottom.

The unseen-attack evaluation section may generate the following result file:

```text
stage4_loao_unseen_results.csv
```

## Notes

* The notebook is provided in its original experimental structure.
* Dataset paths may need to be adjusted before execution.
* Results may vary slightly depending on the software versions, hardware configuration, and random initialization.
* Some stages can require substantial memory and processing time.

## Citation

The associated manuscript is currently being prepared for journal submission. Citation information will be added after publication.

## Contact

**Abolfazl Rastgar Moghadam**

* GitHub: https://github.com/AbolfazlRastgar
* Personal Page: https://abolfazlrastgar.github.io/profile/
* LinkedIn: https://www.linkedin.com/in/abolfazl-rastgar/
