 # Project Report
 ## Sleep and Readiness Score Predictor based on Menstrual Cycle Phase


Goal: Predict readiness/sleep score based on menstrual cycle phase and temperature to recommend to users in advance for planning rest and recovery.


1. Introduction: 
The menstrual cycle has been known to influence various physiological parameters in women. This project aims to predict readiness and sleep scores based on menstrual cycle phases and daily temperature. The ultimate goal is to provide recommendations for rest and recovery.


2. Data Description: 

Source of Data: 
  - Oura: readiness score, days
  - Natural cycles: cycle phase, days, temperature

Data Characteristics: 
  - 1 Participant | Female | Age: 29
  - 6 cycles (5 for training and 1 for testing)
  - Daily temperature
  - Daily readiness score
  - Daily sleep score


3. Cycle Phase Setup:

   Option 1:  
  - Phase 1: Menstruation 
  - Phase 2: Follicular includes Ovulation.
  - Phase 4: Luteal

    Option 2: 
  - Phase 1: Before Ovulation (includes menstruation, follicular, and ovulation)
  - Phase 4: After Ovulation (includes Luteal)

Based on T-test and ANOVA, Option 2 was found to be more statistically significant in terms of difference in readiness score between phases on 10% significance level.



4. Model Development:

A. Predicting Readiness Score:

- Model Options:
  1. Predict readiness score based on phase | grouped by cycle.
  2. Predict readiness score based on phase and temperature | grouped by cycle.
  3. Predict readiness score based on phase and phase interaction with temperature | grouped by cycle.

- Results:

  -  Model 1:
    model = smf.mixedlm("readiness_score ~ C(phase)", train_df, groups=train_df["cycle"])
     - Training MSE: 65.43272790019607
     - Test MSE: 49.33961461512729
     - Training MAE: 6.261412516146517
     - Test MAE: 5.796216094528584
     - Predicted values: 81 or 79

-	 Model 2:
    model = smf.mixedlm("readiness_score ~ C(phase)+ temperature", train_df, groups=train_df["cycle"])
     - Training MSE: 65.37251954838683
     - Test MSE: 46.06317656979369
     - Training MAE: 6.2202353067451375
     - Test MAE: 5.68446437452865
     - Predicted values: 80,81,82,78,79

-	Model 3: 
    model = smf.mixedlm("readiness_score ~ C(phase)* temperature", train_df, groups=train_df["cycle"])
     - Training MSE: 65.25590638793966
     - Test MSE: 45.53496246470211
     - Training MAE: 6.170838590119566
     - Test MAE: 5.609822055959534
     - Predicted values: 81,80,77,78,79








B. Predicting Sleep Score:

- Model Options:
  1. Predict sleep score based on phase | group by cycle.
  2. Predict sleep score based on phase and temperature | group by cycle.
  3. Predict sleep score based on phase and phase interaction with temperature | group by cycle.

- Results:

  - Model 1:
     model = smf.mixedlm("sleep_score ~ C(phase)", train_df, groups=train_df["cycle"])
     - Training MSE: 45.9586850231212
     - Test MSE: 62.69084977411039
     - Training MAE: 5.343464891516985
     - Test MAE: 6.451636255451236
     - Predicted values: 84 or 83

  - Model 2:
 model = smf.mixedlm("sleep_score ~ C(phase)+ temperature", train_df, groups=train_df["cycle"])
     - Training MSE: 45.42095895539741
     - Test MSE: 63.20277011595535
     - Training MAE: 5.313008015657408
     - Test MAE: 6.480161422759279
     - Predicted values: 82,83,84,85

  - Model 3:
    model = smf.mixedlm("sleep_score ~ C(phase)* temperature", train_df,  groups=train_df["cycle"])
     - Training MSE: 45.358913913207154
     - Test MSE: 63.67583179056497
     - Training MAE: 5.313258298520249
     - Test MAE: 6.501708002043001











5. Code Files and Steps: 

1. File: Extract_Data 
   - Extract Data.
2. File: Interpolate _Data 
   - Interpolate missing scores and temperatures.
3. File:  Visualize_Data
   - Plot scores vs. phase & cycle. 
4. File: ttest_Data 
   - Apply t-test and ANOVA to see if there is a difference in scores across phases.
5. File: TrainTest_Model
   - Train and test.


6. Analysis:

- For predicting readiness score, Model 3 ("readiness_score ~ C(phase)*temperature") was the most accurate.

- For predicting sleep score, Model 1 ("sleep_score ~ C(phase)") was the most accurate for the test data, but Model 3 might be overfitting the training data.


7. Discussion:

The results indicate that the menstrual cycle phase and temperature can be used to predict readiness and sleep scores. This can be beneficial for individuals to plan their activities and rest periods. The models developed can be further refined with more data and additional features.


8. Next Steps:

- Expand the Dataset: Collect data from more individuals to create a more robust model.

-   Feature Engineering: Explore other physiological parameters that might influence readiness and sleep scores. Or Explore tag features provided in both Natural cycles and Oura.

-Feedback Loop: Allow users to provide feedback on the accuracy of predictions to continuously improve the model.


