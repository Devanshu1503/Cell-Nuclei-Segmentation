# 🔬 Cell Nuclei Segmentation with Cellpose

Instance segmentation of fluorescence microscopy cell nuclei using the **pre-trained Cellpose model**.  
This project evaluates segmentation accuracy on 50 paired images and ground-truth masks, reporting metrics such as Precision, Recall, F1, and Dice.  
It was completed as part of a technical task under Dr. Madeleine Torcasso at the University of Chicago.

---

## 📌 Project Overview
- **Goal:** Automate segmentation of cell nuclei and evaluate how well a pre-trained model generalizes.  
- **Dataset:** 50 TIFF microscopy images of nuclei, each with paired ground-truth masks.  
- **Approach:**  
  1. Normalize raw images to [0,1].  
  2. Segment nuclei using the **default/general pre-trained Cellpose model**.  
  3. Match predicted masks to ground-truth masks using IoU ≥ 0.5.  
  4. Compute instance segmentation metrics: Precision, Recall, F1, Dice.  
  5. Export per-image metrics to CSV and dataset-level averages.  

---

## ⚙️ Pipeline
1. **Preprocessing:** Normalize raw images (0–1 scale).  
2. **Segmentation:** Run Cellpose model → label masks with unique IDs per nucleus.  
3. **Evaluation:**  
   - Build an IoU matrix between predicted and ground-truth instances.  
   - Greedy matching at IoU ≥ 0.5 → TP, FP, FN.  
   - Compute **Precision, Recall, F1, Dice**.  
4. **Outputs:**  
   - CSV with per-image metrics.  
   - Dataset averages.  
   - Example overlays (for visualization).  

---

## 📊 Results
**Dataset-level averages (IoU ≥ 0.5):**  
- Precision: **0.824**  
- Recall: **0.886**  
- F1 Score: **0.846**  
- Dice: **0.876**

### Interpretation
- **High recall (0.89):** Most true nuclei are detected.  
- **Slightly lower precision (0.82):** Some false positives and merged clumps remain.  
- **Strong Dice score (0.88):** Predicted shapes closely align with ground truth boundaries.  

---

## 🔍 Limitations
- **Model choice:** Used the *general* Cellpose model, not the nuclei-specific weights.  
- **No fine-tuning:** Results could improve if Cellpose were retrained on this dataset.  
- **Small dataset:** Only 50 images; limits generalization conclusions.  

---
