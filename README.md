# 🧠 Inference Evaluation of MedSAM-2 on Brain Tumor Segmentation - BRATS 2019

![thumbnail](https://github.com/user-attachments/assets/f64d69d3-a156-40fc-8d31-c5e0acc451fa)

## 📌 Overview

This repository implements the MedSAM-2 model for brain tumor segmentation using multi-modal MRI data. Built upon the Segment Anything Model 2 (SAM-2), MedSAM-2 introduces advanced self-sorting memory banks and a unified 2D/3D architecture, making it robust for unordered medical data and highly effective for clinical segmentation with minimal prompts.

- ✅ One-prompt segmentation
- ✅ Unified 2D/3D inference
- ✅ Medically optimized memory attention
- ✅ Dice scores >= 0.5 on test cases
- ✅ Comparison with U-Net

---

## 🗂 Project Structure

- `inference-eval-of-medsam-2-on-brain-tumor.ipynb` – Main notebook for loading the model, running inference, and visualizing results.
- `images/` – (Optional) Directory to store MRI input images, corresponding ground truths & model output predictions.
- `README.md` – Project overview and instructions.

---

## 🛠️ Features

- 🔄 Unified 2D/3D segmentation
- 🧠 Self-sorting memory mechanism for relevant embedding tracking
- 🖼️ One-prompt inference over entire volumes
- 📈 Metrics: Dice, IoU, Volume Ratios
- 🧪 Comparison with classical U-Net
- 🎨 Slice-wise visualization overlays

---
## 🧠 MedSAM-2 Architecture

MedSAM-2 extends SAM-2 with innovations tailored for medical imaging:

| Feature           | SAM-2       | MedSAM-2                   |
| ----------------- | ----------- | -------------------------- |
| Image Domain      | Natural     | Medical                    |
| Prompting         | Every image | One-prompt                 |
| Temporal Modeling | Sequential  | Memory-bank-based          |
| Memory            | FIFO        | Confidence + Dissimilarity |
| 3D Support        | No          | Yes                        |

---
## 📚 Dataset - BRATS 2019
- Modalities: T1, T1ce, T2, FLAIR
- Targets:
  - Enhancing Tumor (ET)
  - Tumor Core (TC)
  - Whole Tumor (WT)
- Samples: 335 patients (259 HGG + 76 LGG)
- Preprocessing:
  - Z-score normalization
  - 3D resizing to 128×128×128
  - Combined into 4-channel 3D volume
  - Ground truth masks resized accordingly
---
## 🚀 Results

![Dataset Overview](https://github.com/user-attachments/assets/c30fe9fa-aa6c-47b3-8532-ae8a93ef0ed6)

*Fig 1(a): Dataset Modalities Overview (BRATS-2019)*

![Preprocessed dataset](https://github.com/user-attachments/assets/3ae3babd-0011-4670-acde-9da5c179a8b5)

*Fig 1(b): Preprocessed Dataset*

![Slicing   Segmentation results](https://github.com/user-attachments/assets/ef79cfb6-a013-4ceb-b62c-f53f12cd30ac)

*Fig 2: Slicing & Segmentation Results*

![Ground truth results](https://github.com/user-attachments/assets/7a5c98e8-9f6d-4143-8ea5-7f780b897604)

*Fig 3(a): Ground Truth Results*

![Ground truth results (a)](https://github.com/user-attachments/assets/b8cbfc89-3afd-42dd-b570-f7b63dd24ade)

*Fig 3(b): Ground Truth Results*

![Overlap results (a)](https://github.com/user-attachments/assets/1d869bd4-9991-49c6-b594-f2b2108e5207)

*Fig 4: Overlaped Results*

![Inference dice and IoU score](https://github.com/user-attachments/assets/62ff9a6e-d500-4787-b99e-1d35a2a38574)

*Fig 5: Inference dice & IoU Scores*

![MedSam2   U-net Comparison](https://github.com/user-attachments/assets/e9a63a7a-25ea-4c8d-929a-48168a8537d5)

*Fig 6: MedSAM2 & U-Net Comparison*

## 📊 Evaluation Metrics

| Case                 | Dice  | IoU   | Volume Ratio |
| -------------------- | ----- | ----- | ------------ |
| BraTS19\_2013\_10\_1 | 0.514 | 0.346 | 0.50         |
| BraTS19\_2013\_11\_1 | 0.553 | 0.382 | 0.40         |
| BraTS19\_2013\_12\_1 | 0.410 | 0.258 | 0.26         |
| BraTS19\_2013\_13\_1 | 0.508 | 0.340 | 2.64         |
| BraTS19\_2013\_14\_1 | 0.447 | 0.288 | 0.29         |

## 🆚 MedSAM-2 vs U-Net

| Model    | Dice  | IoU   | Spatial Consistency |
| -------- | ----- | ----- | ------------------- |
| MedSAM-2 | 0.53  | 0.36  | 1/3 Components      |
| U-Net    | Lower | Lower | Poor Coverage       |

MedSAM-2 outperforms classical U-Net in terms of:

- Centralized segmentation accuracy
- Spatial continuity
- Robustness to bad prompts

## 🧰 Requirements

Make sure to install the required dependencies before running the notebook.

```bash
pip install torch torchvision matplotlib opencv-python nibabel
```

## 🧪 How to Use

1. Download or Clone the Repository:
```bash
git clone [https://github.com/najahaja/medsam2-brain-tumor-eval.git](https://github.com/najahaja/Inference-and-Evaluation-of-MedSAM-2-on-Brain-Tu-mor-Segmentation-BRATS-2019-)
cd Inference-and-Evaluation-of-MedSAM-2-on-Brain-Tu-mor-Segmentation-BRATS-2019-
```
2. Download Pretrained Weights:

Get the MedSAM-2 pretrained weights (link or source should be mentioned in the notebook).

3. Prepare the Dataset:

Ensure brain tumor MRI images are placed in a structured folder (images/) or directly referenced in the notebook.

4. Run the Notebook:

Launch Jupyter Lab or Jupyter Notebook and open:
```bash
jupyter notebook inference-eval-of-medsam-2-on-brain-tumor.ipynb
```
5. View Results:

Segmentation results and evaluation metrics will be displayed within the notebook.

## 📚 References

- https://colab.research.google.com/drive/1MKna9Sg9c78LNcrVyG58cQQmaePZq2k2?usp=sharing#scrollTo=FnoCVlmGIgC4
- https://github.com/bowang-lab/MedSAM2
- https://www.kaggle.com/datasets/aryashah2k/brain-tumor-segmentation-brats-2019/data

## 📌 Limitations & Future Work

- Performance varies with prompt accuracy and tumor shape
- Struggles with irregular tumors or diffuse growth
- Future goals:
  - Real-time deployment
  - Multilingual clinical inference
  - Emotion & severity conditioning



