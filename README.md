# xApp-Methodology
 
> **Behavioral anomaly detection for xApps operating within the O-RAN SDL environment**
 
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Dataset Notebook](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/xApp-Methodology/blob/main/colab/O_RAN_xapp_dataset.ipynb)
[![Training Notebook](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/xApp-Methodology/blob/main/colab/O_RAN_xapp_training.ipynb)
[![Google Drive](https://img.shields.io/badge/Google%20Drive-Dataset-4285F4?logo=googledrive&logoColor=white)](https://drive.google.com/drive/folders/1mZLco7DwN_MmVm-kf78-lYN1XyZdEsJj)
[![Google Drive](https://img.shields.io/badge/Google%20Drive-xApp%20Testing%20Environment-4285F4?logo=googledrive&logoColor=white)](https://drive.google.com/drive/folders/1y097sdQFyaK8uLLovHTtZw9GyMPCs8cA?usp=sharing)
---
 
## Overview
 
This repository presents the methodology and associated datasets for a security-oriented xApp monitoring framework designed for the **Open Radio Access Network (O-RAN)** architecture. The proposed approach leverages behavioral analysis to detect anomalous or potentially malicious xApp activity within the **Shared Data Layer (SDL)** — a critical communication substrate of the O-RAN near-real-time RAN Intelligent Controller (near-RT RIC).
 
---
 
## Motivation
 
The disaggregated nature of O-RAN introduces significant operational flexibility, but also expands the attack surface of mobile network infrastructure. xApps, being third-party applications deployed directly into the near-RT RIC, represent a particularly sensitive threat vector: a compromised or malicious xApp can manipulate RAN parameters, exfiltrate telemetry, or disrupt network operations at scale.
 
This work addresses the need for a **runtime behavioral security mechanism** that learns and enforces expected xApp behavior patterns through data-driven inference over SDL interactions.
 
---
 
## Repository Structure
 
```
xApp-Methodology/
│
├── colab/
│   ├── O_RAN_xapp_dataset.ipynb     # Dataset construction and preprocessing pipeline
│   └── O_RAN_xapp_training.ipynb    # Model training, evaluation, and inference
│
├── refined_dataset/                 # Processed and structured dataset (ready for training)
│
├── session_1_32HR/                  # Raw session data — 32-hour collection window
├── session_2_16HR/                  # Raw session data — 16-hour collection window
│
├── inference_results.json           # Output of the inference pipeline on collected sessions
├── LICENSE                          # MIT License
└── README.md
```
 
---
 
## Datasets
 
### Raw Session Data
 
The raw session data was collected directly from an O-RAN SDL environment under controlled conditions, capturing xApp interaction events over two independent time windows.
 
| Folder | Duration 
|---|---|
| `session_1_32HR/` | 32 hours |
| `session_2_16HR/` | 16 hours | 
 
Each session contains timestamped records of xApp interactions with the SDL, including read, write, and subscription events along with associated metadata.

---

### Refined Dataset

The `refined_dataset/` directory contains the final processed dataset, split into dedicated training and testing files. Each split preserves data from both collection sessions — the 32-hour and 16-hour windows — and exposes **33 features** per sample, spanning:

- Operation counts
- Timing statistics
- Key diversity metrics
- Churn rates
- Spectral properties of the operation rhythm

This is the dataset consumed directly by the training pipeline. Researchers wishing to reproduce results without rerunning the full preprocessing pipeline should use this directory as their starting point or the google drive fetch already in the code distributed.

---
 
## Notebooks
 
Two notebooks live in `colab/` and are designed to run end-to-end with no local setup required.
 
| Notebook | Purpose |
|---|---|
| `O_RAN_xapp_dataset.ipynb` | Loads raw sessions, extracts features, exports the refined dataset |
| `O_RAN_xapp_training.ipynb` | Trains the model, evaluates performance |
 
---
 
## Quickstart
 
###  Google Colab
 
#### Step 1 — Open a notebook
 
Click a badge to open directly in Colab:
 
- **Dataset pipeline:** [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/xApp-Methodology/blob/main/colab/O_RAN_xapp_dataset.ipynb)
- **Training & inference:** [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/xApp-Methodology/blob/main/colab/O_RAN_xapp_training.ipynb)

Or go to [colab.research.google.com](https://colab.research.google.com), choose **File → Open notebook → GitHub**, and paste:
 
```
https://github.com/j3les-0/xApp-Methodology
```
 
#### Step 2 — Run all cells
 
Go to **Runtime → Run all** (or `Ctrl+F9`). The notebook will execute top to bottom.

 
---
 
 
## Inference Results
 
The file `inference_results.json` contains the output of the inference made by the model running in the RIC envyroment.
 
---


## License
 
This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.
 
---
