+++
title =  "GSoC - Coding Period Week 1"
tags = ["GSoC", "DevoWorm"]
date = "2021-06-14"
+++

This blog post showcases what I did last week and what I plan to do next.

## Work Done This Week (June 7th to June 13th)

### 1. JPEG or PNG?

* Last week I was able to convert the `.tif` files from the cell-tracking-challenge dataset into NumPy arrays. The next goal was to save these NumPy arrays as image files. 

* Here's where I made a mistake, I saved the images as `.jpeg` files. 

* What I didn't know is that JPEG is a lossy compression method, it changes pixel level values as long as it "looks good" to the human observer.

* I used plotly to zoom into the saved `.jpeg` files, and noticed that the edges of the segmentation masks were noisy, then I plotted the images in 3D, with z axis as pixel value.

<img src="../images/gsoc-coding-period-week-1/compare_png_jpeg.png" alt="" width="700" height="">
<img src="" alt="" width="1000" height="">


* Turns out, JPEG is a lossy compression method - it is designed to save images using less bits even if it changes the pixel values as long as it "looks good" to a human observer.

* I decided to save the images in `.png` format; PNG is a lossless compression method. 

* Each `.tif` file contains 3D data (as slices) from a single instant of time, I've named the corresponding `.png` files accordingly.
    * `features/F{time-point}_{slice}.png`
    * `segmentation_maps/L{time-point}_{slice}.png`  

* Link to code:
    * [Github](https://github.com/Mainakdeb/GSoC-2021/blob/main/3d-embryo-segmentation/explore_and_preprocess_data.ipynb)
    * [Google Colab](https://colab.research.google.com/github/Mainakdeb/GSoC-2021/blob/main/3d-embryo-segmentation/explore_and_preprocess_data.ipynb)


### 2. Defining The Dataset and Dataloader in PyTorch:
* I did not want to use `torchvision.datasets.ImageFolder()` for the dataset class.
* The filenames (both features and labels) contain the time-point and slice number, which could be used to identify unique feature-label pairs.
* I created a Pandas DataFrame that contains these unique id's and saved it as a csv file, using which the custom dataloader loads valid feature-label pairs.

### 3. Experimenting with Gradio:
* [Gradio](https://www.gradio.app/) has been all over the ML community lately, I decided to give it a try. 
* The Gif below showcases a simple GUI (prototype) for the existing DevoLearn embryo segmentation model.

<img src="../images/gsoc-coding-period-week-1/gui_demo.gif" alt="" width="700" height="">


* This still needs a lot more work. I'll try to resume work on this after I'm done with the proposed work for next week.

## Planned:
* Upgrade the existing embryo segmentation model.
* Spend more time on the GUI for the existing segmentation model.
* Look into ways of hosting PyTorch + Gradio based apps online. 