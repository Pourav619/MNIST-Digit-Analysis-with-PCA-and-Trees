# MNIST Classification with PCA and Decision Trees

This project focuses on the classification of the MNIST dataset for classes 0, 1, and 2. The main steps include dimensionality reduction using PCA, learning a decision tree with 3 terminal nodes, evaluating test set accuracy, and implementing bagging to improve performance.

## Project Steps

### 1. Dataset Preparation

- **Dataset URL:** [MNIST Dataset](https://storage.googleapis.com/tensorflow/tf-keras-datasets/mnist.npz)
- **Classes Selected:** 0, 1, 2

### 2. Dimensionality Reduction with PCA

- **Objective:** Reduce dimensions to `p = 10`.
- **Method:** Principal Component Analysis (PCA) was applied to the entire training set of the selected classes to obtain the PCA matrix.
- **Outcome:** Dataset was reduced to 10 dimensions.

![image](https://github.com/Pourav619/MNIST-Digit-Analysis-with-PCA-and-Trees/assets/108517421/2b27ca6b-88c0-4f2d-8e30-4de5bc256856)


### 3. Learning a Decision Tree

- **Objective:** Grow a decision tree with 3 terminal nodes.
- **Method:** 
  - For the first split, all `p` dimensions were considered.
  - For each dimension, one split was considered to divide the space into two regions.
  - The total Gini index was calculated for each split.
  - The best split was determined by the minimum Gini index.
  - This process was repeated for subsequent splits until the space was divided into three regions.
  - 
![image](https://github.com/Pourav619/MNIST-Digit-Analysis-with-PCA-and-Trees/assets/108517421/e3185657-e6c1-4ef5-b2a5-33c5f837598a)

### 4. Class Prediction on Test Set

- **Objective:** Predict the class of all samples in the test set.
- **Method:** 
  - For each test sample, the region in the segmented space was identified.
  - The class of the sample was determined by the majority class in that region.
- **Results:** 
  - **Overall Accuracy:** [0.66]
  - **Class-wise Accuracy:** 
    - Class 0: [0.32]
    - Class 1: [0.91]
    - Class 2: [0.70]
   
  ![image](https://github.com/Pourav619/MNIST-Digit-Analysis-with-PCA-and-Trees/assets/108517421/8f9e75a1-375d-4416-8aae-a25f63ccbd9d)

![image](https://github.com/Pourav619/MNIST-Digit-Analysis-with-PCA-and-Trees/assets/108517421/59b4027b-454b-459c-a6aa-3297683a1b10)


### 5. Bagging 

- **Objective:** Develop 5 different datasets from the original dataset and use majority voting for class prediction.
- **Method:** 
  - Created 5 bootstrap samples from the training set.
  - Learned a decision tree for each dataset.
  - For test samples, majority voting (at least 3 trees agreeing) was used to determine the class.
  - In case of a tie, any of the predicted classes was chosen.
- **Results:** 
  - **Total Accuracy:** [0.61]
  - **Class-wise Accuracy:** 
    - Class 0: [0.65]
    - Class 1: [0.94]
    - Class 2: [0.21]

![image](https://github.com/Pourav619/MNIST-Digit-Analysis-with-PCA-and-Trees/assets/108517421/5a5371e3-1647-4be0-83a9-88b3e82ebedc)


