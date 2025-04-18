# Animal Classification Model

A deep learning model for classifying animal images using PyTorch, with MLOps practices implemented using DVC and MLflow.

## Front end Overview

Check out the README under the "Front End" folder to install dependencies and run the website.

## Overview

This project implements a transfer learning-based image classification model that can identify 10 different animal classes:
- Butterfly
- Cat
- Chicken
- Cow
- Dog
- Elephant
- Horse
- Sheep
- Spider
- Squirrel

The model achieves >90% accuracy using various architectures (ResNet18, ResNet34, MobileNet, EfficientNet) and has been optimized for quick training while maintaining high accuracy.

## Features

- Multiple model architectures (ResNet18, ResNet34, MobileNet, EfficientNet)
- Data version control using DVC
- Experiment tracking with MLflow
- Early stopping and model checkpointing
- Apple Silicon GPU acceleration support (MPS)
- Automatic model optimization

## Requirements

- Python 3.8+
- PyTorch 2.0+
- DVC
- MLflow
- Other dependencies in requirements.txt

## Installation

1. Clone the repository:
```bash
git clone https://github.com/DionRizo/animal_classification_model
cd animal_classification_model
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Pull the data and models using DVC:
```bash
dvc pull
```

## Usage

### Training

To train the model with the default configuration:

```bash
python animal_classification_model_training.py
```

The training script will:
1. Run experiments with different model architectures
2. Use early stopping when reaching 82% accuracy
3. Save the best performing model
4. Track experiments using MLflow
5. Generate training history plots

### Model Selection

The training process tests multiple configurations:
- ResNet18 with medium augmentation (lr=0.001)
- ResNet34 with medium augmentation (lr=0.001)
- MobileNet with medium augmentation (lr=0.001)
- ResNet18 with high augmentation (lr=0.0001)
- ResNet18 with low augmentation (lr=0.003)
- EfficientNet with high augmentation (lr=0.001)

The best performing model is automatically selected and saved.

## Model Performance

Current best model performance:
- Architecture: ResNet18
- Learning Rate: 0.003
- Augmentation: Low
- Accuracy: 94.68%
- Training Time: ~1 epoch

All models consistently achieve:
- Minimum accuracy: >80%
- Average accuracy: >90%
- Training time: 1-2 epochs

## Project Structure

```
animal_classification_model/
├── animal_classification_model_training.py  # Main training script
├── dvc_utils.py                            # DVC utility functions
├── setup_dvc.py                            # DVC setup script
├── requirements.txt                        # Project dependencies
├── .dvc/                                  # DVC configuration
├── .gitignore                             # Git ignore rules
├── .dvcignore                             # DVC ignore rules
└── mlruns/                                # MLflow tracking files
```

## MLOps Features

### Data Version Control (DVC)
- Dataset and models are version controlled using DVC
- Remote storage configuration for data and models
- Easy reproduction of experiments

### Experiment Tracking (MLflow)
- Automatic logging of:
  - Model parameters
  - Training metrics
  - Model artifacts
  - Training plots

### Model Optimization
- Early stopping mechanism
- Learning rate scheduling
- Multiple architecture testing
- Automated model selection

## Contributing

Feel free to open issues or submit pull requests with improvements.
