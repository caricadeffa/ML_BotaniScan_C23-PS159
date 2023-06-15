# Summary of Potato Model (Best Model)

## Dataset
The dataset used is a combination of datasets from [Random Image](https://www.kaggle.com/datasets/shamsaddin97/image-captioning-dataset-random-images) and [Potato Dataset](https://github.com/spMohanty/PlantVillage-Dataset)

The dataset used in this model can be accessed at [Potato zip](https://drive.google.com/file/d/1DVLQOg8nvr5SnLAG6g7a2tL6jUBxXUlo/view?usp=drive_link)

## Prepocessing Steps
### 1. Pixel Normalization
Converting the pixel values of the image to a floating-point representation and dividing them by 255.0
### 2. Resize 
Resizes the image to a new width and height of 224 pixels each
### 3. Balancing dataset
Create a balanced dataset by selecting a specific number of images from each class and copying them to a new directory

The result of preprocessing data is as follows 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/c9c0f8c9-06c9-45ac-a0d2-7e43a264452b" width="600px">

## Split Dataset
Divide the dataset into three parts: train, validation, and test with composition 
Train : 80%, Validation: 10%, and Test : 10%

## Build Model
This model uses a sequential model with a Conv2D layer followed by MaxPooling2D, flatten, dropout, and dense. The model was used to classify images with 4 different classes namely non potato, potato early blight, potato healthy, potato late blight.
A summary of the model can be seen in this image 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/72c2337b-493a-4b23-bffe-660665483441" width="600px">

To train and evaluate the model, callbacks are defined : earlystopping and modelcheckpoint. The model is then compiled using Adam's optimizer, loss function categorical crossentropy, and metric accuracy. With 50 epochs, the results of model training can be seen in the following figure

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/ba39447d-9862-4120-bf9f-a5f893f9f26a" width="600px">

On the validation generator, obtained
test loss: 0.009127928875386715 and test accuracy: 0.9975000023841858
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/ec6b118a-c929-4da2-8eb1-4cdf989969fc" width="600px">

While on the test generator, obtained
test loss: 0.03554805368185043 and test accuracy: 0.9775000214576721
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/46eaae10-2151-42ef-a1c4-f0069d976a47" width="600px">

Overall, the model has good performance on test data and validation data. Low loss values and high accuracy indicate that the model is able to classify both data sets well. The difference between loss and accuracy in the test data and validation data is very small, which indicates that the model is not overfitting to the training data and can generalize well to data not used in training

## Plotting Accuracy and Loss of Training and Validation

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/8a4a899f-db25-4a95-bdfa-f1d5882c409f" width="600px">


## Confusion Matrix
The confusion matrix generated using test data looks like the following image

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/20ab9e65-b7f7-45d6-a5e9-5ecd455499f7" width="600px">

It can be seen that the model classifies not potato class correctly. While in the potato early blight class, there are 2 times the model error classifying to potato late blight. There is 5 time model error classifying potato late blight as potato healthy. And there is 2 time model error classifying potato early blight and potato healthy as potato late blight

## Classification Report 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/8a8a119a-7cf3-4256-88ec-48acd1b2e8a0" width="600px">
     
## Testing Images
Testing is done by uploading images. With some sample images, the results show that the model has classified 3 images according to existing classes

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/125848966/177c0b92-6e60-4f4f-979c-495a085f67d2" height="600px">

## Saving Model
The model is saved in .h5 form and can be directly downloaded using the available code 
