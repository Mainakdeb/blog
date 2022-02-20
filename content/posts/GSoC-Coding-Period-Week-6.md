+++
title =  "GSoC - Coding Period Week 6"
tags = ["GSoC", "DevoWorm"]
date = "2021-07-19"
+++

## Work Done This Week (July 12th to July 19th)

* Swapped out the model for the Cell membrane segmentation with the upgraded model in DevoLearn's repository, ran tests locally before pushing because Travis has been discontinued. ([Link to commit](https://github.com/DevoLearn/devolearn/commit/e65b2f71f597fcfc1358f7fb44ea36e3e9fc9f3e))

<img src="../images/gsoc-coding-period-week-6/tests_local_3_models.png" alt="" width="1000" height="">

* Renamed the `embryo_segmentor` package to `cell_membrane_segmentor`. The reason for this renaming is to avoid naming conflicts when new segmentation models are added. ([Link to commit](https://github.com/DevoLearn/devolearn/commit/e2da9401d6712e7b0c6667ba803e50bda8e9457c))
    * Old syntax - `from devolearn import embryo_segmentor`
    * New syntax - `from devolearn import cell_membrane_segmentor`

* Integrated the new nucleus segmentation model into the library ([Link to commit](https://github.com/DevoLearn/devolearn/commit/bc59be395a68e4565ecde007426c778cc3f047ed))
    * Wrote the necessary functions to run inference, on CPU and GPU.
    * Made additions to the testing script to accomodate this additional model.
    * Steps for usage:
        1. `from devolearn import cell_nucleus_segmentor`
        2. `segmentor = cell_nucleus_segmentor(device='cuda')`
        3. `pred = segmentor.predict(image_path = "input_image.png")`
        4. `plt.imshow(pred)`

* Inference Examples:
    1. Input image with Varying Z axis -
    <img src="../images/gsoc-coding-period-week-6/z_infer.gif" alt="" width="1000" height="">

    2. Inputs varying through time -
    <img src="../images/gsoc-coding-period-week-6/time_infer.gif" alt="" width="1000" height="">


## Planned:
* Build a GUI for all DevoLearn models and host them online.
* Look into ways of running bulk inference using the web-GUI.
* Move from Travis CI to Github Actions.