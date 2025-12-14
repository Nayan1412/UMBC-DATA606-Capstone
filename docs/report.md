# 1. Title and Author

**Project Title:** Early Detection of Cognitive Decline Using Speech  

Prepared for **UMBC Data Science Master Degree Capstone**  
by **Nayan Allam** under the guidance of **Dr. Chaojie (Jay) Wang**

- **Author:** Nayan Allam  
- **GitHub Repository:** https://github.com/Nayan1412/UMBC-DATA606-Capstone  
- **LinkedIn:** https://linkedin.com/in/nayan-allam-ba1411122  
- **Project Demo (YouTube):** https://youtu.be/hfkRF2D4S20  
- **Final Presentation (PPTX):**  
  https://umbc-my.sharepoint.com/:p:/g/personal/nayana1_umbc_edu/IQDK0Sa6QXk6QbXXUWeGqNIWAVO0CLFWQVM4-p9DhaCxpuQ?e=Jh1pAf  

---

## 2. Background

Cognitive impairment, including **Alzheimer’s disease** and **mild cognitive impairment (MCI)**, is a growing global health concern. Early detection is critical because it enables patients and caregivers to seek timely intervention, improve quality of life, and plan for long-term care.

Traditional diagnostic approaches rely on **clinical evaluations, memory tests, and neurological assessments**, which are often time-consuming and typically detect the condition only after noticeable cognitive decline.

Speech has emerged as a promising **biomarker** for early detection because subtle changes in:

- Language usage  
- Speech fluency  
- Acoustic and voice characteristics  

often appear during the early stages of cognitive decline.

The goal of this project is to develop a **machine learning pipeline** that analyzes **speech audio recordings** (and their transcripts) to predict whether an individual shows early signs of cognitive decline using data-driven methods.

---

## 3. Data

The dataset used in this project is derived from an **open-access DementiaBank-inspired speech collection** (likely DementiaNet). It consists of **audio recordings (.wav files)** from individuals diagnosed with dementia and healthy control subjects.

Separate datasets were maintained for:

- Dementia speech samples  
- Non-dementia (healthy control) samples  

Each audio file was processed to extract structured numerical features and speech transcripts.

### Data Structure

Each processed observation contains:

- **file** – Audio sample identifier  
- **path** – File path to the corresponding `.wav` file  
- **label** – Diagnostic group  
  - `dementia`  
  - `non-dementia`  
- **transcript** – Automatically generated speech transcription  
- **feature_1 – feature_30** – Extracted acoustic features  

---

## 4. Audio Processing and Transcript Generation

Each audio file was processed using a standardized pipeline:

- Audio loaded at **16 kHz** for consistency  
- Silence and non-speech segments removed  
- Speech transcribed using **OpenAI Whisper**  
- Transcripts stored alongside numerical features  

This step transformed raw speech into **machine-readable structured data**, enabling both acoustic and linguistic analysis.

---

## 5. Feature Extraction

From each audio file, **30 low-level acoustic features** were extracted, including:

- **Mel-Frequency Cepstral Coefficients (MFCCs)**  
- **Spectral centroid, bandwidth, and rolloff**  
- **Zero-Crossing Rate (ZCR)**  

These features capture **time-domain and frequency-domain** properties of speech associated with cognitive decline.

---

## 6. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to assess data quality, feature behavior, and class balance.

### Dataset Summary

- **Total samples:** 354  
- **Non-dementia:** 223 (62.99%)  
- **Dementia:** 131 (37.01%)

### Key EDA Observations

- No missing values in audio feature columns  
- MFCC features show approximately Gaussian distributions  
- Spectral features exhibit right-skewed distributions  
- Moderate class imbalance motivates stratified sampling and resampling  

---

## 7. Feature Engineering

To capture higher-level speech characteristics, additional engineered features were created:

- Global intensity statistics (mean, median, min, max)  
- Variability measures (standard deviation, interquartile range)  
- Energy-based features (total energy, signal power)  
- Distribution descriptors (skewness, kurtosis)  
- Normalized intensity ratios  

These features summarize speech dynamics and reduce dependence on individual MFCC coefficients.

---

## 8. Statistical Analysis

A **Welch’s t-test** was applied to engineered features to compare dementia and non-dementia groups.

### Findings

- No individual feature reached statistical significance at **p < 0.05**  
- Cognitive decline manifests as **distributed subtle changes** rather than a single dominant marker  
- Supports the use of **multivariate machine learning models**  

---

## 9. Dimensionality Reduction

**Principal Component Analysis (PCA)** was used for visualization:

- PCA plots show substantial overlap between classes  
- No clear linear separation observed  
- Confirms the complexity of speech-based cognitive detection  

---

## 10. Train–Test Splitting

The dataset was split using **stratified sampling**:

- **80% training set**  
- **20% test set**  

This preserved class proportions during evaluation.

---

## 11. Model Development

The following supervised learning models were evaluated:

- Logistic Regression  
- Support Vector Machine (RBF kernel)  
- Random Forest  
- Gradient Boosting  

To address class imbalance:

- Class-weighted learning  
- SMOTE oversampling  
- Feature scaling where required  

---

## 12. Model Evaluation

Models were evaluated using:

- Accuracy  
- Precision  
- Recall  
- F1-score  
- ROC-AUC  

**Logistic Regression** achieved the best balance between **recall and F1-score**, making it the most suitable model for dementia detection.

---

## 13. Hyperparameter Tuning

Hyperparameter optimization was performed using **GridSearchCV** with **5-fold cross-validation** and **F1-score** as the tuning metric.

- Logistic Regression achieved the highest CV F1-score  
- Tree-based models showed higher accuracy but lower dementia recall  

---

## 14. Discussion

Moderate performance reflects:

- Subtle nature of early cognitive decline  
- High feature correlation  
- Limited dataset size  

Accuracy alone was not prioritized. **Recall and F1-score** were emphasized due to the higher cost of missing dementia cases.

---

## 15. Limitations

- Limited dataset size  
- Acoustic features only (no deep linguistic modeling)  
- Speaker variability and recording conditions  
- Overlapping feature distributions  

---

## 16. Future Work

Future improvements include:

- Incorporating NLP-based transcript features  
- Deep learning models on spectrograms  
- Multimodal fusion of audio and text  
- Validation on larger clinical datasets  
- Real-time deployment using Streamlit  

---

## 17. Conclusion

This project demonstrates the feasibility of using **speech-based machine learning** for early cognitive decline detection. While performance is moderate, the results highlight speech as a **non-invasive, cost-effective screening tool** and establish a strong foundation for future research and clinical applications.
