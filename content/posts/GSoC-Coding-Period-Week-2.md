+++
title =  "GSoC - Coding Period Week 2"
tags = ["GSoC", "DevoWorm"]
date = "2021-06-20"
+++

The goal for this week was to upgrade the DevoLearn cell membrane segmentation model. Feel free to check out the code - [Link](https://github.com/Mainakdeb/GSoC-2021/tree/main/cell-membrane-segmentation)

## Work Done This Week (June 14th to June 20th)

### 1. Fixed the Preprocessing Pipeline:
* Fixed a strange issue that led to an offset in the image filenames.
* Used PNG format to store the images instead of JPG (which was being used).
* The JPG format led to lossy edges in segmentation maps, which was being tackled using OpenCV based operations, but that led to larger gaps between the segmentation maps of individual cells. This has been fixed.
* Saved postprocessed data in Google Drive, links below:
    * Postprocessed Images - [Google Drive link](https://drive.google.com/file/d/1wy53XglZl5Pgdq0V6pT3Q7DJeTheZmoh/view?usp=sharing)
    * Csv file - [Google Drive link](https://drive.google.com/file/d/1-BE9yxcEW9i_-GPrIc7ABkosXOAKIES-/view?usp=sharing)
    * Original data - [Paper Link](https://www.researchgate.net/publication/332572299_3DMMS_Robust_3D_Membrane_Morphological_Segmentation_of_C_elegans_embryo), [Data on Figshare](https://figshare.com/articles/dataset/Dataset_for_MMS/7781777)
* The diagram below highlights the difference between new and old training data.

![](../images/gsoc-coding-period-week-2/compare_training_data.png)

### 2. New Augmentation techniques:
* Added in a couple more [Albumentations](https://github.com/albumentations-team/albumentations) based image augmentation techniques.
### 3. Automated Hyperparameter Optimization:
* Used Optuna to automate the process of finding optimal hyperparameters, I used it to optimize the learning rate and batch size to maximize the IOU score.
* Ran 100 Optuna trials, 1 epoch each, on 10% of available data.

### 4. Training metrics:
* The image below showcases metrics after 50 epochs of training.

![](../images/gsoc-coding-period-week-2/training_metrics.png)

### 5. Old vs New Model:
* The code to generate the following plots could be found in the [training notebook](https://github.com/Mainakdeb/GSoC-2021/blob/main/cell-membrane-segmentation/train_segmentation_model.ipynb). 

![](../images/gsoc-coding-period-week-2/comparision_oldvsnew.gif)

![](../images/gsoc-coding-period-week-2/comparision_1.png)

![](../images/gsoc-coding-period-week-2/comparision_2.png)

## Planned:
* Push the upgraded cell membrane segmentation model into the main DevoLearn repository.
* Work on upgrading the DevoLearn lineage population model.
* Revamp the existing DevoLearn starter notebook, add interactive plots.