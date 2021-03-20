# Plant Pathology Project

<img src="/Image/header.jpg" width="600">

---

## Project Overview & Goal:
"Misdiagnosis of the many diseases impacting agricultural crops can lead to misuse of chemicals leading to the emergence of resistant pathogen strains, increased input costs, and more outbreaks with significant economic loss and environmental impacts. Current disease diagnosis based on human scouting is time-consuming and expensive, and although computer-vision based models have the promise to increase efficiency, the great variance in symptoms due to age of infected tissues, genetic variations, and light conditions within trees decreases the accuracy of detection" [Plant Pathology 2020](https://www.kaggle.com/c/plant-pathology-2020-fgvc7). 

The overall goal of this project is to create a multi-class deep learning model that is able to correctly classify apple leaf diseases from our given data. Images will be augmented using cropping, rotation, saturation, and other alterations that will help reinforce the model and prepare it for real world use case. Two models will be fitted and compared for both accuracy and computational speed, since in a real world application we may need to sacrifice accuracy for prediction speed for better user experience. More details about the models and data format will be given in the following section.

*An important note is that this project was created using Google Colab, so Drive must be mounted and formatted in the same directory paths specified in the project in order to run the project.*

---

## Data
The original data for this project came from the [Kaggle](https://www.kaggle.com/c/plant-pathology-2020-fgvc7) Plant Pathology competition. Although the training data came labeled in a csv, it was reformatted to be used in the ImageFolder PyTorch function. The testing data was formatted by creating a custom Dataset class that read in the unlabeled images and converted them to Tensors of the correct size. The data consists of 4 different class labels:
- combinations: contains multiple diseases (mixture of below labels)
- healthy: no disease present on the leaf.
- rust: yellow spots that appear due to fungus.
- scab: dark spots that occur due to fungues.

Training data was augmented (see notebook for details about alterations) but validation/testing data was only resized, normalized, and converted to Tensors. Below is the final format of the data:

<img src="/Image/data_aug.jpg" width="400">

*Requested cite: https://arxiv.org/abs/2004.11958*

---

## Modeling:
*To be filled in...* [EfficientNet](https://pypi.org/project/efficientnet-pytorch/) for PyTorch.

---

**submission3.csv** contains the predictions using the EfficientNet b5 model trained for 30 epochs. This resulted in a 95.9% testing accuracy. Note that the checkpoint containing the model state_dict could not be uploaded since it is around 350 MB. [Click here](https://drive.google.com/drive/folders/1qPAkrDkLgOGlSVm_I-g8QLYljSj7584L?usp=sharing) for link to Google Drive folder containing the model parameters. 
