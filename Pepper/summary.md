# Summary of Bell Pepper Model (Best Model)

## Dataset
The dataset used is a combination of datasets from [Random Image](https://www.kaggle.com/datasets/shamsaddin97/image-captioning-dataset-random-images) and [Bell Pepper Dataset](https://github.com/spMohanty/PlantVillage-Dataset)

The dataset used in this model can be accessed at [Bell pepper zip](https://drive.google.com/file/d/1dl0G9o_2UmnSfPGeFLRQwvCwk0s8b4Xr/view)

## Prepocessing Steps
### 1. Pixel Normalization
Converting the pixel values of the image to a floating-point representation and dividing them by 255.0
### 2. Resize 
Resizes the image to a new width and height of 224 pixels each
### 3. Balancing dataset
Create a balanced dataset by selecting a specific number of images from each class and copying them to a new directory

## Split Dataset
Divide the dataset into three parts: train, validation, and test with composition 
Train : 70%, Validation: 15%, and Test : 15%

## Build Model
This model uses a sequential model with a Conv2D layer followed by MaxPooling2D, flatten, dropout, and dense. The model was used to classify images with 3 different classes namely bell pepper healthy, bell pepper bacterial spot, and not bell pepper.
A summary of the model can be seen in this image 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/4fe0361d-242f-4adf-ad23-fdea640fce06" width="600px">

To train and evaluate the model, callbacks are defined : earlystopping and modelcheckpoint. The model is then compiled using Adam's optimizer, loss function categorical crossentropy, and metric accuracy. With 50 epochs, the results of model training can be seen in the following figure

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/c63e26b0-4012-4854-ac78-00407e46d68a" width="600px">


## Plotting Accuracy and Loss of Training and Validation

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/7616e09c-07cc-4c23-8793-b6f7a7e4bb49" width="600px">


## Confusion Matrix
The confusion matrix generated using test data looks like the following image

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/4e099c7f-a647-4f91-a0fb-90d5a3c1fe0f" width="600px">

It can be seen that the model classifies Not Bell Pepper class correctly. While in the bacterial spot class, there are 2 times the model error classifying to bell pepper healthy. And there is 1 time model error classifying bell pepper healthy as not bell peper.

## Classification Report 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/8881b8e1-6a9d-43db-924e-88eaec924217" width="600px">
     
## Testing Images
Testing is done by uploading images. With some sample images, the results show that the model has classified 3 images according to existing classes

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/432599f1-a7a7-4a7b-abd5-5a0e0b5443a9" height="300px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/1e87ea85-cd02-43d1-808c-64ecb8553c9b" height="300px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/96445426/f3460f8b-3cd0-4c5b-bd3e-a69b341be9ec" height="300px">

## Saving Model
The model is saved in .h5 form and can be directly downloaded using the available code 





