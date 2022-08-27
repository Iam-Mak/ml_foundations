# Project: Image Classifier

<img src='assets/Flowers.png' width=850px>

### Description
Going forward, AI algorithms will be incorporated into more and more everyday applications. For example, we might want to include an image classifier in a smart phone app. To do this, we had to use a deep learning model trained on hundreds of thousands of images as part of the overall application architecture. A large part of software development in the future will be using these types of models as common parts of applications. 

In this project, we'll train an image classifier to recognize different species of flowers. we can imagine using something like this in a phone app that tells us the name of the flower our camera is looking at. In practice we had train this classifier, then export it for use in our application. We'll be using [this dataset](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/index.html) from Oxford of 102 flower categories, you can see a few examples above. 



The project is broken down into multiple steps:

* Load the image dataset and create a pipeline.
* Build and Train an image classifier on this dataset.
* Use our trained model to perform inference on flower images.

#### Check My 
- [Jupyter notebook](https://github.com/Iam-Mak/Udacity-Machine-Learning-Projects/blob/main/2.%20Project%20-%20Image%20Classifier/Image%20Classifier%20Project.ipynb)

## Getting Started
### Data
We will use `tensorflow_datasets` to load the [Oxford Flowers 102 dataset](https://www.tensorflow.org/datasets/catalog/oxford_flowers102).The Oxford Flowers 102 dataset is a consistent of 102 flower categories commonly occurring in the United Kingdom. Each class consists of between 40 and 258 images. The images have large scale, pose and light variations. In addition, there are categories that have large variations within the category and several very similar categories.




###  Data Exploration
This dataset has 3 splits: `'train'`, `'test'`, and `'validation'`.
- The split train has `1020` records
- The split test has `6149` records
- The split validation has `1020` records
- Number of Classes is:  `102`

We'll also need to make sure the training data is normalized and resized to 224x224 pixels as required by the pre-trained networks.
The validation and testing sets are used to measure the model's performance on data it hasn't seen yet, but we'll still need to normalize and resize the images to the appropriate size.

## Build and Train the Classifier
Things we'll need to do:

* Load the MobileNet pre-trained network from TensorFlow Hub.
* Define a new, untrained feed-forward network as a classifier.
* Train the classifier.
* Plot the loss and accuracy values achieved during training for the training and validation set.
* Save your trained model as a Keras model.

<img src='assets/Training and Validation Loss.png' width=600px>

## Inference for Classification
### Image Pre-processing
The process_image function should take in an image (in the form of a NumPy array) and return an image in the form of a NumPy array with shape (224, 224, 3).
- First, we should convert your image into a TensorFlow Tensor and then resize it to the appropriate size using tf.image.resize.
- Second, the pixel values of the input images are typically encoded as integers in the range 0-255, but the model expects the pixel values to be floats in the range 0-1. Therefore, you'll also need to normalize the pixel values.
- Finally, convert your image back to a NumPy array using the .numpy() method

<img src='assets/Processed Image.png' width=700px>

## Sanity Check
It's always good to check the predictions made by your model to make sure they are correct.

<img src='assets/inference_example.png' width=700px>
