# Assignment11
# Session 11 - Assignment

## Basic expectations
- Follow good structure for Code (Reference: https://github.com/kuangliu/pytorch-cifar)
- Create
  - models folder - this is where you'll add all of your future models. Copy resnet.py into this folder, this file should only have ResNet 18/34 models. Delete Bottleneck Class
  - main.py - from Google Colab, now onwards, this is the file that you'll import (along with the model). Your main file shall be able to take these params or you should be able to pull functions from it and then perform operations, like (including but not limited to):
    - training and test loops
    - data split between test and train
    - epochs
    - batch size
    - which optimizer to run
    - do we run a scheduler?
  - utils.py file (or a folder later on when it expands) - this is where you will add all of your utilities like:
    - image transforms,
    - gradcam,
    - misclassification code,
    - tensorboard related stuff
    - advanced training policies, etc
    - etc
  - Your assignment is to build the above training structure. Train ResNet18 on Cifar10 for 20 Epochs. The assignment must:
    - pull your Github code to Google Colab (don't copy-paste code)
    - prove that you are following the above structure
    - that the code in your Google Colab notebook is NOTHING.. barely anything. There should not be any function or class that you can define in your Google Colab Notebook. Everything must be imported from all of your other files
    - your colab file must:
      - train resnet18 for 20 epochs on the CIFAR10 dataset
      - show loss curves for test and train datasets
      - show a gallery of 10 misclassified images
      - show gradcamLinks to an external site. output on 10 misclassified images. Remember if you are applying GradCAM on a channel that is less than 5px, then please don't bother to submit the assignment. 😡🤬🤬🤬🤬
    - Once done, upload the code to GitHub, and share the code. This readme must link to the main repo so we can read your file structure.
    - Train for 20 epochs
    - Get 10 misclassified images
    - Get 10 GradCam outputs on any misclassified images (remember that you MUST use the library we discussed in class)
    - Apply these transforms while training:
      - RandomCrop(32, padding=4)
      - CutOut(16x16)

## Reference to the main repo used for this work and understanding the base code used for running this experiment
- https://github.com/ChintanShahDS/ERAV2_Main
- Follow this to try your own Resnet18 or Resnet34 model with different hyperparameters and options

## Results:
- Model: Resnet18
- Epochs: 20
- Optimizer: SGD
- Criteria: CrossEntropyLoss
- Scheduler: OneCycleLR
- Parameters: 11,173,962
- Training Batch size: 512
- Testing Batch size: 512
- Training
  - Loss=0.2331
  - Batches=98
  - Accuracy=91.58%
- Testing
  - Average loss: 0.0005
  - Accuracy: 9213/10000 (92.13%)

## Some observations
- Ensure that the model initialization is before the Optimizer setup as the parameters are reset and model will not train
- Issues with maxlr with SGD: Incorrect slope getting picked as per me (Need to find a solution for the same)
- Cutout from transforms is not working properly but having issues even with Albumentations library
  - Using RandomErasing - The size of the cutout is not in proportion mentioned in the scale
  - Also not able to find the equivalent way to get the right cutout
