# Breast Cancer Diagnosis — Deep Learning Image Classification

## 📌 Overview
- **Course:** Deep Learning — NOVA IMS (2024/25)  
- **Type:** Group Project
- **Goal:** Diagnose breast cancer from histopathology images using deep learning.  
- **Tasks:**  
  - **Binary classification**: benign vs. malignant  
  - **Multiclass classification**: breast cancer subtypes  
- **Deliverables:** Report, Jupyter notebooks, processed dataset  

Breast cancer is one of the leading causes of cancer-related deaths worldwide.  
This project aimed to build reliable convolutional neural network (CNN) models for both binary and multi-class breast cancer classification, leveraging transfer learning and optimized data pipelines.

---

## 📊 Dataset & Preprocessing
- **Source:** [BreaKHis dataset on Kaggle](https://www.kaggle.com/datasets/ambarish/breakhis) (histopathology images of breast tissue)  
- **Note:** The original dataset (~4GB) is not included in this repository due to size constraints.  
  Only the processed index file (`processed_image_data_final.csv`) is provided here for convenience.  
- **Challenge:** Strong class imbalance (malignant > benign)  
- **Preprocessing:**  
  - Resized images to 256×256 for memory efficiency  
  - Built a `tf.data` pipeline with batching and prefetch for GPU acceleration (Colab)  
  - Applied **class weights** and **augmentation** (flips) on minority classes  
- **Discarded attempts:** Reinhard color normalization, Laplacian filtering, grayscale conversion (lower performance)  


---

## 🧠 Models
- **Baseline CNN** for initial benchmarking  
- **Transfer learning:** tested EfficientNetB0, ResNet50, VGG19, MobileNetV2, NASNetMobile  
- **Best model:** **DenseNet121** (fully fine-tuned, all layers unfrozen)  
- Added **Batch Normalization**, **Dropout**, and **L2 regularization** for better generalization  
- Optimizer: Adam with **EarlyStopping** and **ReduceLROnPlateau**  

---

## 📈 Results
- **Binary classification:**  
  - F1 = **0.99** (validation/test)  
  - Train F1 = 1.00  
- **Multiclass classification:**  
  - F1 = **0.94** (validation/test)  
  - Train F1 = 0.98  
- **Main challenge:** Misclassification between **Ductal** and **Lobular** carcinoma subtypes  

---

## ▶️ How to Run
> Recommended: Google Colab with GPU (T4/A100).  
> Ensure dataset paths in notebooks are updated before running.

1. **Preprocessing**  
   - Run `notebooks/Preprocess_csv_and_build_file_structure.ipynb`  
   - Generates `data/processed_image_data_final.csv` and organizes images for `tf.data`  

2. **Binary model**  
   - Run `notebooks/Best_binary_model.ipynb`  
   - Outputs classification report, confusion matrix, and metrics  

3. **Multiclass model**  
   - Run `notebooks/Best_multiclass_model.ipynb`  
   - Evaluates per-class F1, confusion matrix, and error analysis  

---

## 🧠 Key Learnings
- Efficient **data pipeline design** is essential under compute limits  
- **Class imbalance handling** (weights + augmentation) significantly improves performance  
- **DenseNet121 fine-tuned** outperformed other CNN architectures  
- Remaining challenge: distinguishing between visually similar cancer subtypes  

---

## 🚧 Future Work
- Integrate **explainability methods** (Grad-CAM, SHAP) for medical insights  
- Explore **hybrid CNN–Transformer architectures**  
- Apply **Auto-Augment** strategies tailored to medical imaging   
