# AFF-ai-project

This is the `AFF-ai-project`, aimed at developing AI models for predicting the onset of Atrial Fibrillation and Flutter (AFF) using advanced techniques like BEHRT (Bidirectional Encoder Representation from Transformers for Electronic Health Records) and BERTopic for multimorbidity pattern identification.

## Features
- **AFF Prediction**: Utilizes deep learning techniques to predict AFF onset based on five-year pre-onset disease history.
- **Multimorbidity Analysis**: BERTopic is used to analyze and visualize disease patterns, identifying comorbidities associated with AFF across different populations.
- **Gender-Specific Disease Patterns**: Identifies cardiovascular, respiratory, and neurodegenerative disease patterns in male and female patients with AFF.



## Overview

This repository contains code for:
- **BEHRT Model**: Pre-trained transformer fine-tuned for AFF prediction  
- **BERTopic Analysis**: Gender-specific multimorbidity pattern identification

**Disease Code**: d138 (Atypical Femoral Fracture)  
**Prediction Window**: 5-year pre-onset disease history  
**Data Source**: National Health Insurance Service (NHIS) database

## Repository Structure

```
AFF-ai-project/
├── common/                     # Utility functions
├── dataLoader/                 # Custom data loaders
├── model/                      # Model definitions
├── 1.AFF_Disease_Prediction_BEHRT_Preprocessing.ipynb
├── 2.AFF_Disease_Prediction_BEHRT_MLM_Training.ipynb
├── 3.AFF_Disease_Prediction_AFF_prediction_preprocessing.ipynb
├── 4.AFF_Disease_Prediction_NDP.ipynb
├── 5.BertTopic_TSNE_class_138_100pall_5y_onset.ipynb
├── requirements.txt
└── README.md
```

## Installation

```bash
# Clone repository
git clone https://github.com/skwgbobf/AFF-ai-project.git
cd AFF-ai-project

# Create virtual environment
python -m venv AFF
AFF\Scripts\activate  # Windows
# source AFF/bin/activate  # Linux/Mac

# Install dependencies
pip install -r requirements.txt
```

## Reproducibility

### Step 1: Data Preprocessing
**Notebook**: `1.AFF_Disease_Prediction_BEHRT_Preprocessing.ipynb`

Prepare data splits from raw NHIS data:
```bash
jupyter notebook 1.AFF_Disease_Prediction_BEHRT_Preprocessing.ipynb
```

**Outputs**: 
- Training/validation/test splits (`.pkl` files)
- Vocabulary mapping (`vocab2_new.pkl`)
- Disease sequence data with 5-year pre-onset history

---

### Step 2: BEHRT Pre-training (MLM)
**Notebook**: `2.AFF_Disease_Prediction_BEHRT_MLM_Training.ipynb`

Pre-train BEHRT using Masked Language Modeling:
```bash
jupyter notebook 2.AFF_Disease_Prediction_BEHRT_MLM_Training.ipynb
```

**Model Configuration**:
- Vocab size: 252
- Hidden size: 288
- Layers: 6
- Attention heads: 12
- Epochs: 30
- Batch size: 128

**Output**: Pre-trained BEHRT weights

---

### Step 3: AFF Prediction Preprocessing
**Notebook**: `3.AFF_Disease_Prediction_AFF_prediction_preprocessing.ipynb`

Prepare data specifically for AFF prediction task:
```bash
jupyter notebook 3.AFF_Disease_Prediction_AFF_prediction_preprocessing.ipynb
```

---

### Step 4: BEHRT Fine-tuning (NDP)
**Notebook**: `4.AFF_Disease_Prediction_NDP.ipynb`

Fine-tune pre-trained BEHRT for AFF prediction:
```bash
jupyter notebook 4.AFF_Disease_Prediction_NDP.ipynb
```

**Key Steps**:
1. Load pre-trained BEHRT weights
2. Fine-tune on AFF prediction task
3. Evaluate on test set
4. Save predictions and metrics



---

### Step 5: BERTopic Multimorbidity Analysis
**Notebook**: `5.BertTopic_TSNE_class_138_100pall_5y_onset.ipynb`

Analyze disease patterns using BERTopic:
```bash
jupyter notebook 5.BertTopic_TSNE_class_138_100pall_5y_onset.ipynb
```

**Analysis**:
- Gender-stratified topic modeling
- UMAP dimensionality reduction (n_components=5)
- HDBSCAN clustering (min_cluster_size=10)
- t-SNE visualization
- Disease pattern identification

**Key Findings**:
- Males: Cardiovascular disease clusters
- Females: Osteoporosis and musculoskeletal clusters




