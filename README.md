# Assessing Potential Ink Disease Distribution in Sweet Chestnut Forests in Switzerland. A Remote Sensing Approach - Main Script

This repository contains the code used in my Master's thesis to develop a Random Forest (RF) classification model for assessing potential diseased sweet chestnut trees by using freely availabe Sentinel-2 data and sampled tree data. The model includes Recursive Feature Elimination (RFE) and Leave-Location-Out Cross-Validation (LOO CV) for feature selection and model validation.

## Key Tasks
The primary objective of this script is to find the best performing RF model that classifies pixels of sweet chestnut canopies as either "symptomatic" or " non-symptomatic". Potential input features include monthly calculated median values of DN values of 8 spectral bands, as well as ratio values from 8 vegetation indices. The script performs the following key tasks:

 - Leave-Location-Out Cross-Validation (LLO CV): Instead of using random splits for model validation, LLO CV is used to take into account the spatial dependencies of the input data. 9 spatial folds were defined based on visual assessment of the data's spatial distribution. From each fold, 10 samples were held out from the model training for independent model testing at the end of the script. The scoring metrics used include the final model accuracy, and class-wise precision, recall, and F1-score.

 - Feature Selection: To optimise the classifier's performance, an initial assessment of the number and combination of features has been conducted. After pre-selecting the 32 most important features using RFE, the performance of the RF model with different numbers [6, ..., 23] and combinations of features as an input was evaluated. The feature combination that achieved the highest mean accuracy over 10 iterations was selected for training the final RF model.

- Feature Evaluation: An approach was implemented to train and validate the RF classifier with different numbers and combinations of features. This allowed for an overall assessment of model performance with respect to the given combinations of input features. The evaluation includes the number of features, mean accuracies, specific importance values of the selected features, and accuracy results of all the 10 iterations per feature combination. This provided a detailed insight into the behavior of the model under different feature input conditions.

- Random Forest (RF) model training: With the final selection of input features, the RF classifier was trained and could be used for further model classification.
   
## Libraries
The following libraries are required to run the script:

    random
    pandas
    numpy
    collections
    scikit-learn

Version 1.0.0

Date Created: 2025-01

Copyright (c) Lisa Zumbrunn, 2025

The code has been developed with the help of ChatGPT (version GPT-4) While ChatGPT provided support in writing, all the methodological setup, modifications, and final code were independently completed by the author.
