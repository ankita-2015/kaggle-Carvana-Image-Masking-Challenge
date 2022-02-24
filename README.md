# kaggle-Carvana-Image-Masking-Challenge

In this competition, we’re challenged to develop an algorithm that automatically removes the photo studio background. This will allow Carvana to superimpose cars on a variety of backgrounds. You’ll be analyzing a dataset of photos, covering different vehicles with a wide variety of year, make, and model combinations.

challenge : [link](https://www.kaggle.com/c/carvana-image-masking-challenge)
![image](https://user-images.githubusercontent.com/29517840/155557658-7409be20-27e9-4ecb-83a8-f84d371cfb50.png)

## Data Description

Input Image Resolution :
  - width : 1918
  - height: 1280
- 5088 training images
- 100064 test images

The metric used to score this competition requires that your submissions are in run-length encoded format.

## Solution Overview
 I have trained 3 different models on image size = (320, 480):
 
  1. UNet architecture with pretrained MobileNetV2 encoder.
  2. DeeplabV3p with MobileNetV2 architecture with pretrained cityscapes weights
  3. DeeplabV3p with MobileNetV2 architecture with pretrained MobilenetV2 encoder

For training and generating test results i have used efficient data pipeline [tf.data](https://www.tensorflow.org/guide/data)

## Results
 I have recieved these results on training each model for just 10 epochs.
 
  | Model | backbone|score|Remark|
  | :---: | :---: | :---: | :--- |
  | Unet |mobilenetV2| 0.92799 | with pretrained encoder|
  | DeeplabV3p | mobilenetV2| 0.99217 | with pretrained [cityscapes weights](https://github.com/bonlime/keras-deeplab-v3-plus/releases/download/1.2/deeplabv3_mobilenetv2_tf_dim_ordering_tf_kernels_cityscapes.h5)|
  | DeeplabV3p (custom) | mobilenetV2| 0.99217 | with pretrained encoder only|

