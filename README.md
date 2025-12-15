# VGGNet from Scratch on MNIST (PyTorch)

![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

This repository contains a full implementation of **VGG-16** and **VGG-19** architectures built from scratch using PyTorch. The models are adapted specifically to train on the **MNIST dataset** (grayscale handwritten digits).

## 📌 Project Overview

The standard VGG architecture (Simonyan & Zisserman, 2014) was originally designed for ImageNet (RGB images, 224x224 inputs). This project adapts the architecture for the MNIST dataset by:
1.  **Modifying Input Channels:** Changing the first layer to accept **1 channel** (Grayscale) instead of 3 (RGB).
2.  **Input Resizing:** Resizing MNIST images from $28 \times 28$ to **$32 \times 32$**.
3.  **Output Classes:** adjusting the final fully connected layer to output **10 classes** (digits 0-9).

## 🏗️ Model Architectures

### Why Resize to 32x32?
VGG networks use 5 MaxPool layers, each reducing the spatial dimension by half.
* **Original MNIST ($28 \times 28$):** $28 \to 14 \to 7 \to 3.5$ (Error/Mismatch)
* **Resized ($32 \times 32$):** $32 \to 16 \to 8 \to 4 \to 2 \to 1$ (Clean reduction)

This allows us to preserve the standard depth of VGG without hacking the pooling layers.

### Comparison
| Feature | VGG-16 | VGG-19 |
| :--- | :--- | :--- |
| **Total Layers** | 16 Weight Layers | 19 Weight Layers |
| **Conv Blocks** | 5 Blocks | 5 Blocks |
| **Block 3 Depth** | 3 Conv Layers | **4 Conv Layers** |
| **Block 4 Depth** | 3 Conv Layers | **4 Conv Layers** |
| **Block 5 Depth** | 3 Conv Layers | **4 Conv Layers** |
| **Parameters** | ~33 Million | ~38 Million |

## 🚀 Getting Started

### Prerequisites
* Python 3.x
* PyTorch
* Torchvision

### Installation
```bash
git clone [https://github.com/your-username/vgg-mnist-scratch.git](https://github.com/your-username/vgg-mnist-scratch.git)
cd vgg-mnist-scratch
pip install torch torchvision
