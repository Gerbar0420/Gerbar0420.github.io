# Deep Learning in medical image analysis_Semantic Segmentation

## Introduction

This project aims to **assist doctors in making more accurate diagnoses of medical conditions**. Using the deep learning model developed in this project, computers can accurately identify carotid artery areas in ultrasound images of patients, with an accuracy exceeding 95%.

- **Input**

  Images provided by the E-DA Hospital, as shown in Figure 1.

   ![](/images/blood.bmp "Figure 1")


- **Output**

   Before diagnosing, doctors can see the computer-marked carotid artery areas, compare and verify them with their experience, thereby enhancing the quality of healthcare. The image below shows the marked carotid artery areas using the method proposed in this project, as depicted in Figure 2.

   ![](/images/bloodMask.png "Figure 2")

- **Performance**

  I utilized the ResNet18 as encoder part of UNet within the PyTorch framework, achieving an impressive **testing Dice coefficient of 0.96505.** Additionally, my performance ranked among the top three competitors with backgrounds in Statistics and Computer Science.

   [Kaggle Competition](https://www.kaggle.com/competitions/mia-hw4/leaderboard) (Ranking: 3/31, Testing Dice Cofficient: 0.96505)
   ![](/images/rank.png "My Competition Ranking")

## Analysis Step

1. Converting Image-Type Data to Vector-Type Data

   1.1. 精益求精 - Dealing with Background Noise in Images
   
   1.2. 斬草不除根 - How to Remove Background Noise from Images
   
   1.3. 書同文?車同軌? - Conversion to Vectors and Normalization issues
   
2. Model Exploration
   
   2.1. 長江後浪推前浪 - Model Comparison
   
   2.2. 站在巨人肩膀上 - Model Pretraining
   
   2.3. 工欲善其事 - Hyperparameter Selection and Visualization
   
   2.4. 心中一把尺 - Model Evaluation


## Technical Challenge

### Data Preprocessing
- Data augmentation techniques

  Implementing data augmentation techniques may help to enhance out of sample prediction accuracy. But how those augmented data should be incorporated into the data pipeline? Using local or streaming method?

### Model Building

#### UNet

![](/images/UNET.png "UNet structure")

- **Feature extractor**: In segmentation models, feature extractor layers are used throughout the network, allowing it to process spatial information efficiently. These layers capture local patterns and structures in the input data.

- **Skip Connections**: To recover fine-grained details lost during downsampling, Unet uses skip connections. These connections combine feature maps from early layers with those from later layers, aiding in the reconstruction of high-resolution information.

- **Upsampling**: Segmentation models employ upsampling techniques to restore the spatial resolution of the feature maps. Transposed convolutions or bilinear interpolation can be used for this purpose.

#### Challenge encountered

- Last or Best parameter set

  After training each epoch, tens of thousands of estimated model parameters will be logged and the best set among all epochs will be chosen in the condition that smallest validation loss. However, parameter set from last epoch is not necessary to be the best set. So, how to determine whether training with more epochs further or taking the best set in the current training process is the trade-off between prediction accuracy and the time consumption.

- Countless combinations of hyperparameters

  There are infinite combinations of hyperparameters, in my project I mainly focus on trying different combinations of learning rate and weight decay using grid search method. With the help of visualization provided by wandb, it is easier to compare and understand the performance of each combination comprehensively and quickly.
  
- Validation loss remain the same

  I encounter the problem of the not declined validation loss. The predictions are identical, increasing the epochs may not improve the model's performance. Trying the different learning rate using scheduler function help to avoid getting stuck in a local minimum of the loss function. 

- Shape of input tensor 

  I encounter the problem of the not declined validation loss. The predictions are identical, increasing the epochs may not improve the model's performance. Trying the different learning rate using scheduler function help to avoid getting stuck in a local minimum of the loss function.
  
### Evaluation


#### Dice Coefficient

- The Dice Coefficient, also known as the F1 Score, is a measure of the similarity between two sets. In the context of image segmentation, it is used to quantify the agreement between the predicted segmentation and the ground truth.

- The formula for Dice Coefficient is given by:
  
$$ Dice = \frac{2 \times |X \cap Y|}{|X| + |Y|} $$
  
- Dice Coefficient ranges from 0 to 1, where 1 indicates a perfect overlap between the predicted and ground truth segmentations.

#### Intersection over Union (IoU)

- IoU, also known as the Jaccard Index, is another widely used metric for segmentation evaluation. It measures the ratio of the intersection area to the union area between the predicted and ground truth segmentations.

- The formula for IoU is given by:

$$ IoU = \frac{|X \cap Y|}{|X \cup Y|} $$

-  Similar to Dice Coefficient, IoU ranges from 0 to 1, with 1 indicating a perfect overlap.

![](https://www.mathworks.com/help/vision/ref/jaccard.png "Jaccard Index")

#### Interpretation

- **High Values**: A higher Dice Coefficient or IoU indicates better segmentation performance, as it signifies a greater overlap between the predicted and ground truth regions.

- **Low Values**: Lower values suggest poor segmentation accuracy, indicating a mismatch between the predicted and ground truth segmentations.
