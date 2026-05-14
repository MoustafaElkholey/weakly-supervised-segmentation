# Tackling the Annotation Paradox in Remote Sensing 

## Overview
High annotation costs for satellite imagery in remote sensing cause severe data scarcity. This project builds a land-use semantic segmentation model using extreme weak supervision—relying on only 10 annotated points per class per image, rather than expensive, pixel-perfect dense masks.

## Technical Architecture
* **Framework:** U-Net integrated with a pre-trained ResNet-50 backbone.
* **Loss Function:** Custom **Partial Cross-Entropy (pCE)**. Standard loss functions collapse under extreme label sparsity. The pCE loss mathematically isolates gradients strictly to the known annotated pixels, shielding the model from unclassified background noise.
* **Preprocessing:** Applied deterministic Histogram Matching via CDF mapping to neutralize sensor variance and sun-angle differences across different aerial source patches.

## Performance Metrics
* Successfully generalized dense segmentation masks from minimal point-level data.
* Decreased training loss from **1.14 to 0.62** within the initial 3 epochs.
* Achieved robust spatial reconstruction despite >90% of pixels being unlabeled.

## Repository Contents
* `Mostafa_Elkholy_Landvisor_Assessment.ipynb`: Contains the full pipeline (Data preprocessing, Model Architecture, Custom Loss definition, and Training loop).
* `Mostafa_Elkholy_Landvisor_Assessment.pdf`: A business-style technical presentation of the methodology and results.

## Impact
By shifting from full supervision to a weakly supervised framework, this pipeline reduces the required manual annotation effort by over 90%, cutting data acquisition costs while maintaining operational accuracy.
