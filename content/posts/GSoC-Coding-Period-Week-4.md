+++
title =  "GSoC - Coding Period Week 4"
tags = ["GSoC", "DevoWorm"]
date = "2021-07-05"
+++

Most of my time this week was spent on building the training pipeline for the proposed cell nucleus segmentation model in C. elegans embryos.

## Work Done This Week (June 28th to July 4th)

* Back in [week-1](https://mainakdeb.github.io/posts/gsoc-coding-period-week-1/), I had worked on preprocessing data from the cell-tracking-challenge dataset. The dataset was extracted from `.tif` files and saved as pairs of `.png` files.


* To prevent anu CPU bottlenecks while training, I used PIL to resize all the training images to 1x256x256 beforehand.

* Defined a custom Dataset class for the data, this class uses a csv file that contains image id's, which are being used to identify feature-label pairs.

* Used Albumentations to define the image augmentation pipeline. Also defined a new class to add gaussian noise in training images (inputs only). The image below shows feature-label pairs from the training data, notice that one of the input images contains a lot more noise.

    ![](../images/gsoc-coding-period-week-4/training_data.png)


* Ran some tests to ensure that the dataloader works properly, plotted some feature-label pairs for visual inspection.

* Defined the network:
    * Type - Feature Pyramid Network
    * Backbone - ResNet-18

* Defined a rough training loop and trained the model for a couple epochs as a test. The image below showcases the metrics for the 2 epoch test-run. The IOU score is close to 79 after the 2nd epoch, which is not bad. 


    ![](../images/gsoc-coding-period-week-4/train_metrics_2_epochs.png)

    ![](../images/gsoc-coding-period-week-4/inference_2_epochs.png)

* Feel free to check out this work:
    * Github - [Link](https://github.com/Mainakdeb/GSoC-2021/blob/1cbe0e8429671491168f3cceaa602d5953e85df3/cell-nucleus-segmentation/train_segmentation_model.ipynb)
    * NBViewer - [Link](https://nbviewer.jupyter.org/github/Mainakdeb/GSoC-2021/blob/1cbe0e8429671491168f3cceaa602d5953e85df3/cell-nucleus-segmentation/train_segmentation_model.ipynb)


## Planned:
* Continue working on the nucleus segmentation model.
    * Use Optuna to find suitable hyperparameters.
    * Experiment with mixed precision training and inference.
    * Build and deploy a GUI after training the model.
