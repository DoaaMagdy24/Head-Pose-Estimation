# Head Pose Estimation

> Real-time 3D head orientation estimation to detect suspicious examinee behavior during online exams.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)

## Project Overview
This project implements a robust head pose estimation system using ResNet-18, designed to detect abnormal head movements during online exams. The model accurately predicts yaw, pitch, and roll angles while classifying head poses into categories—enabling identification of suspicious behaviors like frequent turning, tilting, or looking away.

## Features
- Estimates **yaw**, **pitch**, and **roll** angles in real time  
- Detects suspicious head movements (e.g., looking sideways or down)  
- Uses ResNet-18 backbone for optimal speed–accuracy trade-off  
- Trained with bias correction for extreme poses (up/down angles)  
- Outputs both continuous angles and discrete pose categories (frontal, left, right, up, down)

## Dataset & Model

- **Base Model**: ResNet-18 (pre-trained on ImageNet)  
- **Training Data**: Combined datasets — BIWI, 300W-LP, and AFLW2000-3D (31,903 images)  
- **Input**: Face crops from YOLOv8 detector, resized to 640×640  
- **Augmentations**: Flips, HSV shifts, affine transforms, and rotation to improve robustness  
- **Bias Mitigation**: Under-sampling of frontal poses + weighted sampling and dynamic loss for rare angles

| Before Bias Correction | After Bias Correction |
|:----------------------:|:---------------------:|
| <img src="https://github.com/user-attachments/assets/96240222-ce2c-4323-80b7-d9dafeb65c9d" width="450"> | <img src="https://github.com/user-attachments/assets/d24a2682-e8e7-44c2-b87f-5c9506e002bc" width="450"> |


## Performance Metrics

| Metric        | Value                          |
|-------------|----------------------------------|
| MSE (Yaw)      | 1.7° |
| MSE (Pitch)     | 1.5° |
| MSE (Roll) | 1.9° |
| Pose Classification Accuracy      | 94.3% |
