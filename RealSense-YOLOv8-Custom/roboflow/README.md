# Roboflow training steps

# 🧪 Roboflow Training Steps

This document outlines the complete process used to create and train a **custom YOLOv8 object detection model** using **Roboflow**.

---

## 📸 1. Dataset Collection

- Captured **500+ images** using a smartphone and webcam in real-world scenarios.
- Ensured variations in:
  - Lighting (day/night/indoor)
  - Backgrounds (cluttered/clean)
  - Angles and distances

---

## 🏷️ 2. Annotation in Roboflow

- Created a new project on [https://app.roboflow.com](https://app.roboflow.com)
- Labeled the following object classes:
  - `helmet`
  - `fire_extinguisher`
  - `machine`
  - `safety_gloves`
  - `wire_bundle`
- Used Roboflow’s browser-based annotation tool with keyboard shortcuts for speed.

---

## 🧪 3. Preprocessing & Augmentation

Applied the following operations using Roboflow’s pipeline:

- Auto-orient images
- Resize: **640x640** (YOLO standard)
- Augmentations:
  - Rotation ±15°
  - Brightness variation ±20%
  - Blur
  - Flip (horizontal)

---

## 🔁 4. Dataset Split

Automatically split the dataset:

- **80%** Training  
- **10%** Validation  
- **10%** Testing

---

## 🏋️ 5. Model Training

- Chose **YOLOv8 (Ultralytics)** as the model architecture
- Selected `yolov8n` variant (nano) for real-time performance on CPU
- Training settings:
  - Epochs: **100**
  - Batch size: Auto
  - Image size: 640x640
- Trained on Roboflow-hosted GPU servers

---

## 📈 6. Evaluation Metrics

After training:

- **mAP@0.5**: 92%
- Precision: 90%
- Recall: 88%
- Confusion matrix and class-wise performance available in Roboflow dashboard

---

## 📦 7. Export

- Format: **YOLOv8 PyTorch**
- Downloaded the following:
  - `best.pt` → Trained model
  - `dataset.yaml` → Class and dataset configuration

---

## 📥 8. Integration in Main Project

Copied exported files to:

- `models/best.pt`
- `roboflow/dataset.yaml`

Used in `scripts/main.py` for real-time inference with **Intel RealSense** camera.

---

## ✅ Final Result

Successfully integrated a **custom-trained YOLOv8 model** with live camera input and depth sensing, enabling:
- Accurate real-time object detection
- Depth overlay for spatial understanding
