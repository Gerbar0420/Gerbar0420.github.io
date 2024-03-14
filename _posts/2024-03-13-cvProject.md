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

#### Generalized Additive Models

![](/images/ "UNet structure")

- **Flexibility**

    GAMs allow for non-linear relationships between predictors and response variables. They can capture complex patterns in the data without the need for specifying explicit functional forms, making them highly flexible for modeling a wide range of relationships.

- **Interpretability**

    Despite their flexibility, GAMs often maintain interpretability. By allowing for smooth functions of predictors, GAMs provide interpretable results, enabling researchers to understand the effect of each predictor on the response variable while considering potential non-linearities.

- **Automatic Variable Selection**

    GAMs can perform automatic variable selection during the modeling process. Through techniques such as penalized regression or stepwise selection, GAMs can identify the most relevant predictors while excluding irrelevant ones, thereby simplifying the model and improving its interpretability. This feature helps prevent overfitting and enhances the model's predictive accuracy.


#### Challenge encountered

- The selection of the link function for proportional data.

  

- The selection and meaning of parameters of basis number for splines functions

  
  
- The benefit of Double Penalty Approach

   

- The meaning of edf value and its choosing criteria  

  

- Concurvity issue in GAM

  
  

- The criterion for model diagnostic   

  
