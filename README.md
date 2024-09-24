# Classifying Persian Handwritten Digits Using Machine Learning Methods

This project was done as an exercise in **Learning in Brain and Machine 1** course. It focuses on the classification of Persian handwritten digits using different feature extraction and classification methods. The aim is to identify the best model for accurately classifying the digits. The dataset used for this task is the **Hoda Persian Handwritten Digit Dataset**, consisting of 60,000 samples in total, with a subset used for training and testing.

## Project Overview

### Key Objectives:
- **Feature Extraction**: Implement two feature extraction methods for Persian handwritten digit recognition.
- **Classification**: Apply multiple machine learning classifiers to the extracted features and compare their performance.
- **Evaluation**: Analyze the models' accuracy on both clean and noisy test sets, as well as with different training set sizes.

## Dataset

- **Hoda Dataset**: The dataset contains 60,000 samples, with 40,000 used for training and 20,000 for testing. However, for faster execution, a subset of the data was used:
  - **Training Set**: 3,000 samples
  - **Test Set**: 1,000 samples

## Methods

### 1. Preprocessing
To ensure uniformity across the dataset, each digit image was resized to a standard dimension by placing smaller images within a zero matrix, preserving the height-width ratio to avoid classification inaccuracies.

### 2. Feature Extraction
Two feature extraction methods were implemented:
- **Zoning Feature Extraction**: The image is divided into 5x5 zones, and the average pixel intensity in each zone is computed, resulting in a 25-element feature vector.
- **Horizontal and Vertical Histograms**: The pixel intensities along the horizontal and vertical axes are computed and concatenated to form a feature vector.

### 3. Classification Techniques
The following classifiers were applied to the extracted features:
- **k-Nearest Neighbor (k-NN)**: Classifies based on the majority vote of the k-nearest neighbors. Grid search was used to find the optimal k values, which were k=5 for the zoning feature and k=7 for the histogram feature.
- **Bayes Classifier**: A probabilistic classifier based on Bayes' theorem. 
- **Parzen Window**: A non-parametric method used to estimate the probability density function, with grid search used to determine the optimal bandwidth.
- **K-Means**: A clustering method used to group similar feature vectors before classification.

## Results

### Accuracy on Clean Test Set

| Classification Model | Zoning Feature Vector (%) | Histogram Feature Vector (%) |
|----------------------|---------------------------|------------------------------|
| **Nearest Neighbor**  | 86.9%                     | 76.7%                        |
| **k-NN**              | 89.3%                     | 77.0%                        |
| **Bayes**             | 83.0%                     | 59.8%                        |
| **Parzen Window**     | 85.4%                     | 32.0%                        |
| **K-Means**           | 84.6%                     | 69.5%                        |
| **Average Accuracy**  | 85.84%                    | 63.0%                        |

The results demonstrate that the **k-NN classifier with zoning features** achieved the highest accuracy of **89.3%**, outperforming the other models.

### Accuracy on Noisy Test Set (10% Salt-and-Pepper Noise)

| Classification Model | Zoning Feature Vector (%) | Histogram Feature Vector (%) |
|----------------------|---------------------------|------------------------------|
| **Nearest Neighbor**  | 72.6%                     | 37.7%                        |
| **k-NN**              | 80.1%                     | 46.5%                        |
| **Bayes**             | 29.4%                     | 12.1%                        |
| **Parzen Window**     | 76.9%                     | 8.2%                         |
| **K-Means**           | 73.7%                     | 44.7%                        |
| **Average Accuracy**  | 66.54%                    | 29.84%                       |

As expected, accuracy decreased on the noisy test set, but the **zoning feature extraction method** still performed significantly better than the histogram method.

### Efficiency Over Different Training Set Sizes
The performance of each model was also evaluated with different training set sizes. The zoning feature vectors consistently led to better performance across all classifiers compared to the histogram feature vectors.

## Conclusion

This project demonstrates that using the **zoning feature extraction** method in combination with the **k-NN classifier** yields the best results for classifying Persian handwritten digits. The method was robust even when noise was introduced into the test set, outperforming the other classifiers tested. Further improvements could be explored by using larger training sets or refining feature extraction techniques.

