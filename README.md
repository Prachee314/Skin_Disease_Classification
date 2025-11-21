# Skin Disease Classification Using Transfer learning
This project implements a multi-class skin lesion classification system using the HAM10000 dermatology dataset, leveraging transfer learning, fine-tuning, and model interpretability techniques.
Multiple pretrained CNN architectures were trained, fine-tuned, evaluated, and compared to identify the most effective model for dermatology image classification.

📂 Dataset: HAM10000

Dermoscopic dataset containing 10,015 images across 7 classes:

akiec, bcc, bkl, df, mel, nv, vasc

Challenges handled:

Highly imbalanced classes

High visual similarity among diseases

Real-world imaging variability

Dataset link:
https://www.kaggle.com/kmader/skin-cancer-mnist-ham10000

🧠 Models Used (Transfer Learning)

All models were initialized with ImageNet weights:

ResNet50

DenseNet121

MobileNetV2

EfficientNetB0

InceptionV3

Each model was trained using the same pipeline:

Stage 1: Freeze base model → train classifier head

Stage 2: Unfreeze last layers → fine-tune with low LR

This ensures a fair comparison.
