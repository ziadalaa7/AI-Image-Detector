# 🕵️‍♂️ AI-Generated vs. Real Image Detector

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=for-the-badge&logo=flask&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.9-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)

## 📖 Project Overview
With the rapid advancement of Generative AI, distinguishing between authentic photographs and AI-generated images has become a critical challenge for digital security and media authenticity. 

This project provides an **End-to-End Deep Learning solution** to detect synthetic media. It features a highly accurate Convolutional Neural Network (CNN) wrapped in a lightweight, user-friendly, and interactive web application.

---

## ✨ Key Features
- **State-of-the-Art Deep Learning:** Utilizes **EfficientNetB3** optimized via a strategic two-phase fine-tuning approach.
- **Robust Preprocessing:** Handles dataset class imbalances using mathematical `class_weights` and implements dynamic Data Augmentation to prevent overfitting.
- **Interactive Web Interface:** A sleek, drag-and-drop UI built with Vanilla JS, providing real-time visual feedback and confidence scores.
- **Seamless Integration:** Fast prediction pipeline converting OpenCV BGR format to RGB on-the-fly for accurate model inference.

---

## 🧠 Model Architecture & Training Strategy

The core of this application is a custom-trained image classification model designed to capture the subtle artifacts left by AI generators.

- **Base Architecture:** `EfficientNetB3` (pre-trained on ImageNet).
- **Custom Classification Head:** `GlobalAveragePooling2D` -> `Dropout (0.5)` -> `Dense (Sigmoid)`.
- **Two-Phase Training Protocol:**
  1. **Phase 1 (Feature Extraction):** The base model was frozen. The custom head was trained using the Adam optimizer with a learning rate of `1e-4` to adapt to the new classes.
  2. **Phase 2 (Fine-Tuning):** The top 30 layers of the base model were unfrozen. The model was recompiled with a highly conservative learning rate (`1e-5`) to fine-tune the weights without causing catastrophic forgetting of the ImageNet features.

### 📊 Performance Metrics
The model was evaluated on a strictly unseen test dataset, achieving outstanding results:
- **Accuracy:** ~94%
- **ROC-AUC Score:** 0.98+
- **F1-Score:** 0.86 for Fake (AI) / 0.91 for Real images.

---

## 🛠️ Technology Stack

| Category | Technologies |
| :--- | :--- |
| **Machine Learning & Vision** | TensorFlow, Keras, OpenCV, NumPy, Scikit-Learn |
| **Backend API** | Python, Flask, Werkzeug |
| **Frontend** | HTML5, CSS3, JavaScript (Fetch API) |

---

## 📂 Repository Structure

```text
AI-Image-Detector/
│
├── app.py                                   # Flask application & API endpoint
├── efficientnet_final_fine_tuned.keras      # Pre-trained CNN model
├── requirements.txt                         # Project dependencies
├── .gitignore                               # Git ignore file
│
└── notebooks/
    └── AI_vs_Real_Image_Detection.ipynb     # Detailed Jupyter Notebook (EDA, Training, Evaluation)
```

---

## 🚀 Getting Started

Follow these steps to set up and run the project locally on your machine.

### 1. Prerequisites
Ensure you have Python 3.8 or higher installed.

### 2. Installation
Clone this repository and navigate to the project directory:
```bash
git clone [https://github.com/ZiadAlaa/AI-Image-Detector.git](https://github.com/ZiadAlaa/AI-Image-Detector.git)
cd AI-Image-Detector
```

Install the required dependencies:
```bash
pip install -r requirements.txt
```

### 3. Running the Application
Start the Flask server:
```bash
python app.py
```

### 4. Usage
- Open your web browser and navigate to `http://127.0.0.1:5000`.
- Drag and drop any image into the upload area (or click to browse).
- Click **"Analyze Image"** to see the real-time prediction and confidence bars.

---

## 👤 Author
**Ziad Alaa**
- LinkedIn: [Ziad Alaa](https://www.linkedin.com/in/ziad-alaa-234930338/)
- GitHub: [ZiadAlaa](https://github.com/ziadalaa7)

*This project is part of a comprehensive AI Engineering portfolio and graduation project.*
