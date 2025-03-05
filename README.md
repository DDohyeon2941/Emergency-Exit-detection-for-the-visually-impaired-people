 
# Emergency Exit Detection for Visually Impaired People

## 🔍 Introduction

### 📌 Motivation
Visually impaired individuals face challenges in identifying emergency exit signs. In workplace environments, various obstacles such as doorplates, nameplates, and signboards can resemble exit signs, making emergency evacuation difficult and unsafe.

### 🎯 Purpose
This project aims to develop an **effective emergency exit detection system** for visually impaired people.  
The system provides **real-time environmental awareness and emergency exit detection**, assisting visually impaired individuals in navigating unfamiliar spaces safely.

---

## ⚙️ Method

### 🏗 Process
1. **Emergency Exit Detection Model Training**
   - Transfer Learning based on a **pretrained model**.
   - **MobileNet_V2** as the backbone (pretrained on ImageNet).
   - Retrained with a **custom indoor dataset** for emergency exit detection.

2. **Dataset**
   - **Indoor Sign Dataset (ISD)** and **Indoor Object Detection Dataset** were utilized.
   - Constructed a dataset containing emergency exit signs and other indoor signs.

3. **Experiment Design**
   - **Binary Classification:** Emergency Exit vs. Other Signs.
   - **Multiclass Classification:** Categorizing emergency exits (Exit, Directional Signs, etc.).

4. **Data Preprocessing**
   - **Addressing Data Imbalance:** Emergency exit samples were augmented.
   - **Transformations:** Normalization (1/255), resizing (224x224), horizontal/vertical flips, brightness adjustment, etc.

---

## 🧪 Experiment

### 📊 Dataset Composition
| Step  | Class                     | Train Data | Validation Data | Test Data |
|------|---------------------------|------------|----------------|------------|
| Step 1 | Emergency Exit vs. Other Signs (Binary Classification) | 600, 590  | 47, 36  | 10, 10  |
| Step 2 | Exit Arrow, Exit Here, Non-Exit (Multiclass) | 1002, 1002, 590 | 25, 12, 36 | 37, 13, 324 |

### 🔢 Experiment Settings
- **Batch Size:** 64
- **Epochs:** 20
- **Evaluation Metric:** AUROC
- **Early Stopping:** Stops training if validation loss increases for 3 consecutive epochs.

---

## 📈 Results

### 🎯 Model Performance
- **Step 1 (Binary Classification: Emergency Exit vs. Other Signs)**
  - AUROC (Validation Data): **0.95**
  - Continuous decrease in loss and increase in AUROC.

- **Step 2 (Multiclass Classification: Exit Arrow, Exit Here, Non-Exit)**
  - AUROC (Validation Data): **0.9538**
  - Loss increased, AUROC decreased → Requires more data.

### 🔍 Model Prediction Performance (Confusion Matrix)
#### Step 1 (Binary Classification)
| Actual | Predicted: Emergency Exit | Predicted: Other Signs |
|--------|--------------------------|-----------------------|
| Emergency Exit | 10 | 0 |
| Other Signs | 1 | 9 |

#### Step 2 (Multiclass Classification)
| Actual | Predicted: Exit Arrow | Predicted: Exit Here | Predicted: Non-Exit |
|--------|----------------------|----------------------|----------------------|
| Exit Arrow | 43 | 3 | 1 |
| Exit Here | 4 | 14 | 0 |
| Non-Exit | 10 | 3 | 310 |

---

## 🚀 Inference & Deployment
- **Inference Speed:** ~140-150ms on average.
- **Inference Performance:** Recognition accuracy drops when backgrounds include ceilings, walls, or windows.

---

## 🔮 Future Work
- **Incorporating exit sign directionality** → To improve route guidance.
- **Expanding dataset** → To mitigate class imbalance.
- **Deploying lightweight models** → For mobile and embedded applications.

---
