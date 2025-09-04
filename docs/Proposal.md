# 1. Title and Author  

**Project Title:** Early Detection of Cognitive Decline Using Speech  

Prepared for **UMBC Data Science Master Degree Capstone**  
by **Nayan Allam** under the guidance of **Dr. Chaojie (Jay) Wang**  

- **Author:** Nayan Allam  
- **GitHub Repo:** [UMBC-DATA606-Capstone](https://github.com/Nayan1412/UMBC-DATA606-Capstone)  
- **LinkedIn:** [linkedin.com/in/nayan-allam-ba1411122](https://linkedin.com/in/nayan-allam-ba1411122)  

## 2. Background  

Cognitive impairment, including **Alzheimer's disease** and **mild cognitive impairment (MCI)**, is a growing global health concern.  
Early detection is significant as it allows patients and caregivers to seek early intervention, improve quality of life, and plan for long-term care.  

Traditional diagnostic methods rely on **clinical assessments** and **memory tests**, which are often lengthy and tend to identify the condition only after significant decline.  

Speech, however, is emerging as a promising **biomarker**:  
- Changes in **language usage**,  
- **Fluency**, and  
- **Voice characteristics**  
often occur during the early stages of cognitive decline.  

The goal of this project is to create a **machine learning pipeline** that takes **audio recordings** and their **transcripts** to predict whether an individual shows early signs of cognitive decline.  
By combining **audio signal processing** with **natural language processing (NLP)**, we aim to identify subtle but meaningful differences between at-risk patients and healthy individuals.  


## 3. Data  

The dataset appears to be derived from an **open-access subset of the DementiaBank-inspired collections** (likely *DementiaNet*).  
It contains **audio recordings (.wav files)** from individuals labeled as either **dementia** or **non-dementia**.  

I have extracted audio recordings from patients with dementia, and the next step is to **convert the audio files into text transcripts** and collect the structured data.  

###  Data Structure (after parsing correctly):  

- **file** → The audio sample identifier  
- **label** → The diagnostic group:  
  - `dementia` → Individuals with cognitive decline  
  - `non-dementia` → Healthy control individuals  
- **path** → File path to the corresponding `.wav` audio file  



