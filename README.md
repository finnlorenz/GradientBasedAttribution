Studying Gradient-Based Attribution Over Training Epochs
========================================================

OVERVIEW
--------
This project studies the temporal stability of gradient-based explanations
during neural network training. We analyze how saliency maps and integrated
gradients evolve across epochs and when explanations become stable.

RESEARCH QUESTIONS
------------------
1. When do gradient-based explanations stabilize during training?
2. Does explanation stability correlate with predictive convergence?
3. How do dataset complexity, model size, and learning rate affect stability?

METHODS
-------
Datasets:
- MNIST (binary classification)
- CIFAR-10 (binary classification)

Models:
- Small CNN
- Deep CNN

Explanation Methods:
- Saliency (vanilla gradients)
- Integrated Gradients (zero baseline)

Training Settings:
- Epochs: 50
- Learning rates: {0.001, 0.01}
- Optimizer: Adam
- Loss: Cross-Entropy
- Seeds: 10 per configuration
- Fixed explanation samples per run

STABILITY METRICS
-----------------
- Cosine similarity between explanations at epochs t and t+1
- Spearman rank correlation of absolute attributions
- Cosine similarity to final-epoch explanation
- Temporal variance of explanations across epochs

REPRODUCIBILITY
---------------
- Random seeds fixed (Python, NumPy, PyTorch)
- Deterministic CuDNN enabled
- Fixed evaluation set for explanation tracking
- Manual implementation of saliency and integrated gradients

DEPENDENCIES
------------
Python >= 3.9

Required packages:
- torch==2.0.1
- torchvision==0.15.2
- numpy
- scipy
- matplotlib
- tqdm
- jupyter
- notebook

EXECUTION
---------
Run experiments:
    Experiments.ipynb

Run analysis:
    Analyse.ipynb

Outputs:
- Training results saved to: results/
- Figures saved to: plots/

EXPECTED RUNTIME
----------------
- CPU only: several hours
- GPU recommended: ~1–2 hours

All results and figures can be reproduced without modifying the code.
