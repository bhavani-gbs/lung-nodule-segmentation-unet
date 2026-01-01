CT-Based Lung Nodule Segmentation using 2D U-Net
------------------------------------------------
Objective:
----------
This project focuses on reducing false negatives in lung cancer detection
by performing pixel-level lung nodule segmentation on CT scan slices.
Since missing a malignant nodule has serious clinical consequences,
the model prioritizes recall (sensitivity) over accuracy.

Dataset:
--------
LIDC-IDRI (slice-wise PNG format)

Multiple radiologist annotations per slice

Annotations combined using union (OR) strategy to reduce false negatives

A pixel is considered a nodule if any radiologist marked it.

Methodology:
------------
2D U-Net architecture for segmentation

Dice loss to handle class imbalance

Patch-based training with padding for variable image sizes

Recall-based early stopping

FN-aware thresholding (0.35)

Evaluation Metrics
------------------
Dice Score

Recall (Sensitivity)

Pixel-level Confusion Matrix (TP, FP, FN, TN)

Results
-------
| Metric     | Value    |
| ---------- | -------- |
| Dice Score | **0.73** |
| Recall     | **0.76** |

These results reflect realistic performance given the small size of nodules
and inter-observer variability in the LIDC-IDRI dataset.

Explainability
--------------
Pixel-level segmentation masks are overlaid on CT slices
to improve clinical interpretability.

How to Run:
-----------
pip install torch torchvision numpy matplotlib opencv-python tqdm
    Open and run:lung_nodule_segmentation_unet.ipynb

Note
-----
The dataset is not included due to size and licensing constraints.
Please download LIDC-IDRI separately and place it in: LIDC-IDRI-slices/

