# Metastatic Cancer Detection
Histopathological-based Metastatic Cancer Detection using Deep learning - Group 5 Project

# Overview

Breast cancer metastases detection using CNN.

## How it works 
1. Divide the WSI into fixed-size tiles and label each tile as positive or negative 
2. Train a Convolutional Neural Network (CNN) to classify the WSI as tumor or normal
3. Predict a score (from 0 to 1) for each tile in the WSI in the test set
4. Combine prediction results on tiles of a WSI to create a heatmap 

# Data
The datasets used in this project:CAMELYON16 and CAMELYON17 are available in the [CAMELYON challenge website](https://camelyon17.grand-challenge.org/Data/) 

# Execution order
1. run generate_tiles.py in preprocess: divide WSI into fixed-size 256 x 256 tiles, and separate them into positive tiles (using the annotations provided) and negative tiles (using Otsu thresholding). 
2. run generate_hdf5.py in preprocess: create a single HDF5 file containing all tiles generated with generate_tiles.py (this is useful to reduce reading time). 
3. run model.py in cnn_model: train a CNN to predict if a tile is tumorous or normal 
4. run heatmap.py in heatmap_creation: use the score predicted by the model on individual tiles to construct a heatmap of the WSI which shows which part contains metastases. 

The trained model is available [here](https://drive.google.com/file/d/1gtrDGWj3auGixQlNfFVR5JO0AqnZeFK1/view?usp=sharing)
