# 🚦 Traffic Signs Recognition with Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://tensorflow.org)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![Accuracy](https://img.shields.io/badge/Accuracy-99.33%25-brightgreen.svg)]()

A deep learning solution for classifying German traffic signs using Convolutional Neural Networks (CNNs) implemented in TensorFlow, achieving **99.33% accuracy** on the test dataset.

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Features](#features)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [License](#license)
- [Contact](#contact)

## 🎯 Overview

This project implements a CNN-based classifier for the [German Traffic Sign Recognition Benchmark (GTSRB)](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). The solution incorporates advanced techniques including:

- **Data Preprocessing**: Histogram equalization and grayscale conversion
- **Data Augmentation**: Flipping, rotation, and projection transformations
- **Multi-scale Feature Extraction**: Skip connections for improved classification
- **Regularization**: Dropout and L2 regularization to prevent overfitting

## 📊 Dataset

The German Traffic Sign Dataset consists of:

| Split | Images | Description |
|-------|--------|-------------|
| Training | 39,209 | 32×32 px color images |
| Testing | 12,630 | 32×32 px color images |
| Classes | 43 | Different traffic sign types |

Each image is a 32×32×3 RGB array with pixel intensities in the `[0, 255]` range.

## ✨ Features

### Preprocessing Pipeline
- Pixel normalization to `[0, 1]` range
- Localized histogram equalization for enhanced feature extraction
- Grayscale conversion (Y channel from YCbCr color space)
- One-hot encoding for labels

### Data Augmentation
- **Horizontal/Vertical Flipping**: Extends dataset from 39,209 to 63,538 images
- **Rotation & Projection**: Random transformations for better generalization
- **Class Balancing**: 20,000 examples per class for balanced training

## 🏗️ Model Architecture

<p align="center">
  <img src="model_architecture.png" alt="Model architecture"/>
</p>

The architecture consists of:

| Layer | Type | Size | Dropout |
|-------|------|------|---------|
| Layer 1 | 5×5 Conv | 32 filters | 10% |
| Layer 2 | 5×5 Conv | 64 filters | 20% |
| Layer 3 | 5×5 Conv | 128 filters | 30% |
| Layer 4 | Fully Connected | 1024 units | 50% |

**Key Features:**
- Multi-scale feature extraction with skip connections
- L2 regularization (λ = 0.0001)
- Early stopping with 100 epochs patience

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/danishsyed-dev/traffic-signs.git
   cd traffic-signs
   ```

2. **Install dependencies**
   ```bash
   pip install tensorflow numpy matplotlib scikit-learn opencv-python
   ```

3. **Download the dataset**
   - Get the dataset from [GTSRB](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset)
   - Place it in the `traffic-signs-data/` directory

## 💻 Usage

Open and run the Jupyter notebook:

```bash
jupyter notebook Traffic_Signs_Recognition.ipynb
```

The notebook includes:
- Data loading and exploration
- Preprocessing and augmentation
- Model training (2-stage approach)
- Evaluation and visualization

### Training Strategy

| Stage | Dataset | Learning Rate | Purpose |
|-------|---------|---------------|---------|
| 1 | Extended | 0.001 | Pre-training (~180 epochs) |
| 2 | Balanced | 0.0001 | Fine-tuning |

## 📈 Results

| Metric | Value |
|--------|-------|
| **Test Accuracy** | 99.33% |
| **Misclassified Images** | 85 out of 12,630 |
| **Human Performance** | 98.3% - 98.8% |

The model outperforms average human performance on this classification task!

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## 📬 Contact

**Syed Danish Ali**

- 🌐 Website: [danishsyed-dev.github.io/SYED_DANISH_ALI](https://danishsyed-dev.github.io/SYED_DANISH_ALI/)
- 💻 GitHub: [@danishsyed-dev](https://github.com/danishsyed-dev)

---

<p align="center">
  Made with ❤️ by Syed Danish Ali
</p>
