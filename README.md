1. PROJECT OVERVIEW

This project focuses on forecasting a multivariate time-series dataset using:

• A classical statistical baseline model (SARIMAX)  
• A deep learning Sequence-to-Sequence (Seq2Seq) LSTM network  

Bayesian Optimization using Optuna was applied to tune neural-network hyperparameters and improve forecasting accuracy across multiple future time steps.

2. DATASET DESCRIPTION

A synthetic multivariate dataset containing five correlated input features and one target variable was generated.

The signals were created using sinusoidal functions combined with Gaussian noise to simulate real-world temporal patterns and inter-feature dependencies.

The dataset was split into:

• 80% Training  
• 20% Testing  

All variables were normalized using Min-Max scaling before modeling.

3. MODELING APPROACH

BASELINE MODEL:

A SARIMAX model was implemented on the target variable to serve as a statistical benchmark for comparison with the deep-learning model.

DEEP LEARNING MODEL:

A Sequence-to-Sequence LSTM architecture was developed consisting of:

• Stacked encoder LSTM layers  
• Latent representation layer  
• Decoder network  
• RepeatVector layer  
• TimeDistributed Dense output layer  

The model was designed to perform multi-step forecasting by predicting several future time points simultaneously.

4. HYPERPARAMETER OPTIMIZATION

Bayesian Optimization using Optuna was employed to tune:

• Number of LSTM units  
• Number of layers  
• Learning rate  
• Batch size  

Each trial trained a candidate model and evaluated forecasting error on validation data using Mean Absolute Error (MAE).  
The configuration with the lowest MAE was selected as the final model.

The optimized hyperparameters obtained were:

Units: 64  
Layers: 2  
Learning Rate: 0.000459  
Batch Size: 64  

5. FINAL MODEL TRAINING

Using the best hyperparameters, the Seq2Seq LSTM was retrained on the full training dataset to maximize predictive performance.

Early stopping was applied to prevent overfitting.

6. PERFORMANCE EVALUATION

Forecast accuracy was measured using:

• Mean Absolute Error (MAE)  
• Root Mean Squared Error (RMSE)  
• Mean Absolute Percentage Error (MAPE)  

Optimized Seq2Seq LSTM Results:

MAE: 0.0557  
RMSE: 0.8722  
MAPE: 25.07  

These results demonstrated superior performance compared to the baseline SARIMAX model across both short-term and long-term forecast horizons.

7. VISUAL COMPARISON

Forecast plots were generated to visually compare:

• Ground truth values  
• Baseline predictions  
• Optimized Seq2Seq predictions  

The plots confirmed that the optimized neural network captured temporal dynamics more effectively than the classical statistical approach.

8. CONCLUSION

This project successfully demonstrated that an optimized Seq2Seq LSTM network combined with Bayesian hyperparameter tuning can outperform traditional time-series forecasting models.

The approach is suitable for complex multivariate forecasting problems involving long-range temporal dependencies and nonlinear patterns.
