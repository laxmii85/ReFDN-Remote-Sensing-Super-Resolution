# 🛰️ Lightweight Remote-Sensing Image Super-Resolution with ReFDN

This project implements a **lightweight Remote-Sensing Image Super-Resolution (RSISR)** framework using the **Re-Parameterized Feature Distillation Network (ReFDN)**. The model is trained and evaluated on the **UC Merced LandUse dataset** and focuses on achieving a balance between **high reconstruction quality** and **efficient inference** through re-parameterization.

---

## 📌 Project Overview

Remote sensing imagery often suffers from limited spatial resolution due to sensor constraints. This project addresses this problem using a **single-image super-resolution approach**, where low-resolution (LR) images are enhanced to high-resolution (HR) outputs using a deep learning model.

The implementation includes:
- Dataset preprocessing
- ReFDN model with re-parameterization
- Training and testing pipeline
- Quantitative evaluation (PSNR, SSIM)
- Qualitative visualization of results

---

## 📂 Dataset

**UC Merced LandUse Dataset**

- Aerial RGB images across multiple land-use classes
- Widely used benchmark in remote sensing research

### 🔗 Dataset Source
The dataset can be downloaded from the official source:  
👉 https://www.kaggle.com/datasets/apollo2506/uc-merced-land-use-dataset

### Preprocessing
- **High-Resolution (HR)**: 256 × 256
- **Low-Resolution (LR)**: 64 × 64
- **Upscaling factor**: ×4
- LR images generated using bicubic downsampling

> ⚠️ The dataset is **not included** in this repository due to size constraints.

---

## 🏗️ Model Architecture

### ReFDN (Re-Parameterized Feature Distillation Network)

- Input channels: 3 (RGB)
- Feature channels: 48
- ReFDB blocks: 8
- Upsampling: PixelShuffle (×4)

### Key Components

**MultiConv (Re-Parameterizable Convolution)**
- Parallel 1×1, 3×3, and 5×5 convolutions during training
- Fused into a single 3×3 convolution at inference time

**ECSA (Efficient Channel Self-Attention)**
- Lightweight attention mechanism
- Enhances important channel-wise features

**ReFDB (Re-Parameterized Feature Distillation Block)**
- MultiConv → ECSA → MultiConv
- Residual connections for stable learning

---

## ⚙️ Training Configuration

- Epochs: 30  
- Loss Function: L1 Loss  
- Optimizer: Adam  
- Learning Rate: 2e-4  
- LR Scheduler: MultiStepLR  
- LR Decay: Halved at epochs 15 and 25  

---

## 📊 Evaluation Metrics

- PSNR (Peak Signal-to-Noise Ratio)
- SSIM (Structural Similarity Index)

### Expected Performance
- PSNR: ~25–26 dB
- SSIM: ~0.65–0.70

---

## 🖼️ Visualization

The notebook visualizes:
- Low-Resolution (LR) input
- Super-Resolved (SR) output
- Re-parameterized SR output
- Ground Truth High-Resolution (HR)

Zoomed-in regions are also shown for qualitative comparison.

---

## 🧪 Environment & Dependencies

- Python 3.13.2
- torch
- torchvision
- numpy
- pillow
- scikit-image
- matplotlib
- tqdm
- jupyter
- ipykernel

---

## 💻 Hardware Requirements

- GPU recommended
- Tested with CUDA 12.7
- For Windows users:




Dataset folders are intentionally excluded.

---

## 🚀 How to Run

1. Download the UC Merced LandUse dataset from the link above
2. Update dataset paths in the notebook
3. Run the notebook cells sequentially:
   - Data preprocessing
   - Training
   - Evaluation and visualization
4. Use the re-parameterized model for efficient inference (optional)

---

## 📚 References

- ReFDN: Re-Parameterized Feature Distillation Network for Lightweight Image Super-Resolution  
- UC Merced LandUse Dataset  

---

## 👩‍💻 Author

**Laxmi Prajapati**  
Master’s Student – Computer Engineering  
Research Interests: AI/ML, Deep Learning, Image Processing  

---

## ⭐ Acknowledgement

This project is developed for academic and research purposes, following best practices in lightweight deep learning-based super-resolution.
