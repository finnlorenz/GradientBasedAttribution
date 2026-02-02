Studying Gradient-Based Attribution Over Training Epochs

Reproducibility & Replication Guide

This repository contains all code required to reproduce the experiments and figures from the study “Studying Gradient-Based Attribution Over Training Epochs”.
The goal is to analyze how gradient-based explanations evolve during training and when they become stable.

1. System Requirements

The experiments were run under the following environment:

OS: Windows / macOS 
Python: 3.10.18

CUDA (optional): 11.7

GPU: Optional but recommended (CPU is supported)

2. Python Dependencies

All dependencies are listed in requirements.txt.

Required packages and versions
torch==2.0.1
torchvision==0.15.2
numpy==1.23.5
scipy==1.10.1
matplotlib==3.7.1
tqdm==4.66.1
ipython==8.12.0
jupyter==1.0.0
notebook==6.5.6

3. Environment Setup
Step 1: Clone the repository
git clone <repository-url>
cd <repository-name>

Step 2: Create a virtual environment
python -m venv venv

Step 3: Activate the environment
source venv/bin/activate        # Linux / macOS
# venv\Scripts\activate         # Windows

Step 4: Install dependencies
-pip install -r requirements.txt

4. Running the Experiments

-All experiments are executed from Experiments.ipynb.
-What the experiment script does
-For each configuration, the script:
-Initializes a CNN model
-Trains for T epochs
-After each epoch:
-Records test accuracy
-Computes explanations on a fixed evaluation set
-Stores results as .pt files

Experimental factors

Datasets:
    MNIST (binary classification)
    CIFAR-10 (binary classification: cat vs dog)

Models:
    Small CNN
    Deep CNN

Learning rates:
    0.001, 0.01

Explanation methods:
    Saliency (vanilla gradients)
    Integrated Gradients

Random seeds:
    10 per configuration

Running all experiments
-Open Experiments.ipynb and run all cells.
Results are saved to:

results/
├── mnist_small_lr0.001_seed0_vanilla.pt
├── cifar_deep_lr0.01_seed7_integrated.pt
└── ...


Each file contains:
-Accuracy per epoch
-Explanations per epoch
-Dataset, model, learning rate, seed, and method metadata

5. Analysis and Plot Generation

-All analysis is performed in Analyse.ipynb.
-What the analysis script does
-Loads all saved .pt files

Computes:
-Cosine similarity between consecutive epochs
-Spearman rank correlation
-Cosine similarity to final-epoch explanations
-Temporal explanation variance
-Aggregates results across random seeds
-Generated figures are saved to:
    plots/

6. Reproducibility Controls

-The following measures ensure reproducibility:
-Fixed random seeds (random, numpy, torch)
-Deterministic CuDNN behavior
-Fixed explanation samples per run
-Identical evaluation set across epochs
-Explanations computed using PyTorch autograd only

Note: Saliency and Integrated Gradients are implemented manually and do not rely on external explainability libraries.

7. Hardware Notes

GPU acceleration is optional but recommended

CPU-only runs are supported but slower

Results are statistically robust due to seed averaging

8. Expected Runtime
Setup	Runtime
CPU	Several hours
Single GPU	~3–4 hours
9. Reproducing Figures Exactly

To reproduce all figures from scratch:

1. Run Experiments.ipynb
2. Run Analyse.ipynb
3. Use figures in plots/
