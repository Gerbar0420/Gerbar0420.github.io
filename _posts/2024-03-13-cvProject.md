# Academia Sinica - The Impact of Different Pollution Sources on Lower Respiratory Diseases(STILL UPDATING)

## Introduction

The research aims to target specific sources of pollution to reduce their emissions, thereby improving air quality and lowering the incidence of diseases. The following analysis will focus on the **Douliu area**. The results indicate that two sources of pollution, namely sea salt spray and industrial processes, were selected from the eight sources of pollution, along with other types of variables. This selection yields an 84% explainability of the P1 value. Additionally, the results show that increasing a unit of sea salt spray results in a 0.62 unit increase in the P1 value, holding other variables unchanged, while increasing a unit of industrial processes results in a 0.04 unit decrease in the P1 value, holding other variables unchanged.

- **Input**

  Data provided by the Academia Sinica, the time series plot of **responding variable P1** is defined as the percentage of patients with lower respiratory diseases among the total number of patients seeking medical attention. P1 time series is shown in Figure 1. Also, **Eight Major Pollution Sources**, **Time Variables** and **Air Condition Variables**  totally 63 predictors can be used.

   ![](/images/douliuP1.png "Figure 1")

- **Output**

  
  Through the variable selection process, eight predictors were selected from a pool of 63 variables. Taking Douliu as an example, **Sea salt spray** and **Industrial processes** were identified as important Pollution Sources variables for interpretating P1 value.
   

- **Performance**

  After fitting a generalized additive model to select important variables, the R-squared of the test dataset reach **0.84**. Moreover, it also exhibited considerable performance in prediction, as detailed in Figure 3.

   ![](/images/AS_output.png "Figure 3")

## Analysis Step

1. Variable discussion

   1.1. P1 - potential problem

     該變數為就診且為下呼吸道疾病病患之人數除以總就診人數，具明顯的假日效應，也就是假日的P1值會較平日高
   
   1.2. Eight Major Pollution Sources

     The time series plot of Douliu area's three important pollution sources are shown in Figure 2.

     ![](/images/final33.png "Figure 2")
     
   
   1.3. Time Variable - Time really matters

     透過將P1變數隨著時間作圖，可得知P1具有週期性，本例中之週期約莫為一週，因此就該觀測值是否為**假日**新增一變數，後來發現該變數非常重要

   1.4. Chemical Element Variable - preliminary dependence analysis

     化學元素的資訊在本次研究中未被採用，但我認為未來可採納的統計方法有
     
       1.將34個化學元素採取PCA維度縮減方式，萃取出2個主要成分。
       2.由步驟1所萃取出的2個主要成分利用copula模型做待有時間資訊的變數相關性研究。

     由上述兩步驟，即可透過具有解釋性的統計方法，將34維度的變數量，縮減為2個具代表性的變數量

   1.5. Air Condition Variable -

     
   
3. Model Exploration
   
   2.1. Generalized Additive Models(GAM) - Model advantage
   
   2.2. Variable Selection - Double penalty approach, Marra and Wood (2011)
   
   2.3. Concurvity - variable dependence
   
   2.4. Model diagnostic - different from the linear assumption diagnostic


## Technical Challenge

### Model Building

#### Generalized Additive Models

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

  
