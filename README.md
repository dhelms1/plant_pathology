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
- **multiple_diseases**: contains multiple diseases (mixture of below labels)
- **healthy**: no disease present on the leaf.
- **rust**: yellow spots that appear due to fungus.
- **scab**: dark spots that occur due to fungues.

Training data was augmented (see notebook for details about alterations) but validation/testing data was only resized, normalized, and converted to Tensors. Below is the final format of the data:

<img src="/Image/data_aug.jpg" width="600">

*Requested cite: https://arxiv.org/abs/2004.11958*

---

## Modeling:
Transfer learning was implemented for both models used in this notebook, one being [MobileNet v2](https://pytorch.org/hub/pytorch_vision_mobilenet_v2/) and the other [EfficientNet b5](https://pypi.org/project/efficientnet-pytorch/). One important note is that EfficientNet used a batch size of 8 while MobileNet used a batch size of 32. Both models had their final layer replaced by a fully connected layer and a softmax output.

Looking first at the **MobileNet v2** model we have the following results after training and validating:

<img src="/Image/mobilenet.jpg" width="750">

We can see the training loss (blue line) seemed to even out around 0.5 after 10 epochs, as well as the validation loss staying near 0.3. Similarly, the training accuracy (blue line) seemed to increase to around 83% as our epochs increased as well as the validation accuracy averaging about 87% as the epochs increased.

Looking first at the **EfficientNet b5** model we have the following results after training and validating:

<img src="/Image/efficient.jpg" width="750">

We can see the training loss (blue line) seemed to even out around 0.4 after 15 epochs, as well as the validation loss staying near 0.2 to 0.3. Similarly, the training accuracy (blue line) seemed to continue increasing as our epochs grew, reaching around 88%.  The validation accuracy was averaging about 93% after the 18th epoch, with a slight dip on the 27th epoch (where the loss also spiked). 

### Conclusion
The EfficientNet model seemed to be performing better on the training and validation set, and after using the model to predict on the testing set we could see it had around a 4% accuracy advantage over the MovileNet model. An important note is that for submission 2 below, the EfficientNet model was trained for the same epochs as the MobileNet model (25 epochs) but after seeing it performed better on the testing data, we retrained and extended the number of epochs for submission 3. The difference in computational speed was also quick large, with MobileNet taking around 2 minutes to predict while EfficientNet took around 19 minutes on the 1821 test images. This will be important to keep in mind if we were worried about response time in an application (but is not a large concern for just the notebook).

---

**submission3.csv** contains the predictions using the EfficientNet b5 model trained for 30 epochs. This resulted in a 95.9% testing accuracy. Note that the checkpoint containing the model state_dict could not be uploaded since it is around 350 MB. [Click here](https://drive.google.com/drive/folders/1qPAkrDkLgOGlSVm_I-g8QLYljSj7584L?usp=sharing) for link to Google Drive folder containing the model parameters.


