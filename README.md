
 MURA_Deep_Learning

## Deep Learning for Musculoskeletal Radiograph Analysis

### Project Overview

Musculoskeletal conditions impact over 1.7 billion people globally, causing chronic pain and disability. Radiologists face fatigue and rising diagnostic workloads, risking inconsistent outcomes.
Our project aims to automate abnormality detection in X-ray images using deep learning, improving diagnostic accuracy, speed, and healthcare accessibility. Leveraging the MURA (Musculoskeletal Radiographs) dataset, we trained and evaluated multiple deep learning models DenseNet-169 and ResNet-50 on classifying radiographs as normal or abnormal.

### Dataset: MURA
- Domain: Radiology, medical imaging
- Data Size: 40,561 images across 14,863 patient studies
- Body Parts: Shoulder, Wrist, Finger, Elbow, Forearm, Humerus, Hand
- Labels: Binary (0 = Normal, 1 = Abnormal), assigned by expert radiologists

### Methodology
**Data Preprocessing** 
- Resized to 320x320 pixels
- Converted to grayscale
- Data Augmentation: Random flips and rotations (±30°)
- Normalized using ImageNet mean and std dev

**Models Used**

**DenseNet-169**
- Pretrained on ImageNet
- Modified for grayscale input and binary classification
- Output: Probability of abnormality via sigmoid activation
  
**ResNet-50**
- Same preprocessing and loss function (Binary Cross-Entropy)
- Used for benchmarking against DenseNet
  

> Training Toolset: PyTorch, torchvision, Adam optimizer, Binary Cross-Entropy Loss

### Results & Evaluation

**Forearm (DenseNet-169)**

| Iteration | Accuracy | Abnormal Recall | F1 Score (Abnormal) |
| --------- | -------- | --------------- | ------------------- |
| Iter 4    | **80%**  | **64%**         | 76%                 |


![forearm_img_1](https://github.com/user-attachments/assets/9b77bb5f-5c3d-4f8c-b11b-b8f2eded3797)

**Shoulder (DenseNet-169)**

| Iteration | Accuracy | Normal Recall | F1 Score (Normal) |
| --------- | -------- | ------------- | ----------------- |
| Iter 2    | **72%**  | 73%           | 73%               |

![Shoulder_img_4](https://github.com/user-attachments/assets/6178299c-6cff-4025-9533-bc47a93952aa)

**Confusion Matrix Insights**

- High precision in detecting abnormalities
- Lower recall for abnormal class due to class imbalance
- Misclassifications occurred more in underrepresented abnormal cases

### Visual: CAM Highlighting Abnormality

<img width="731" alt="Screenshot 2025-05-13 at 10 34 20" src="https://github.com/user-attachments/assets/72f33de9-c2e0-4520-ac28-9679a4bac0f3" />

Frontal radiograph of the left humerus demonstrates a displaced transverse spiral fracture. This area
is highlighted by the model CAM.

### Key Learnings
- DenseNet-169 outperformed ResNet-50 in both precision and F1-score.
- Class imbalance was the primary challenge; future improvements include:
  - Focal Loss
  - Dynamic thresholding
  - Ensemble Models


### Business & Clinical Impact

| Area                       | Benefit                                      |
| -------------------------- | -------------------------------------------- |
| **Radiologist Efficiency** | Reduces time on normal cases                 |
| **Scalability**            | Deployable in low-resource and rural clinics |
| **Consistency**            | Lowers diagnostic variability                |
| **Decision Support**       | CAMs aid interpretation and trust            |

> **ROI Potential**: Hospitals adopting such AI tools can reduce imaging delays, minimize repeat scans, and improve patient outcomes enhancing both operational and clinical KPIs.


### Tools & Tech Stack

- Language: Python
- Frameworks: PyTorch, torchvision
- Visualization: Matplotlib, Seaborn
- Model Storage & Reuse: TorchHub
- Hardware: Trained on GPU for speed and scale


### Final Takeaway

This project proves that deep learning can act as a digital radiologist assistant, increasing access to consistent diagnostics and reducing human fatigue. DenseNet-169, in particular, shows high promise for integration into real-world hospital workflows with minimal retraining.













