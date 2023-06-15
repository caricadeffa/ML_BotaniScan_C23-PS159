# Summary of Corn Model (Best Model)

## Dataset
The dataset used is a combination of datasets from [Random Image](https://www.kaggle.com/datasets/shamsaddin97/image-captioning-dataset-random-images) and [Corn Dataset](https://github.com/spMohanty/PlantVillage-Dataset)

The dataset used in this model can be accessed at [Corn Dataset](https://drive.google.com/file/d/1gxrIm8GTs65D9eFprwYoboN-PcetNZ7_/view?usp=sharing)

## Prepocessing Steps
### 1. Resize 
This stage is performed on the images contained in the "Not_Corn" directory. Next, for each image in not_corn_images, the image is read using cv2.imread, resized to 256x256 pixels using cv2.resize, and saved again with the new size using cv2.imwrite. This process is performed for all images in the "Not_Corn" directory.
### 2. Rename
Rename the image files in each folder according to the corn class in question.

The result of preprocessing data is as follows 

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/39f3f221-9d76-4ef8-b902-5c130ffcf4bb" width="600px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/01adc743-05e3-44c4-a5fa-b98877de2496" width="600px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/701d9da9-0b4f-4d31-8bc0-c4fa0f4cdb90" width="600px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/c070a4d6-be7b-4c45-914c-ca3be581183f" width="600px">
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/858d7c21-1fb2-4bf7-87e8-5ce36b43f0e1" width="600px">

## Split Dataset
The data is divided into training data and validation data using validation_split=0.15 on the ImageDataGenerator object. The training data will be used to train the model, while the validation data will be used to evaluate the model's performance during training.

## Build Model
The Neural network model is built using Sequential objects from Keras. This model consists of several interconnected layers. Until finally, softmax activation is used in the output layer to get class prediction probabilities.
A summary of the model can be seen in this image.  Here are the layers used:
- Conv2D and MaxPooling2D: Convolution and pooling layers for performing feature extraction from images.
- Flatten: Layer for converting image representation to vector.
- Dropout: A dropout layer to reduce overfitting by randomly turning off some units during training.
- Dense: The fully connected (dense) layers that connect all units from the previous layer.

<center>
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/f3c3d873-af9a-4610-8b6b-deb779d0893e" width="600px">
</center>

To train and evaluate the model, callbacks are defined : earlystopping and modelcheckpoint. The model is then compiled using Adam's optimizer, loss function categorical crossentropy, and metric accuracy. With 30 epochs, the results of model training can be seen in the following figure.

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/10616a68-87b1-413a-a4ff-4d79dc2a37f5" width="600px">

On the validation generator, obtained
test loss: 0.27271974086761475 and test accuracy: 0.9479940533638

In general, the model demonstrates good performance on both the test data and validation data. The low loss value and high accuracy achieved on the test data indicate that the model effectively classifies the samples. Furthermore, the test loss and accuracy values obtained from the validation generator are comparable, suggesting that the model does not suffer from overfitting and can generalize well to new, unseen data. 

## Confusion Matrix
The confusion matrix for the classification as the picture below.
<center>
<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/1919fb05-e014-4e43-9d95-ef4062dd802f" width="600px">
</center>

It can be seen that the corn disease classification model works well, but there are some misclassifications in the class corn_cercospora_leaf_spot and random images.

## Testing Prediction
Testing is done by uploading image from local computer. With some sample images, the results show that the model has classified the images according to appropriate class with the details:
Class Predictions:
- Corn_Cercospora_Leaf_Spot_Gray_Leaf_Spot: 0.00%
- Corn_Common_Rust: 0.00%
- Corn_Healthy: 0.00%
- Corn_Northern_Leaf_Blight: 0.00%
- Not_Corn_Clean: 100.00%

Highest Prediction:
- Not_Corn_Clean: 100.00%

Highest Prediction: Not_Corn_Clean: 100.00%

<img src="https://github.com/caricadeffa/ML_BotaniScan_C23-PS159/assets/136357806/537bff8d-9a33-4aaa-9e27-9b62d8a5d84c" height="300px">

## Saving Model
The model is saved in .h5 form and can be directly downloaded from the colab file manager. 
