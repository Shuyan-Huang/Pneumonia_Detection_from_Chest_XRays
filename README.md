## Project Overview

This project was designed by Udacity to deliver hands-on experience with 2D medical imaging data analysis.

Chest X-Ray exam is the best available and cost-effective method for pneumonia diagonosis. Its high enough quantity makes it a good candidate for deep learning application. However, deriving clinical diagnoses from chest X-Rays can be very challenging even for skilled radiologists. This project aims to provide practice of transfer learning application in medical imaging analysis, instead of pursuing high model performance. 

The dataset for this project was released as NIH Chest X-ray Dataset, composed of 112,120 X-ray images with disease labels from 30,805 uinque patients. A total of 14 disease labels were extrated from rediological reports using Natural Language Processing. They are expected to be >90% accuate and suitable for weakly-supervised learning. [Link to the paper]([https://www.nih.gov/news-events/news-releases/nih-clinical-center-provides-one-largest-publicly-available-chest-x-ray-datasets-scientific-community](https://www.nih.gov/news-events/news-releases/nih-clinical-center-provides-one-largest-publicly-available-chest-x-ray-datasets-scientific-community))

## Project Steps:

### 1. Exploratory Data Analysis (EDA)

The first part of the project was to understand and describe the dataset. The analysis includes:

- The patient demographic data such as gender, age, etc.
- The view postion where the x-ray was taken
- The number of pneumonia cases and non-pneumonia cases
- The distribution of other diseases that are comorbid with pneumonia
- Number of diseases per patient
- Pixel-level assessments of the image data

### 2. Building and Training Model

The second part was to apply transfer learning using a pre-trained CNN architecture. Key points are as follows:

- Training and validation sets were curated according to the EDA. In general, the ratio between pneumonia and non-pneumonia individuals was 1:1 in training set and 1:3 in validation set.
- Image pre-processing and augmentation were performed to increase model performance.
- An existing CNN architecture, VGG16, was used with weights trained on the ImageNet dataset. First 17 layers in VGG16 were freezed and several new layers were added to the end to train.
- Parameters that were tweaked to improve performance include: image augmentation parameters, training batch size, training learning rate etc.
- As model was trained, the performance was monitored over subsequence training epochs. Metrics include accuracy, AUC, precision, recall and F1.

### 3. Clinical Workflow Integration

In the real world, medical imaging data is usually contained inside of standard DICOM files. In the third part, a DICOM wrapper was created to take in a standard DICOM file and output data in the format that the trained model could accept. 

## Result:

The overall accuracy on the validation set was 65%.

![Confusion Matrix](./iamges/cm.png)
