+++
title =  "GSoC - Community Bonding"
tags = ["GSoC", "DevoWorm"]
date = "2021-06-06"
+++

This blog post summary of what I've been doing this week and what I plan to do in the coming week.

## Work Done This Week :
* Gave a presentation on the weekly DevoWorm meeting, discussed the goals and deadlines that need to be met in the coming months - [link to the slides](https://docs.google.com/presentation/d/1VR5oWVtKlGROYGVXpA4JboOeKzyke3N0hIJUphotOZA/edit?usp=sharing)
* Read some articles/papers suggested by my mentor that deal with working with communities and collaboration, liked one in particular that talks about "bursty" communication and how it helps remote teams thrive - [link](https://drive.google.com/file/d/1Kf6zMxhCUX0orIAPlDsHfSvzxUoAh9B3/view)
* Read publications that deal with extracting data from C. elegans embryogenesis data, tried to find possible applications that could be implemented. I've linked to some of the papers I came across below:
  * [Segmentation and classification of two-channel C. elegans nucleus-labeled fluorescence images](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5602880/)
  * [3D cell nuclei segmentation based on gradient flow tracking](https://www.researchgate.net/publication/6055472_3D_cell_nuclei_segmentation_based_on_gradient_flow_tracking)
  * [3D convolutional neural networks-based segmentation to acquire quantitative criteria of the nucleus during mouse embryogenesis](https://www.nature.com/articles/s41540-020-00152-8) - 

* The last paper in the list above links to the [cell-tracking-challenge website](http://celltrackingchallenge.net/), which contains download links to many datasets, among which I found a 3D+t fluorescence microscopy dataset of the developing C. elegans embryo with segmentation maps - [link](http://celltrackingchallenge.net/3d-datasets/).

* I had zero experience with _.tif_ files, had to figure out how to convert them to numpy arrays, then used matplotlib to plot them as images.

![](../images/gsoc-community-bonding-1/inferno_sbs_celltrackingchallenge.png)

* The dataset is by no means ideal, it is scattered across multiple folders and contains many useless datapoints near the extreme ends of the dorsal-ventral axis.

![](../images/gsoc-community-bonding-1/inferno_sbs_celltrackingchallenge_grid.png)

* Links to the notebook :
  * [Google Colab](https://colab.research.google.com/github/Mainakdeb/GSoC-2021/blob/main/3d-embryo-segmentation/explore_and_preprocess_data.ipynb)
  * [NBviewer](https://nbviewer.jupyter.org/github/Mainakdeb/GSoC-2021/blob/main/3d-embryo-segmentation/explore_and_preprocess_data.ipynb)
  * [Github repository](https://github.com/Mainakdeb/GSoC-2021)
## Planned :
* Begin working on upgrading the DevoLearn embryo segmentation model. 
* Explore and clean the cell-tracking-challenge dataset. 
* Discuss in detail about how the cell-tracking-challenge dataset could be used to automate the process of 3D cell-segmentation.
