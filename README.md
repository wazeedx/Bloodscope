
🩸 Blood Cell Classification for Blood Disease Detection Using CNN

## 🎯 Project Objective

The goal of this project was to build a Convolutional Neural Network (CNN) capable of automatically classifying different types of white blood cells from microscopic blood smear images. Accurate identification of blood cells plays an important role in the early detection and diagnosis of various blood-related disorders. By automating this process, the model can help reduce manual effort and support medical professionals in screening large numbers of samples more efficiently.

---

## 📂 Dataset

The project uses the Blood Cell Images Dataset available on Kaggle.

The dataset contains approximately **12,500 RGB microscopic blood cell images** with a resolution of **320 × 240 pixels**. Images are categorized into four major white blood cell types:

* Eosinophil
* Lymphocyte
* Monocyte
* Neutrophil

The dataset is divided into two collections:

### dataset-master

* Contains around 410 original microscopic images.
* Useful for understanding the raw dataset.

### dataset2-master

* Contains approximately 3,000 augmented images for each cell type.
* Organized into separate training, validation, and testing folders.
* Used for model training and evaluation.

---

## 🛠️ Approach

### Data Preparation

To efficiently load and process the image data, I used TensorFlow's `image_dataset_from_directory()` utility. This simplified the creation of training, validation, and test datasets directly from the folder structure.

A rescaling layer was added to normalize pixel values, ensuring consistent input for the neural network and improving training stability.

### Model Development

A custom CNN architecture was designed to learn distinguishing visual patterns from blood cell images, such as:

* Cell shape
* Nucleus structure
* Texture patterns
* Color distribution

The model consists of multiple convolution and pooling layers for feature extraction, followed by fully connected layers for classification.

### Regularization

A Dropout layer with a rate of 0.1 was introduced to reduce overfitting and improve the model's ability to generalize to unseen data.

### Hyperparameter Experimentation

To compare training performance, the same architecture was trained using five different optimizers:

* SGD
* Adagrad
* Adadelta
* Adam
* RMSprop

All models used:

* Sparse Categorical Crossentropy Loss
* ReLU Activation Function
* Softmax Output Layer

The goal was to determine which optimizer achieved the best balance between convergence speed and classification accuracy.

---

## 🧠 CNN Architecture

### Model Summary

* Rescaling Layer (320 × 240 × 3 Input)
* Conv2D (32 Filters, 3×3 Kernel)
* MaxPooling2D
* Conv2D (64 Filters, 3×3 Kernel)
* MaxPooling2D
* Conv2D (64 Filters, 3×3 Kernel)
* MaxPooling2D
* Conv2D (32 Filters, 3×3 Kernel)
* MaxPooling2D
* Flatten Layer
* Dense Layer (ReLU)
* Dropout Layer (10%)
* Dense Output Layer (Softmax)

### Why CNN?

CNNs are highly effective for image classification tasks because they automatically learn spatial features from images without requiring manual feature engineering. This makes them particularly suitable for medical imaging applications where subtle visual differences are important.

---

## 📊 Exploratory Data Analysis

Before training, the dataset was visually inspected to understand the characteristics of each blood cell type. Sample images showed clear differences in:

* Cell morphology
* Nucleus size and shape
* Cytoplasm appearance
* Color intensity

This confirmed that image-based classification was a suitable approach for the problem.

---

## 📈 Model Evaluation

The CNN was trained separately using five optimization algorithms and their performance was compared based on:

* Training Accuracy
* Validation Accuracy
* Loss Curves
* Convergence Speed

### Optimizers Evaluated

| Optimizer | Loss Function                   |
| --------- | ------------------------------- |
| SGD       | Sparse Categorical Crossentropy |
| Adagrad   | Sparse Categorical Crossentropy |
| Adadelta  | Sparse Categorical Crossentropy |
| Adam      | Sparse Categorical Crossentropy |
| RMSprop   | Sparse Categorical Crossentropy |

Training progress and performance metrics were monitored using TensorBoard for better visualization and comparison.

---

## 🔍 Results

Among all tested optimizers, **RMSprop achieved the most consistent performance**, demonstrating:

* Faster convergence during training
* Lower validation loss
* Higher validation accuracy
* More stable learning behavior

While optimizers such as SGD eventually improved performance, they required significantly more epochs to reach comparable results.

---

## 📢 Conclusion

This project demonstrates the effectiveness of Convolutional Neural Networks in classifying microscopic blood cell images. The model successfully learned meaningful visual features and achieved strong classification performance across four white blood cell categories.

The optimizer comparison highlighted how training algorithms can significantly influence model performance, with RMSprop producing the best overall results for this architecture and dataset.

Future improvements could include:

* Transfer learning using pretrained models such as ResNet50 or EfficientNet
* Data augmentation techniques for improved robustness
* Deployment through a web application using Flask or FastAPI
* Integration into real-time medical diagnostic systems

### Technologies Used

* Python
* TensorFlow / Keras
* NumPy
* Matplotlib
* TensorBoard
* Google Colab
* Kaggle Dataset

---

