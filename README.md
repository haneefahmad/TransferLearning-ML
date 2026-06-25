# Transfer Learning vs. Baseline CNN for CIFAR-10 Image Classification

## Overview

This project compares the performance of a **Transfer Learning** approach using **MobileNetV2** with a **custom Convolutional Neural Network (CNN)** for image classification on the CIFAR-10 dataset.

The objective is to evaluate whether a pre-trained ImageNet model performs better than a simple CNN when working with small-resolution images (32×32).

---

## Dataset

The project uses the **CIFAR-10** dataset provided by TensorFlow.

- **60,000** color images
- **10 object classes**
- **32 × 32** pixel images
- **50,000** training images
- **10,000** testing images

Classes include:

- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

---

## Project Workflow

1. Load and preprocess the CIFAR-10 dataset
2. Normalize image pixel values
3. Split the dataset into training and validation sets
4. Build a transfer learning model using MobileNetV2
5. Freeze the pretrained feature extractor
6. Train a custom classification head
7. Build a baseline CNN from scratch
8. Compare both models using:
   - Training accuracy
   - Validation accuracy
   - Test accuracy
9. Visualize feature maps from MobileNetV2
10. Plot training and validation performance

---

## Technologies Used

- Python
- TensorFlow / Keras
- MobileNetV2
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab

---

## Model Architectures

### Transfer Learning Model

- MobileNetV2 (ImageNet pretrained)
- Frozen convolutional layers
- Global Average Pooling
- Dropout (0.5)
- Dense (128, ReLU)
- Softmax Output Layer (10 classes)

### Baseline CNN

- Conv2D
- MaxPooling2D
- Flatten
- Dense (128, ReLU)
- Softmax Output Layer

---

## Results

| Model | Test Accuracy |
|--------|--------------:|
| Transfer Learning (MobileNetV2) | **32.6%** |
| Baseline CNN | **62.7%** |

The baseline CNN significantly outperformed the transfer learning model.

---

## Performance Comparison

The notebook generates the following comparison graph.

<p align="center">
  <img src="transfer_learning_vs_baseline.png" width="700">
</p>

---

## Why Did the Baseline Perform Better?

Although transfer learning is often highly effective, several factors limited MobileNetV2's performance in this experiment:

- MobileNetV2 was trained on **224×224 ImageNet images**, whereas CIFAR-10 images are only **32×32**.
- Important low-level features may be lost during the early downsampling stages.
- The pretrained layers were completely frozen, preventing adaptation to CIFAR-10.
- A lightweight CNN is better suited for learning features from small-resolution datasets.

---

## Possible Improvements

Future work could include:

- Fine-tuning the last MobileNetV2 blocks instead of freezing all layers.
- Resizing CIFAR-10 images to 96×96 or 224×224.
- Applying data augmentation.
- Using learning-rate scheduling.
- Adding Batch Normalization.
- Training for more epochs.
- Experimenting with ResNet50, EfficientNet, or DenseNet.
- Performing hyperparameter tuning.

---

## Repository Structure

```
.
├── TransferLearning.ipynb
├── transfer_learning_vs_baseline.png
└── README.md
```

---

## Key Learning Outcomes

- Understanding transfer learning using MobileNetV2
- Building CNNs from scratch
- Comparing pretrained and custom models
- Visualizing learned feature maps
- Evaluating deep learning models using TensorFlow/Keras
- Analyzing why transfer learning may not always outperform simpler architectures

---

## Author

**Haneef Ahmad**

GitHub: https://github.com/haneefahmad
