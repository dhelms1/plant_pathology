# Plant Pathology Project

<img src="/Image/header.png" width="600">

### Project Description:
This project was taken from the [Kaggle competition](https://www.kaggle.com/c/plant-pathology-2020-fgvc7/overview/evaluation) for plant pathology. Misdiagnosis of the many diseases impacting agricultural crops can lead to misuse of chemicals leading to the emergence of resistant pathogen strains, increased input costs, and more outbreaks with significant economic loss and environmental impacts. In this project, we will use images of apple leaves to train a model that can correctly diagnose infected and healthy leaves. We will transform images in such a way that trains the model for real world data that would be submitted by a user (different brightness, angles, leaf positioning, coloring, etc.). 

#### The focus of this project:
- Formatting image directories to be used in *ImageFolder* and *DataLoader*.
- Image augmentation to replicate real world data examples.
- Creating custom datasets for unlabeled testing data.
- Implement transfer learning to use pretrained models for training and predicting.
- Saving and loading model checkpoints.

#### Requirements:
- [PyTorch](https://pytorch.org/get-started/locally/) using CUDA.
- [EfficientNet](https://pypi.org/project/efficientnet-pytorch/) for PyTorch.
- Main packages: Sklearn, Matplotlib, Seaborn, NumPy, and Pandas.

**submission3.csv** contains the predictions using the EfficientNet b5 model trained for 30 epochs. This resulted in a 95.9% testing accuracy. Note that the checkpoint containing the model state_dict could not be uploaded since it is around 350 MB. [Click here](https://drive.google.com/drive/folders/1qPAkrDkLgOGlSVm_I-g8QLYljSj7584L?usp=sharing) for link to Google Drive folder containing the model parameters. 
