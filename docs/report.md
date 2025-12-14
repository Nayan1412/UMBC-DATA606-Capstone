# Early Detection of Cognitive Decline Using Speech  

Prepared for **UMBC Data Science Master Degree Capstone**  
by **Nayan Allam**  
Under the guidance of **Dr. Chaojie (Jay) Wang**

- **Author:** Nayan Allam  
- **GitHub Repository:** https://github.com/Nayan1412/UMBC-DATA606-Capstone  
- **LinkedIn:** https://linkedin.com/in/nayan-allam-ba1411122  
- **Project Presentation (PPT):** https://umbc-my.sharepoint.com/:p:/g/personal/nayana1_umbc_edu/IQDK0Sa6QXk6QbXXUWeGqNIWAVO0CLFWQVM4-p9DhaCxpuQ  
- **Project Demo (YouTube):** https://youtu.be/hfkRF2D4S20  

---

## 1. Background  

Cognitive impairment, including **Alzheimer’s disease** and **mild cognitive impairment (MCI)**, is a rapidly growing global health concern. Early detection is critical, as it allows patients and caregivers to seek timely medical intervention, plan long-term care, and improve overall quality of life.

Traditional diagnostic methods rely heavily on **clinical assessments**, **neuropsychological tests**, and **memory evaluations**, which are often time-consuming and typically identify the disease only after noticeable cognitive decline has occurred.

Recent research shows that **speech patterns** change early in the progression of cognitive decline. These changes include:
- Altered language usage  
- Reduced fluency  
- Increased pauses  
- Changes in pitch, energy, and articulation  

Because speech can be collected **non-invasively** and **remotely**, it presents a promising opportunity for scalable early screening.

---

## 2. Project Objective  

The primary goal of this project is to develop a **machine learning system** that can:

- Accept **speech audio recordings** as input  
- Automatically extract **acoustic features**  
- Transcribe speech using **automatic speech recognition (ASR)**  
- Predict whether an individual shows **early signs of cognitive decline**

This system is designed as a **complete pipeline**, from raw audio to prediction, and is deployed through an **interactive Streamlit web application**.

---

## 3. Dataset  

The dataset is derived from an **open-access DementiaBank-inspired collection** and consists of audio recordings labeled as either:
- **Dementia**
- **Non-dementia (healthy controls)**

### Final Dataset Summary
- **Total samples:** 354  
- **Non-dementia:** 223 (≈63%)  
- **Dementia:** 131 (≈37%)  

### Data Columns
- `file`: Audio filename  
- `path`: Path to `.wav` file  
- `label`: Dementia or non-dementia  
- `transcript`: Automatically generated speech transcript  
- `feature_1` – `feature_30`: Acoustic speech features  

---

## 4. Audio Processing and Transcription  

Each `.wav` audio file was processed using the following steps:

1. **Audio loading** using `librosa` (16 kHz, mono)
2. **Silence trimming** to remove non-speech segments
3. **Feature extraction**, including:
   - MFCC means and standard deviations
   - Spectral centroid
   - Spectral bandwidth
   - Spectral rolloff
   - Zero-crossing rate
4. **Speech transcription** using the **OpenAI Whisper model**
5. Storing all extracted features and transcripts in a structured dataset

This process converts unstructured audio into a **machine-learning-ready tabular format**.

---

## 5. Exploratory Data Analysis (EDA)  

EDA was performed using **Plotly** to understand feature distributions and class behavior.

Key observations:
- MFCC features show approximately **Gaussian distributions**
- Spectral features exhibit **right-skewed distributions**
- Dementia and non-dementia classes overlap significantly, indicating that speech differences are **subtle**
- Class imbalance exists but is not extreme

These findings motivated advanced feature engineering and careful model evaluation.

---

## 6. Feature Engineering  

To improve model performance and interpretability, additional **engineered features** were created:

### Statistical Features
- Mean, median, min, max
- Standard deviation
- Interquartile range
- Dynamic range
- Skewness and kurtosis

### Energy-Based Features
- Total signal energy
- Signal power
- Normalized intensity

### Interaction Features
- Ratios and differences between key MFCC components
- Latent speech factors using PCA-style aggregation

These engineered features aim to capture **global speech characteristics** rather than frame-level details.

---

## 7. Train–Test Split  

The dataset was split using **stratified sampling**:
- **Training set:** 80%
- **Test set:** 20%

Stratification ensured that both dementia and non-dementia classes were proportionally represented.

---

## 8. Handling Class Imbalance (SMOTE)  

Although the class imbalance was moderate, **SMOTE (Synthetic Minority Oversampling Technique)** was applied during training to improve recall for dementia cases.

Important observation:
- SMOTE improved **recall**
- Sometimes reduced **accuracy**
- Chosen metric emphasis: **F1-score and Recall**, not accuracy

---

## 9. Machine Learning Models  

The following models were evaluated:

- Logistic Regression  
- Support Vector Machine (RBF)  
- Random Forest  
- Gradient Boosting  

All models were implemented using **pipelines** to ensure clean preprocessing.

---

## 10. Hyperparameter Tuning  

**GridSearchCV** with 5-fold cross-validation was used to optimize model performance using **F1-score** as the objective.

### Best Performing Model
- **Logistic Regression**
  - Test F1-score ≈ **0.52**
  - ROC-AUC ≈ **0.66**

This model provided the best balance between precision and recall for dementia detection.

---

## 11. Model Evaluation Summary  

Key conclusions:
- Accuracy alone is misleading for medical screening
- Logistic Regression generalized better than tree-based models
- High feature correlation limited maximum achievable performance
- Speech-based dementia detection is inherently challenging due to subtle differences

---

## 12. Pipeline and Model Packaging  

A complete **production-ready pipeline** was created using `imblearn.pipeline`:

Pipeline stages:
1. SMOTE  
2. Feature scaling  
3. Trained classifier  

The trained pipeline was saved as a **`.pkl` file** using `joblib`.

This ensures:
- Reproducibility
- Easy reuse
- Deployment readiness

---

## 13. Streamlit Application  

A **Streamlit web application** was developed to demonstrate real-world usage.

### App Workflow
1. User uploads a `.wav` audio file  
2. Audio is processed and features are extracted  
3. The saved pipeline (`.pkl`) is loaded  
4. Model outputs a **probability score**
5. A configurable **decision threshold** determines the final prediction

### Key Design Choice
A **lower threshold** was used internally to improve dementia sensitivity, ensuring subtle signals are not missed.

---

## 14. Results Interpretation  

The system is not intended as a clinical diagnosis tool, but rather as:
- An **early screening assistant**
- A **decision-support system**
- A research prototype demonstrating feasibility

The results confirm that speech contains meaningful signals related to cognitive decline, though more advanced linguistic features could further improve performance.

---

## 15. Limitations  

- Small dataset size
- Limited linguistic feature usage
- High feature correlation
- Variability in speaker accents and recording quality

---

## 16. Future Work  

- Incorporate advanced NLP features (pause duration, lexical richness)
- Use transformer-based audio embeddings
- Expand dataset size
- Perform longitudinal analysis
- Integrate clinician feedback

---

## 17. Conclusion  

This project demonstrates that **speech-based machine learning models** can assist in the **early detection of cognitive decline**. By combining signal processing, machine learning pipelines, and a user-friendly Streamlit interface, the system provides a strong foundation for future research and real-world applications.

---

**End of Report**
