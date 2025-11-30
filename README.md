Skin Disease Classification Using Transfer learning
This project implements a multi-class skin lesion classification system using the HAM10000 dermatology dataset, leveraging transfer learning, fine-tuning, and model interpretability techniques.
Multiple pretrained CNN architectures were trained, fine-tuned, evaluated, and compared to identify the most effective model for dermatology image classification.

#📂 Dataset: HAM10000

Dermoscopic dataset containing 10,015 images across 7 classes:

akiec, bcc, bkl, df, mel, nv, vasc

Challenges handled:

* First point Highly imbalanced classes

* Second point High visual similarity among diseases

* third point Real-world imaging variability

Dataset link:
https://www.kaggle.com/kmader/skin-cancer-mnist-ham10000

#🧠 Models Used (Transfer Learning)

All models were initialized with ImageNet weights:

• ResNet50

• DenseNet121

• MobileNetV2

• EfficientNetB0

• InceptionV3

Each model was trained using the same pipeline:

Stage 1: Freeze base model → train classifier head

Stage 2: Unfreeze last layers → fine-tune with low LR

This ensures a fair comparison.

conditions

#🧠 Approach
1️⃣ Data Processing

Loaded metadata and resolved image paths

80/20 stratified train–validation split

Applied data augmentation (rotation, zoom, shift, brightness)

Used class weights to manage imbalance

2️⃣ Model Training

Each model followed a consistent two-stage training strategy:

Stage 1 — Transfer Learning

Base model frozen

Custom classifier head trained

Stage 2 — Fine-Tuning

Unfrozen top layers

Trained with low learning rate

This ensures a fair comparison across all architectures.

3️⃣ Evaluation Metrics

Validation Accuracy

Top-3 Accuracy

Validation Loss

Confusion Matrix

Classification Report

📊 Model Comparison
Model	Val Accuracy	Top-3 Accuracy
⭐ ResNet50	79.48%	95.35%
InceptionV3	74.29%	92.81%
MobileNetV2	73.68%	92.81%
DenseNet121	72.99%	93.55%
EfficientNetB0	71.34%	90.16%

➡️ ResNet50 achieved the best overall performance.
All models exceeded 90% top-3 accuracy, indicating strong ranking ability.

#🔍 Model Interpretability (Grad-CAM)

Grad-CAM was used to visualize class-discriminative regions in lesion images.

This step provides:

• Explainability for clinical settings

• Insight into model decision patterns

• Increased trustworthiness of predictions

#🛠️ How to Run
**Install dependencies**
pip install -r requirements.txt

**Download dataset from Kaggle

Place dataset files (images + metadata) in any directory and update the paths inside the notebook.

**Run the notebook**
skin_disease_classification.ipynb
