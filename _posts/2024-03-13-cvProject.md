# Data Analysis Project in C.V.(STILL UPDATING)

## Academia Sinica - The Impact of Different Pollution Sources on Lower Respiratory Diseases

## Introduction

The research aims to target specific sources of pollution to reduce their emissions, thereby improving air quality and lowering the incidence of diseases. The following analysis will focus on Douliu area, and the result shows that two pollution sources **Sea salt spray** and **Industrial processes** along with other six variables will have 84% explainability of P1 value. The result also shows that increasing a unit of **Sea salt spray** turns to an 0.62 unit increasing in P1 value holding other variables unchanged while increasing a unit of **Industrial processes** turns to an 0.04 unit decreasing in P1 value holding other variables unchanged.

- **Input**

  Data provided by the Academia Sinica, the box plot of **responding variable P1** is defined as the percentage of patients with lower respiratory diseases among the total number of patients seeking medical attention. P1 values from the six areas are shown in Figure 1.

   ![](/images/AS_EDA.png "Figure 1")


  The percentage of **eight major pollution sources** as shown in Figure 2.

  ![](/images/AS_EDA2.png "Figure 2")

- **Output**

  
  Through the variable selection process, eight explanatory variables were selected from a pool of 63 variables. Taking Douliu as an example, Sea salt spray and Industrial processes were identified as important explanatory variables for interpretating P1 value among the eight major pollution sources in that area.
   

- **Performance**

  By fitting a generalized additive model to selecting important variables, the R-squared of the test dataset reach **0.84**. Moreover, it also exhibited considerable performance in prediction, as detailed in Figure 3.

   ![](/images/AS_output.png "Figure 3")

## Analysis Step

1. Variable discussion

   1.1. P1 - The potential problem
   
   1.2. Eight Major Pollution Sources - 
   
   1.3. Time Variable - Time really matters

   1.4. Chemical Element Variable - preliminary dependence analysis 

   1.5. Air Condition Variable - 
   
2. Model Exploration
   
   2.1. Generalized Additive Models(GAM) - Model advantage
   
   2.2. Variable Selection - Double penalty approach, Marra and Wood (2011)
   
   2.3. Concurvity - variable dependence
   
   2.4. Model diagnostic - different from the linear assumption diagnostic


## Technical Challenge

### Data Preprocessing
- 

  

### Model Building

#### UNet

![](/images/ "UNet structure")

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

## Institute for Information Industry - PERFECT corp user's APP behavior history data analysis 

## National Chengchi University Data Science Course - Predicting Loyalty Scores

## Securities & Futures Institute - Taiwan Bioindustry Analysis

## Shopee - Shopee Ultimate Case Challenge 2021

## National Chengchi University Regression Analysis Course - Multiple Regression Analysis of NBA Player Salaries
