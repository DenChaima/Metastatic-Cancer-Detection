# MLP Group 5: Metastatic Cancer Detection

Build a breast cancer metastases detection and classification model using deep learning.

## How it works 
1. Divide the WSI into fixed-size tiles and label each tile as positive or negative 
2. Train a Convolutional Neural Network (CNN) to classify the WSI as tumorous or normal
3. Predict a score (between 0 and 1) for each tile in a WSI randomly picked from the test set
4. Combine prediction results on tiles to create a heatmap which shows the metastases in the WSI

## Data
The datasets used in this project: **CAMELYON16** and **CAMELYON17** are available in the [CAMELYON challenge website](https://camelyon17.grand-challenge.org/Data/) 

The datasets consist of **Whole-Slide Images (WSI)** of lymph nodes sections.

**CAMELYON16** 
- Contains a total of 400 whole-slide images.
- Training set contains 270 WSI. The ground truth data for the slides containing metastases is provided in two formats: .xml files containing metastasis annotations and WSI binary Masks.
- Test set contains 130 WSI.

**CAMELYON17**
- Contains a total of 1000 whole-slide images.
- Training set and test set contain each 100 patients, and each patient consists of five WSI.
- Training set also contains 50 slides with detailed annotations of metastases.


## Prerequisites 
The modules needed to run this project can be installed using **pip**: 
- scipy==1.3.1
- progress==1.5
- graphviz==0.13.2
- openslide==3.4.1
- pandas==0.25.3
- scikit-learn==0.21.3
- scikit-image==0.16.2



## Execution Instruction

1. Add the **custom_modules** directory to **PYTHONPATH** environment variable

This directory contains the classes and functions neccessary for handling WSI and preprocessing the dataset. 

2. Run **generate_tiles.py** located in **preprocess**

Divide WSI into fixed-size 256 x 256 tiles, and separate them into positive tiles (using the annotations provided) and negative tiles (using Otsu thresholding). 

3. Run **generate_hdf5.py** located in **preprocess**

Create a single HDF5 file containing all tiles obtained with **generate_tiles.py** (this is useful in reducing reading time). 

4. Run **model.py** located in **cnn_model**

Train a CNN to predict if a tile is tumorous or normal 

5. Run **heatmap.py** located in **heatmap_creation**

Use the score predicted by the model on individual tiles to construct a heatmap of the metastases in the WSI. 

## Trained model

The trained model is available [here](https://drive.google.com/file/d/1gtrDGWj3auGixQlNfFVR5JO0AqnZeFK1/view?usp=sharing)
