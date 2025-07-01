# Brain-Tumor-Classification-using-Novel-Area-Attention-Mechanism
Implemented RESNet for Classification of Brain Tumour 

![WhatsApp Image 2025-07-01 at 12 07 10_cf745158](https://github.com/user-attachments/assets/a3d289b0-2ac9-4924-87eb-3c1a3ad5ca14)

## Brain‑Tumour‑Detection
*A (very) early‑stage CNN playground for binary brain‑tumour classification on CT & MRI slices.*

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

---

## Project snapshot
|                |                                                 |
| -------------- | ----------------------------------------------- |
| **Goal**       | Binary classification – *Tumour* vs *Healthy*   |
| **Data**       | [`murtozalikhon/brain-tumor-multimodal-image-ct-and-mri`](https://www.kaggle.com/datasets/murtozalikhon/brain-tumor-multimodal-image-ct-and-mri) (4 800 train / 600 test images) |
| **Model**      | Custom *ResNet* CNN with a hand‑rolled **Area‑Attention** layer |
| **Current score** | 50 % accuracy |

---

## Requirements 

numpy==1.25.0
pandas==2.1.0
Pillow==10.0.0
matplotlib==3.8.0
scikit-learn==1.3.0
imbalanced-learn==0.11.0
tensorflow==2.16.1
keras-tuner==1.4.0
kagglehub==0.3.6
tqdm==4.66.1

---

## How it works (the 30‑second tour)
1. **Data download** – one‑liner via `kagglehub` (no more ZIP‑juggling).  
2. **Pre‑processing** – resizing, normalising, and light augmentation (rotation ±15°, flips, yadda yadda).  
3. **Model** – a small ResNet backbone + my niche *AreaAttentionLayer* that forces the net to stare at contiguous square patches (because tumours are spatially coherent blobs, not random pixels).  
4. **Training** – Adam optimiser, focal loss (yes, the dataset is imbalanced), early stopping on val‑loss.  
5. **Evaluation** – standard classification report & confusion matrix. Spoiler: it currently calls “tumour” on every other scan – we can do better!

---

## Quick start
```bash
# 1. Clone the repo
git clone https://github.com/<your‑username>/Brain‑Tumour‑Detection.git
cd Brain‑Tumour‑Detection

# 2. (Optional but smart) Create a virtual‑env
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Grab the data (needs a Kaggle API token set up)
python -c "import kagglehub, os; print('Downloading...'); kagglehub.dataset_download('murtozalikhon/brain-tumor-multimodal-image-ct-and-mri')"

# 5. Fire up the notebook
jupyter notebook notebook/Brain_Tumour_Detection.ipynb
```

## Disclaimer

This repo is RESEARCH ONLY.
Do not use it to diagnose real patients or pets.
Consult a qualified radiologist.
