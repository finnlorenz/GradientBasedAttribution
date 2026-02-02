# Studying Gradient-Based Attribution Over Training Epochs

## Overview
This repository contains the code and analysis for our project on the temporal stability of
gradient-based explanations during training. We study how saliency maps and integrated
gradients evolve over training epochs and when they become stable.

## Research Questions
We investigate:
1. When do explanations stabilize during training?
2. Does explanation stability correlate with predictive convergence?
3. How do dataset complexity, model size, and learning rate influence explanation stability?

## Methods
We train CNN models on:
- MNIST (binary classification)
- CIFAR-10 (binary classification: cat vs dog)

We compare:
- Small vs Deep CNN
- Learning rates: 0.001 vs 0.01
- Explanation methods: Saliency (vanilla gradients) vs Integrated Gradients
- 10 random seeds per configuration



All experiments can be reproduced by running Experiments.ipynb.
All plots can be regenerated using Analysis.ipynb.