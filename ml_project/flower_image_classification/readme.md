# Flower Image Classification

A pretrained MobileNetV2 model is used for efficient and accurate image classification.

<img src="../../images/flower_samples_with_labels.png" width="850">

## Description

This project implements an image classification model to identify 102 different flower categories.

The model is built using transfer learning, where a pretrained MobileNetV2 network is fine tuned by replacing the final classifier layer. This allows efficient training while maintaining strong performance.

The model is trained on the [Oxford Flowers 102 dataset](https://docs.pytorch.org/vision/main/generated/torchvision.datasets.Flowers102.html) and is capable of predicting flower classes from new images.



## Workflow

The project follows these steps:

- Load and preprocess the dataset  
- Train a classification model using transfer learning  
- Evaluate the model on unseen data  
- Perform inference on new images  

#### Notebook
- [Jupyter Notebook](Image_Classifier_Project.ipynb)



## Libraries

- NumPy  
- Matplotlib  
- PyTorch  
- Torchvision  



## Data

The dataset contains 102 flower categories with variations in scale, pose, and lighting conditions.

- Training set: 1020 images  
- Validation set: 1020 images  
- Test set: 6149 images  

Images are resized to 224 × 224 and normalized to match the input requirements of pretrained models.

## Model

MobileNetV2 pretrained on ImageNet is used as the base model.

The feature extraction layers are frozen, and the final classifier layer is replaced to match the 102 flower classes.

This transfer learning approach enables efficient training while maintaining strong performance.

### Model Training

The model is trained using:

- Loss function: CrossEntropyLoss  
- Optimizer: Adam  
- Training and validation sets to monitor performance  



## Inference

### Image Preprocessing

Input images are processed before being passed to the model:

- Resize to 224 × 224  
- Scale pixel values to [0, 1]  
- Normalize using ImageNet statistics  
- Convert to tensor and add batch dimension  



## Results

The trained model predicts the most likely classes along with their probability scores.

<img src="../../images/predictions_grid.png" width="1000">