# 🌽 Fall Armyworm Detection using Deep 


### PyCon Somalia 2025 Hackathon  
𝐓𝐞𝐚𝐦: SomByte (Somali Byte)

---

## 🚀 Project Overview
Fall Armyworm (FAW) is a pest that severely affects maize crops, threatening food security in Somalia.  
This project leverages 𝗱𝗲𝗲𝗽 𝗹𝗲𝗮𝗿𝗻𝗶𝗻𝗴 (𝗖𝗡𝗡𝘀) to automatically detect FAW in maize leaf images, helping farmers take early action.

---

## 📂 Dataset
- Provided by Zindi competition.  
- Images labeled:  
  - `0` = Healthy  
  - `1` = Fall Armyworm-infected  
- Files: `Train.csv`, `Test.csv`, `SampleSubmission.csv`, and `Images/`.

---

## 🧠 Approach
1. 𝗣𝗿𝗲𝗽𝗿𝗼𝗰𝗲𝘀𝘀𝗶𝗻𝗴: Resizing, normalization, and augmentations.  
2. 𝗠𝗼𝗱𝗲𝗹𝘀:  
   - ResNet18 @ 256px → baseline.  
   - ResNet34 @ 320px (5-fold CV) → stronger/stable.  
   - Blend (40% ResNet18 + 60% ResNet34) → reduces variance.  
3. 𝗧𝗿𝗮𝗶𝗻𝗶𝗻𝗴 𝘁𝗿𝗶𝗰𝗸𝘀:  
   - Stratified K-Fold cross-validation.  
   - Label smoothing (ε = 0.05).  
   - AdamW optimizer, cosine LR schedule, early stopping.  
   - Test-Time Augmentation (original + flips).  
4. 𝗠𝗲𝘁𝗿𝗶𝗰: Area Under ROC Curve (AUC).

---

## 📊 Results
- 𝗣𝘂𝗯𝗹𝗶𝗰 𝗟𝗲𝗮𝗱𝗲𝗿𝗯𝗼𝗮𝗿𝗱: AUC ≈ 𝟏.𝟎  
- 𝗣𝗿𝗶𝘃𝗮𝘁𝗲 𝗟𝗲𝗮𝗱𝗲𝗿𝗯𝗼𝗮𝗿𝗱 (expected): Stable, robust across folds.  
- Final submissions selected:  
  - `submission_cv5_resnet34_img320.csv`  
  - `submission_blend_r18r34_40_60.csv`

---

## 🗂 Repository Structure
pycon-2025-hackthon/
│
├── Images/ # Training & test images
├── submissions/ # Final submission CSVs
│ ├── submission_cv5_resnet34_img320.csv
│ ├── submission_blend_r18r34_40_60.csv
│
├── Train.csv
├── Test.csv
├── SampleSubmission.csv
├── maize_faw_baseline.ipynb # Colab notebook
├── maize_faw_baseline2.ipynb # Colab notebook that decided "ResNet18", "ResNet34", "Blend"
├── requirements.txt
└── README.md

---

## 📌 Reproducibility 
Seed fixed: 1337
Environment: Google Colab (T4 GPU)
Run the notebook: maize_faw_baseline2.ipynb

---

## 🌍 Impact 
Provides fast, accurate pest detection.
Supports Somali farmers and food security.
Future: mobile app deployment + expansion with local data.

---

## 👥 Team 
SomByte (Somali Byte)
1- Abdisalan Abdukadir Mohamed
2- Ibrahim Ahmed Abdirahman
3- Mohamed Dahir Ahmed

