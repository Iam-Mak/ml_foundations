# Image Classifier Code

## Explore the Dataset
`take()` method to extract the first 3 examples (i.e., images) from the training set of the "oxford_flowers102" dataset. For each example, it converts the TensorFlow tensor object to a NumPy array using the `numpy()` method, and assigns the image array and its corresponding label to the `image` and `label` variables, respectively.

## Label Mapping

File called **label_map.json** and loads it as a JSON object into the variable `class_names`.


## Create Pipeline 
### format_image(image, label):
- The `tf.cast()` function is used to convert the data type of the image tensor to `tf.float32`. This is because many machine learning models require input data to be in floating-point format.
- The `tf.image.resize()` function is used to resize the image to the desired size specified by `image_size`. This function uses bilinear interpolation to resize the image.
- The pixel values in the image tensor are then normalized to the range [0, 1] using the expression `image /= 255`. This is a common pre-processing step used in computer vision tasks to help the model converge faster during training.
- The pre-processed image and label are returned as a tuple.

#### training_batches
- `training_set.shuffle(num_training_examples//4)`: This function shuffles the training set, which helps to ensure that the model doesn't overfit to any particular order of the training examples. The `num_training_examples` variable is the total number of examples in the training set, and the `//4` expression divides this number by 4 to specify how many examples to use for shuffling.
- `.map(format_image)`: This function applies the `format_image()` function we defined earlier to each example in the shuffled training set. This function converts the image data type to `tf.float32`, resizes the image to `image_size` specified earlier (224 in this case), and normalizes the pixel values to the range [0, 1].
- `.batch(batch_size)`: This function creates batches of `batch_size` examples from the pre-processed training examples. Batching the examples together allows for more efficient training on GPUs or TPUs, as multiple examples can be processed in parallel.
- `.prefetch(1)` : This function prefetches one batch of examples to be processed by the GPU or TPU while the current batch is being processed by the CPU. This can help to reduce the training time by minimizing the idle time of the GPU or TPU.

## Build and Train the Classifier
MobileNet is a family of small and efficient convolutional neural networks designed for mobile and embedded vision applications. These models are optimized for mobile devices and are lightweight, making them easy to deploy on devices with limited resources.

It consists of over 1 million labeled images. This pre-trained model has learned to recognize a wide variety of objects and features from the ImageNet dataset, and can be used as a starting point for many computer vision tasks.

### Build and train your network.
We are using the hub.KerasLayer() function from TensorFlow Hub to load the MobileNet pre-trained model.

The URL variable specifies the location of the MobileNet pre-trained model, which is available as a TensorFlow Hub module.

- `feature_extractor` This creates a new Keras layer that we can use as the feature extractor for our model.
- The `feature_extractor.trainable = False` line of code freezes the weights of the pre-trained MobileNet model so that they are not updated during training.
- The `tf.keras.Sequential()` function is used to create a new sequential model that combines the pre-trained feature extractor with the new dense layer.
- The `tf.keras.layers.Dense()` function is used to define a new dense layer with the specified number of output classes and activation function. 

### model.compile()
- **Adam (Adaptive Moment Estimation)** is an optimization algorithm used in deep learning to update the weights of a neural network during training. It's an extension of stochastic gradient descent (SGD) that uses adaptive learning rates for each weight parameter, rather than a single learning rate for the entire network. The idea behind Adam is to adapt the learning rates of each weight based on their gradient's first and second moments.
- `sparse_categorical_crossentropy ` is a type of loss function used in multiclass classification tasks where the target variable is represented by integers rather than one-hot encoded vectors.

## Save the Model

Saves the trained model to a file using Keras' .save() method. The path where the file will be saved is defined by concatenating the current directory ('./') with the current timestamp (obtained using time.time()) and appending the .h5 extension to indicate that this is a Keras model file.

## Load the Keras Model
- `load_model()` method from Keras is used to load the saved model.
- The model contains a KerasLayer from TensorFlow Hub, we also pass the argument `custom_objects={'KerasLayer':hub.KerasLayer}` to the `load_model()` method to ensure that this layer is correctly loaded as part of the model.

## Image Pre-processing
### process_image
- Converts the numpy image to a TensorFlow tensor using `tf.convert_to_tensor`.
- Resizes the tensor to the specified `image_size` using `tf.image.resize`.
- Normalizes the tensor by dividing by 255 to ensure pixel values are between 0 and 1.
- Returns the processed tensor as a numpy array using `.numpy`() method.

## Inference
### predict
- The function opens the image at the given path, converts it to a numpy array, and processes it using the `process_image` function that was defined earlier.
- The function expands the dimensions of the processed image by adding an additional axis at index 0. This is because the model expects a batch of images as input.
-  The function uses the predict method of the loaded model to generate predictions for the input image.
- The `tf.nn.top_k` method is used to find the top `k`  predictions, where k is the integer value provided as input to the function. The method returns two tensors: one containing the top k probability values, and another containing the corresponding class indices.