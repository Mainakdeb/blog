+++
title =  "GSoC - Coding Period Week 7"
tags = ["GSoC", "DevoWorm"]
date = "2021-07-25"
+++

## Work Done This Week (July 20th to July 25th)

* Converted the nucleus segmentation model into ONNX ([Link to code](https://github.com/Mainakdeb/GSoC-2021/blob/main/cell-nucleus-segmentation/torch_to_onnx.ipynb))
* Began working on the DevoLearn GUI, this time using [Streamlit](https://github.com/Mainakdeb/GSoC-2021/blob/main/cell-nucleus-segmentation/torch_to_onnx.ipynb), this would support multiple models on one web-app.
    * Built the pipeline to run inference using the ONNX models, ran tests to ensure the 2 segmentation models work via the GUI.
    * The user will have the ability to select any of the DevoLearn models from the drop down menu to the left, then drag and drop inputs. I've also added in some examples, just in case.

<img src="../images/gsoc-coding-period-week-7/devolearn_web_demo_1.gif" alt="" width="700" height="">


<img src="../images/gsoc-coding-period-week-7/devolearn_web_demo_2.gif" alt="" width="700" height="">


* The GIFs above showcase the current progress. I could get 2 of the segmentation models to work with the GUI. 
* As of now, the home page contains animations that highlight what the software can do. I have plans to add more content soon.
* All related files for this work could be found here - [Github repository]()

## Planned:
* Finish building the GUI for DevoLearn, host it online on Heroku.
* Try to render interactive plots (using Plotly) in the GUI. 
* Look into ways of running bulk inference using the web-GUI.
* Move from Travis CI to Github Actions.