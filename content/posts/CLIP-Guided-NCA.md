+++
title =  "CLIP Guided Neural Cellular Automata using PyTorch"
tags = ["Emergent Systems", "Cellular Automata", "Neural Networks"]
date = "2022-06-06"
+++
 

<img src="../images/CLIP-Guided-NCA/clip_pytorch_logo_wide.gif" width=800>

The gif above was generated using outputs from a Neural Cellular Automata model steered by OpenAI's CLIP (language model trained on image-text pairs) using the text prompt "The PyTorch Logo". 

## Primer on Neural CA
Classical Cellular Automata employs a set of predefined rules set by humans to update the grid state.  In neural CA, we let a neural network decide the rules as it trains and we guide this process using the language of loss functions. 

<img src="../images/CLIP-Guided-NCA/primer_nca.png" width=800>

Once the network is trained, we can iteratively run forward passes and eventually get closer to our target grid-state.

## Leveraging CLIP
[OpenAI's CLIP](https://openai.com/blog/clip/) (Contrastive Language-Image Pre-training) is trained on image-text pairs. 

The CLIP model consists of 2 sub-models:
* Text Encoder
* Image Encoder

Given an image and a text sequence, we could compare their encoding vectors (of the same dimension) to measure how relevant the caption is to the image. 

Cellular automata states can be encoded and then compared to text-encodings for a certain piece of text. In order top quantify this comparision, one could compute the cosine similarity or the dot product. 

## The CA Model

The CA model that I used is heavily inspired from the architecture used in the [Self Organizing Textures Paper](https://distill.pub/selforg/2021/textures/).

We start out with a pool of noise tensors, with shape ```[pool_size, num_channels, width, height]```. Let's trace along one forward pass for a batch of 1 sampled from the pool 

1. The first step is to Convolve the input tensor ```[1, 12, 128, 128]``` with four 3x3 fiilters. The idea behind this is to give the individual cell an idea of its neighboring pixels.

<img src="../images/CLIP-Guided-NCA/perception.png" width=800>

2. The resulting tensor ```[1,48,128,128]``` is then fed into 2 successive Convolutional Layers.  

<img  src="../images/CLIP-Guided-NCA/nca_model.png" width=800>

3. The model output is added to the input but before we perform this addition, we apply a boolean update mask over the network output (update vector). This operation can be also seen as an application of per-cell dropout. 

<img src="../images/CLIP-Guided-NCA/update_grid.png" width=800>

We replace samples in the pool that were sampled for the batch with the output states from the training step over this batch.

## Guiding the CA Model
Our target is a string of text, this text is encoded using the CLIP text encoder.  

We only consider the first 3 channels (as RGB) of the 12 channel samples when computing the loss. The CLIP image encoder is used to encode a batch of images, and is compared to the encoded target text. 
<img src="../images/CLIP-Guided-NCA/dot_product.png" width=835>

We also use penalize the model for pixel values lying beyond the range of ```(-1.0, 1.0)``` which we reser to as the overflow loss. The loss value of a batch could be represented as:
<center><b><tt>Loss = -torch.mean(dot product values of batch) + Overflow Loss</tt></b></center>

## Results
<figure>
<center><img src="https://raw.githubusercontent.com/Mainakdeb/text-2-cellular-automata/main/media/gifs/nose_cropped_compressed.gif" width=400>
<figcaption>"noses"</figcaption></center>
</figure>

<figure>
<center><img src="https://github.com/Mainakdeb/project-omega/raw/main/media/gifs/underwater_bioluminescence_16:9_compressed.gif" width=400>
<figcaption>"Underwater Bioluminescence"</figcaption></center>
</figure>

<figure>
<center><img src="https://raw.githubusercontent.com/Mainakdeb/text-2-cellular-automata/main/media/gifs/clip_pytorch_logo_16%3A9.gif
" width=400>
<figcaption>"The PyTorch Logo"</figcaption></center>
</figure>

<figure>
<center><img src="https://github.com/Mainakdeb/project-omega/raw/main/media/gifs/northern_lights_meteor_shower_collage_short.gif" width=700>
<figcaption>"The Northern Lights" and "Meteor Shower"</figcaption></center>
</figure>

## Credits
* [Growing Neural Cellular Automata paper](https://distill.pub/2020/growing-ca/)
* [Self Organizing textures paper](https://distill.pub/selforg/2021/textures/)
* [OpenAI CLIP](https://openai.com/blog/clip/)
* [Neural CA from scratch (video tutorial)](https://www.youtube.com/watch?v=8EN_8p9Toyc) by [Alexander Mordvintsev](https://twitter.com/zzznah)
* [Blog post on image filters](https://setosa.io/ev/image-kernels/) by [Victor Powell](https://twitter.com/vicapow)
* [Cosine similarity vs dot product as distance metrics](https://datascience.stackexchange.com/questions/744/cosine-similarity-versus-dot-product-as-distance-metrics)

