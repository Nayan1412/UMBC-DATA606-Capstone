# UMBC-DATA606-Capstone docs

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
