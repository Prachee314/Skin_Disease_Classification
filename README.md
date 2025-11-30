# 🌟 Skin Disease Classification Using Transfer Learning

This project implements a **multi-class skin lesion classification system** using the **HAM10000 dermatology dataset**.  
Five ImageNet-pretrained CNN architectures were trained, fine-tuned, evaluated, and compared to identify the most effective model for dermatology image classification.  
Grad-CAM visualizations were generated to improve model interpretability—important for medical AI.

---

## 📂 Dataset: HAM10000

Dermoscopic dataset containing **10,015 images** across **7 disease classes**:

`akiec, bcc, bkl, df, mel, nv, vasc`

### **Dataset Challenges**
- 🔸 **Highly imbalanced classes**  
- 🔸 **High visual similarity** between diseases  
- 🔸 **Real-world imaging variability**  

Dataset link:  
👉 https://www.kaggle.com/kmader/skin-cancer-mnist-ham10000

---

## 🧠 Models Used (Transfer Learning)

All models were initialized with **ImageNet pretrained weights**:

- **ResNet50**
- **DenseNet121**
- **MobileNetV2**
- **EfficientNetB0**
- **InceptionV3**

### **Training Workflow**
Each model followed the same **two-stage training** pipeline:

#### ⭐ Stage 1 — Transfer Learning
- Freeze base model  
- Train classifier head  

#### ⭐ Stage 2 — Fine-Tuning
- Unfreeze last layers  
- Train with **low learning rate**  

This ensures a **fair comparison across all architectures**.

---

## 🧠 Approach

### **1️⃣ Data Processing**
- Loaded metadata and resolved image paths  
- Applied **80/20 stratified train–validation split**  
- Data augmentation: rotation, zoom, shift, brightness  
- Used **class weights** to address class imbalance  

### **2️⃣ Model Training**
- Training done in two stages (freeze → unfreeze)  
- Used Adam optimizer with separate learning rates  
- Preprocessing functions matched each architecture  

### **3️⃣ Evaluation Metrics**
- Validation Accuracy  
- Top-3 Accuracy  
- Validation Loss  
- Confusion Matrix  
- Classification Report  

---

## 📊 Model Comparison

| Model | Val Accuracy | Top-3 Accuracy |
|-------|--------------|----------------|
| ⭐ **ResNet50** | **79.48%** | **95.35%** |
| InceptionV3 | 74.29% | 92.81% |
| MobileNetV2 | 73.68% | 92.81% |
| DenseNet121 | 72.99% | 93.55% |
| EfficientNetB0 | 71.34% | 90.16% |

➡️ **ResNet50 achieved the best performance overall.**  
All models achieved **>90% Top-3 accuracy**, indicating strong ranking performance.

---

## 🔍 Model Interpretability (Grad-CAM)

Grad-CAM was used to visualize class-discriminative regions in lesion images.

**Benefits:**
- Explainability for clinical settings  
- Insight into model decision-making  
- Improved trust and transparency

## 🛠️ How to Run
### **1. Install dependencies**

```bash
pip install -r requirements.txt

### 2. Download the dataset from Kaggle

