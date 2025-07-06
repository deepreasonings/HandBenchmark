
# Hand Animatable Avatar Generation Benchmark Dataset

A Comprehensive Benchmark for Hand Animatable Avatar Generation

<p align="center">
  <br>
  <em>A Comprehensive Benchmark for Evaluating Hand Animatable Avatar Generation</em>
  <br>
  <a href="#" target="_blank">GitHub</a> | 
  <a href="#" target="_blank">Paper</a> |
  <a href="#" target="_blank">Dataset</a>
</p>
## 📖 Introduction

The Hand Animatable Avatar Generation Benchmark Dataset addresses a gap in evaluating hand animatable avatar generation systems. Creating realistic, fully animatable hand avatars from a single static expression remains challenging, as existing methods struggle to accurately capture:

* Subtle hand gestures and finger movements
* Dynamic background changes
* Consistent identity preservation

Our benchmark is motivated by two primary needs:

1. Current metrics fail to adequately capture the complexity involved in generating hand animatable avatars from a single image
2. A dedicated benchmark dataset can offer valuable insights to drive progress in high-quality hand animatable avatar generation

The Hand Animatable Avatar Generation Dataset is a fully open-source benchmark specifically designed for hand animatable avatar generation. It provides comprehensive labels and a versatile evaluation framework to facilitate rigorous assessment of high-quality hand animatable avatar generation.

## 🎬 Key Features

Our benchmark provides several compelling features:

* **Specialized Hand Evaluation** : Focused metrics specifically designed for hand animation assessment
* **Detailed Multi-Modal Annotations** : Comprehensive labels that facilitate high-quality hand animatable avatar generation by providing fine-grained hand gesture guidance
* **Versatile Evaluation Framework** : Enables rigorous assessment of hand animatable avatar quality across multiple dimensions
* **Specialized Metrics** : Both objective metrics (FID, E-FID, FVD, PSNR, SSIM, CSIM) and subjective metrics for holistic evaluation
* **Standardized Methodology** : Consistent testing protocol for fair comparison between different hand animation methods

## 📊 Evaluation Framework

Our benchmark provides multiple specialized evaluation metrics:

### Objective Metrics

* **FID (Fréchet Inception Distance)** : Measures visual quality similarity
* **E-FID (Edge-FID)** : Evaluates structural consistency using edge maps
* **FVD (Fréchet Video Distance)** : Assesses temporal coherence in generated videos
* **PSNR (Peak Signal-to-Noise Ratio)** : Quantifies reconstruction accuracy
* **SSIM (Structural Similarity Index)** : Measures perceptual similarity
* **CSIM (Cosine Similarity)** : Evaluates feature-level similarity

### Subjective Consistency Metrics

Six dimensions of subjective evaluation:

* Subject Consistency
* Background Consistency
* Motion Smoothness
* Dynamic Degree
* Aesthetic Quality
* Imaging Quality

## 🚀 Getting Started

### Installation

This benchmark uses MMPose for hand keypoint detection. For detailed installation instructions, please refer to the [MMPose installation guide](https://mmpose.readthedocs.io/en/latest/installation.html).

We recommend following these steps to set up your environment:

#### Prerequisites

Our benchmark requires Python 3.7+, CUDA 9.2+ and PyTorch 1.8+.

**Step 0.** Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) from the official website.

**Step 1.** Create a conda environment and activate it:

```bash
conda create --name hand-avatar python=3.8 -y
conda activate hand-avatar
```

**Step 2.** Install PyTorch following official instructions:

For GPU platforms:

```bash
conda install pytorch torchvision -c pytorch
```

For CPU-only platforms:

```bash
conda install pytorch torchvision cpuonly -c pytorch
```

**Step 3.** Install MMEngine and MMCV using MIM:

```bash
pip install -U openmim
mim install mmengine
mim install "mmcv>=2.0.1"
```

**Step 4.** Install MMPose:

```bash
mim install "mmpose>=1.0.0"
```

**Step 5.** Clone the repository and install dependencies:

```bash
# Clone the repository
git clone https://github.com/yourusername/hand-avatar-benchmark.git
cd hand-avatar-benchmark
```

#### Alternative: Manual Installation from Source

If you prefer to install MMPose from source (recommended for development):

```bash
git clone https://github.com/open-mmlab/mmpose.git
cd mmpose
pip install -v -e .
# "-v" means verbose, and "-e" means installing in development mode
cd ..
```

#### Verify the Installation

To verify that MMPose and other dependencies are correctly installed:

```bash
# Enter Python interpreter
python

# Try importing key packages
>>> import torch
>>> import mmpose
>>> import mmcv
>>> import cv2
>>> print(torch.__version__)
>>> print(mmpose.__version__)
```

For troubleshooting, please refer to the [MMPose installation guide](https://mmpose.readthedocs.io/en/latest/installation.html).

### Dataset Structure

```
hand-avatar-benchmark/
├── gt_test/                  # Ground truth test videos
├── hand_images/              # Extracted hand image frames
├── hand_videos/              # Hand region videos
├── FIDres/                   # FID evaluation results
├── SCres/                    # Subjective Consistency results
└── evaluation/               # Evaluation scripts
```

### Running Evaluations

```bash
# Process hand region extraction
python process_hand_videos.py

# Calculate FID, E-FID, FVD, PSNR, SSIM metrics
python FID_calculate.py

# Calculate Subjective Consistency scores
python SC_calculate.py
```

## 📊 Benchmark Results

Performance comparison of various methods on our hand animatable avatar benchmark:

| Method |   SC   |   BC   |   MS   |   DD   |   AQ   |   IQ   |  FID  |   FVD   | SSIM | PSNR | E-FID | CSIM |
| :-----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :------: | :---: | :---: | :----: | :---: |
|  Step  | 66.83% | 77.98% | 46.36% | 48.14% | 24.22% | 38.40% | 327.10 | 1597.65 | 0.316 | 12.98 | 277.47 | 0.681 |
|   Hun   | 48.15% | 64.98% | 49.65% | 52.85% | 19.02% | 27.69% | 301.94 | 1734.98 | 0.262 | 11.45 | 255.53 | 0.737 |
|   Wan   | 51.27% | 57.45% | 42.49% | 41.71% | 18.38% | 23.84% | 331.51 | 1561.58 | 0.367 | 13.09 | 240.48 | 0.796 |
|  OpenS  | 19.16% | 22.45% | 13.30% | 13.89% | 6.40% | 11.50% | 278.95 | 1534.50 | 0.342 | 15.50 | 264.98 | 0.794 |
|  Ha3/w  | 13.65% | 14.76% | 13.25% | 13.05% | 5.08% | 6.51% | 574.40 | 7750.48 | 0.098 | 6.13 | 445.59 | 0.366 |
| Ha3/wo | 2.13% | 2.56% | 0.49% | 0.91% | 0.39% | 0.89% | 921.16 | 10671.79 | 0.008 | 0.55 | 713.46 | 0.041 |
| ecv2/w | 14.19% | 18.21% | 9.27% | 9.52% | 5.08% | 10.24% | 588.72 | 8958.27 | 0.106 | 7.272 | 525.18 | 0.427 |
| ecv2/wo | 3.58% | 4.27% | 2.79% | 1.84% | 2.74% | 1.94% | 975.92 | 9472.28 | 0.019 | 0.492 | 741.03 | 0.152 |

*Legend: SC: Subject Consistency, BC: Background Consistency, MS: Motion Smoothness, DD: Dynamic Degree, AQ: Aesthetic Quality, IQ: Imaging Quality, FID: Fréchet Inception Distance, FVD: Fréchet Video Distance, SSIM: Structural Similarity Index Measure, PSNR: Peak Signal-to-Noise Ratio, E-FID: Enhanced Fréchet Inception Distance, CSIM: Cosine Similarity. ↑ indicates higher is better, ↓ indicates lower is better.*

## 🔧 Technical Details

### FID_calculate.py

This script calculates objective metrics for hand animation evaluation:

* Extracts frames from generated and ground truth hand videos
* Computes FID using InceptionV3 features
* Calculates E-FID using edge maps for hand structure consistency
* Measures FVD using I3D network for temporal coherence
* Calculates PSNR, SSIM, and CSIM for hand-specific quality assessment

### SC_calculate.py

This script processes subjective consistency scores for hand animation:

* Filters out unmatched hand videos
* Calculates average scores across hand animation dimensions
* Generates summary statistics for hand animation quality

### process_hand_videos.py

This script handles hand region extraction and processing:

* Uses DWPose-onnx for hand keypoint detection
* Processes video frames and extracts hand landmarks
* Creates cropped hand videos for specialized hand animation evaluation
* Ensures consistent hand region boundaries across frames

## 📝 Citation

If you find our work useful in your research, please consider citing.

## 🙏 Acknowledgements

We extend our gratitude to:

* [VBench](https://github.com/Vchitect/VBench) for their Comprehensive Benchmark Suite for Video Generative Models
* [DWPose-onnx](https://github.com/IDEA-Research/DWPose) for their hand keypoint detection framework
* Our research institution for providing computational resources
* Hand animation research community contributors

## 📄 License

This project is licensed under the [MIT License](https://demo.fuclaude.com/chat/LICENSE).
