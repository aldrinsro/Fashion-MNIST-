# Fashion-MNIST-

Fashion MNIST Image Classification using CNN
Project Overview
This project demonstrates how to build and train a Convolutional Neural Network (CNN) using TensorFlow/Keras to classify images from the Fashion MNIST dataset. The Fashion MNIST dataset consists of 60,000 training images and 10,000 test images of 10 different fashion categories. Each image is a 28x28 grayscale image.

Dataset
The Fashion MNIST dataset is a collection of Zalando's article images, each a 28x28 grayscale image, associated with a label from 10 classes.

Classes:

T-shirt/top
Trouser
Pullover
Dress
Coat
Sandal
Shirt
Sneaker
Bag
Ankle boot
Setup and Data Loading
The necessary libraries like numpy, matplotlib, tensorflow, keras, plotly, and sklearn are imported. The Fashion MNIST dataset is loaded directly using keras.datasets.fashion_mnist.load_data().

Data Exploration and Visualization
Training and Test Data Shapes:

Training shape: (60000, 28, 28)
Test shape: (10000, 28, 28)
Sample images from the dataset are visualized using Plotly's go.Heatmap to show the grayscale pixel intensity and their corresponding class labels.

Data Preprocessing
Normalization: Pixel values are scaled from the original range of [0, 255] to [0, 1] by dividing by 255.0. This helps in faster convergence during training.
Reshaping: Images are reshaped to include a channel dimension, changing their shape from (28, 28) to (28, 28, 1), which is required for Conv2D layers in Keras.
Model Architecture
A Sequential Keras model is constructed with the following layers:

Conv2D Layer 1: 32 filters, 3x3 kernel, ReLU activation, input shape (28, 28, 1).
MaxPooling2D Layer 1: 2x2 pool size.
Conv2D Layer 2: 64 filters, 3x3 kernel, ReLU activation.
MaxPooling2D Layer 2: 2x2 pool size.
Flatten Layer: Flattens the 2D feature maps into a 1D vector.
Dense Layer 1: 64 units, ReLU activation.
Dense Layer 2 (Output Layer): 10 units (for 10 classes), Softmax activation.
Model Compilation
The model is compiled with:

Optimizer: adam
Loss Function: sparse_categorical_crossentropy (suitable for integer labels)
Metrics: accuracy
Model Training
The model is trained for 20 epochs with a batch size of 64. A 20% validation split is used to monitor performance on unseen data during training.

Callbacks:

Early Stopping: Stops training if validation loss does not improve for 3 consecutive epochs, restoring the best weights.
Model Checkpoint: Saves the best model (based on validation loss) to best_model.h5.
Model Evaluation
After training, the model's performance is evaluated on the test dataset.

Test Loss: The final loss on the test set.
Test Accuracy: The final accuracy on the test set.
Prediction and Classification Report
Predictions are made on the x_test data, and the predicted class labels are obtained using np.argmax. A detailed classification report is generated using sklearn.metrics.classification_report, which includes precision, recall, f1-score, and support for each class, as well as overall accuracy.
