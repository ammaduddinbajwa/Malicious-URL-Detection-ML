# Malicious URL Detection Using Machine Learning

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![scikit--learn](https://img.shields.io/badge/scikit--learn-Random%20Forest-F7931E?logo=scikitlearn&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-Gradient%20Boosting-02569B)
![XGBoost](https://img.shields.io/badge/XGBoost-Gradient%20Boosting-EC1C24)
![Accuracy](https://img.shields.io/badge/Best%20Accuracy-96.6%25-2EA44F)

Supervised machine learning classifiers trained to detect malicious URLs (phishing, malware, defacement) at scale, benchmarked against a 650K+ URL dataset.

**At a glance**
- Benchmarked **Random Forest, LightGBM and XGBoost** on 651,191 real-world URLs across 4 classes: benign, defacement, phishing, malware.
- Engineered 15+ URL-structure features (IP usage, Google index, special-character counts, length, etc.) with encoding, normalisation and dimensionality reduction.
- **Random Forest reached 96.6% accuracy** (best overall), LightGBM 95.6%, XGBoost 93.2% — full precision/recall/F1 breakdown below.
- Full write-up and figures in [report.pdf](report.pdf). No standalone executable code or notebook is currently published.

## Published Materials and Evaluation Limits

This repository currently contains this README and `report.pdf`; it does not include a runnable training notebook, dependency file, dataset snapshot, or saved predictions. Metrics below are reported results and have not been independently reproduced from repository code.

The documented methodology mentions binary label mapping, while the results present four classes. These must be reconciled against the original experiment before treating the metrics as a reproducible benchmark. The originally listed per-class correct-prediction counts have been omitted here because their relationship to the stated dataset distribution and 80/20 split is unclear.

## Overview
This project explores the use of machine learning algorithms to detect malicious URLs, addressing limitations of traditional blacklist methods. Malicious URLs pose significant cybersecurity threats, leading to scams like phishing, spam, and malware distribution. The study formalizes the problem as a classification task and evaluates models such as Random Forest, LightGBM, and XGBoost on a large dataset. It includes data preprocessing, feature engineering, model training, and performance analysis to achieve high detection accuracy.

This work is useful for cybersecurity professionals and ML researchers, providing insights into system design and future directions.

**Key Skills Demonstrated:**
- Machine Learning (Supervised Classification, Gradient Boosting)
- Feature Engineering and Preprocessing (Encoding, Normalization, Dimensionality Reduction)
- Model Evaluation (Accuracy, Precision, Recall, F1 Score, Confusion Matrix, Feature Importance)
- Python Libraries (Scikit-learn, LightGBM, XGBoost, Matplotlib for Visualization)
- Data Analysis (Word Clouds, Dataset Exploration)

## Dataset
The dataset is sourced from Kaggle[](https://www.kaggle.com/datasets/sid321axn/malicious-urls-dataset) and contains 651,191 URLs classified into four categories:
- Benign: 428,103
- Defacement: 96,457
- Phishing: 94,111
- Malware: 32,520

The dataset has no null values and includes columns for URL and label.

## Methodology
### Preprocessing
- Remove missing data (none present).
- Extract features to reduce dimensionality.
- Encode categorical features (e.g., IP address, Google Index) using count encoding.
- The report summary mentions mapping Benign to 0 and other categories to 1. The four-class result tables below require a separate label setup; the final experimental configuration needs verification.
- Normalize data to rescale values between 0 and 1, handling outliers.
- Split data: 80% training, 20% testing.

### Feature Extraction
Features are engineered to improve model performance. Key features include:

| Features              |
|-----------------------|
| Use of IP             |
| Google Index          |
| Count(.)              |
| Count(www)            |
| Count(@)              |
| Count(dir)            |
| Count(embed_domain)   |
| Count(http)           |
| Count(%)              |
| Count(?)              |
| Count(-)              |
| Count(=)              |
| URL length            |
| Hostname length       |
| Count(Digits)         |
| Count(letters)        |

Techniques like PCA and LDA are mentioned for dimensionality reduction.

### Models
Three classifiers are implemented using Scikit-learn:
- **Random Forest Classifier**: Ensemble method for classification and regression.
- **LightGBM Classifier**: Gradient boosting framework for efficiency and performance.
- **XGBoost Classifier**: Optimized gradient boosting library for high accuracy.

Hyperparameters are tuned to optimize metrics like accuracy, precision, recall, and F1 score.

## Results and Analysis
Simulations were run on Google Colab.

### Reported Performance Metrics
- **Random Forest**: 96.6% accuracy

- **LightGBM**: 95.6% accuracy

- **XGBoost**: 93.2% accuracy

#### Precision Analysis
| Algorithm      | Benign | Defacement | Phishing | Malware |
|----------------|--------|------------|----------|---------|
| Random Forest  | 0.97   | 0.98       | 0.99     | 0.91    |
| LightGBM       | 0.97   | 0.96       | 0.96     | 0.90    |
| XGBoost        | 0.95   | 0.89       | 0.92     | 0.88    |

#### Recall Analysis
| Algorithm      | Benign | Defacement | Phishing | Malware |
|----------------|--------|------------|----------|---------|
| Random Forest  | 0.98   | 0.99       | 0.94     | 0.86    |
| LightGBM       | 0.99   | 0.99       | 0.89     | 0.81    |
| XGBoost        | 0.98   | 0.96       | 0.76     | 0.73    |

#### F1 Score Analysis
| Algorithm      | Benign | Defacement | Phishing | Malware |
|----------------|--------|------------|----------|---------|
| Random Forest  | 0.98   | 0.99       | 0.96     | 0.88    |
| LightGBM       | 0.98   | 0.97       | 0.92     | 0.85    |
| XGBoost        | 0.97   | 0.92       | 0.83     | 0.80    |

The reported results rank Random Forest highest by overall accuracy. These comparisons remain provisional until the label mapping, test-set composition, and original evaluation outputs are reconciled.

Visualizations include confusion matrices, feature importance graphs, and word clouds (refer to figures in the attached document).

## References
1. P. Prakash et al., "PhishNet: Predictive blacklisting to detect phishing attacks," IEEE INFOCOM, 2010.
2. Dharmaraj Rajaram Patil and JB Patil, "Survey on Malicious Web Pages Detection Techniques," International Journal of u-and e-Service, Science and Technology, 2015.
3. Schultz et al., "Data Mining Methods for Detection of New Malicious Executables," IEEE Symposium on Research in Security and Privacy, 2001.
4. Bai et al., "A Malware Detection Scheme Based on Mining Format Information," Sci. World J., 2014.
5. Moser et al., "Limits of Static Analysis for Malware Detection," Annual Computer Security Applications Conference, 2007.
6. Mohanta and Saldanha, "Malware Analysis and Detection Engineering," Apress, 2020.
7. Rakesh Verma et al., "What’s in a URL: Fast Feature Extraction and Malicious URL Detection," ACM Conference on Data and Application Security and Privacy, 2017.
8. Kaggle Dataset: https://www.kaggle.com/datasets/sid321axn/malicious-urls-dataset

For detailed figures (e.g., flowcharts, code snippets, confusion matrices), code implementations, and full analysis, refer to the attached [report.pdf](report.pdf).

This project demonstrates practical ML applications in cybersecurity, ideal for roles in data science, security engineering, or AI research.

---

**Ammad Ud Din Bajwa** — MSc Cybersecurity, National College of Ireland · SOC Analyst | Incident Response | Cybersecurity Operations
[LinkedIn](https://www.linkedin.com/in/ammaduddinbajwa) · [GitHub](https://github.com/ammaduddinbajwa) · ammaduddinbajwa702@gmail.com
