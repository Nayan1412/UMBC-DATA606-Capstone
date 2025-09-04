1. Title and Author
Project Title: Early Detection of Cognitive Decline Using Speech
Prepared for UMBC Data Science Master Degree Capstone by Nayan Allam under the guidance of Dr. Chaojie (Jay) Wang
Author: Nayan Allam
GitHub Repo: https://github.com/Nayan1412/UMBC-DATA606-Capstone
LinkedIn: linkedin.com/in/nayan-allam-ba1411122

2. Background
Cognitive impairment, including Alzheimer's disease and mild cognitive impairment (MCI) is a growing global health concern. Early detection is significant as it allows patients and caregivers to seek early intervention improve quality of life and plan for long-term care.
Traditional diagnostic methods rely on clinical assessment and memory tests, which are lengthy and identify the condition late after significant decline. Speech, however, is emerging as a good biomarker: language usage, fluency, and voice changes generally occur during early stages of decline.
The goal of this project is to create a machine learning pipeline that takes audio recordings and transcripts of speech to predict whether an individual has early signs of cognitive decline. By connecting audio signal processing and natural language processing (NLP), we aim to identify subtle differences between at-risk patients and healthy patients.

3.Data
The dataset appears to be derived from an open-access subset of the DementiaBank-inspired collections (likely DementiaNet). It contains audio recordings (.wav files) from individuals labeled as either dementia or non-dementia.
I’ve had extracted audio recordings from the patients with dementia now I need to convert the audio files into text transcripts and collect the data 
•  Data Structure (after parsing correctly):
•	file → The audio sample identifier 
•	label → The diagnostic group:
o	dementia → Individuals with cognitive decline
o	non-dementia → Healthy control individuals
•	path → File path to the corresponding .wav audio file


