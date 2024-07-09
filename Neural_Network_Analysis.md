# Neural Network Model Analysis Report

## Overview
The purpose of the Neural Network Model is to use existing available data from prior initiatives that Alphabet Soup Foundation funded to determine the likelihood of new candidate projects being successful. A good model will allow Alphabet Soup Foundation to effectively allocate available funds to the candidates most likely to succeed.

## Results

### Data Preprocessing
The data file was first split into the following feature columns:
- APPLICATION_TYPE
- AFFILIATION
- CLASSIFICATION
- USE_CASE
- ORGANIZATION
- STATUS
- INCOME_AMT
- SPECIAL_CONSIDERATIONS
- ASK_AMT

A single column was used for training as the target:
- IS_SUCCESSFUL

There were two additional columns that acted as record identifiers rather than either feature or target, and were therefore dropped from the data frame:
- EIN
- NAME

In order to avoid overfitting and allowing rare outliers to significantly impact the results, unusual values in certain categorical columns were combined into an "Other" value in order to minimize the chances of their skewing results.

- APPLICATION_TYPE
- CLASSIFICATION

Here is a screenshot of the resulting valid Application Types:

![Application Type](images/nn_Application_Type.png?raw=true)

And here is a screenshot of the resulting valid Classifications:

![Classifications](images/nn_Classification.png?raw=true)

This left the following Pandas data frame:

![Data Frame](images/nn_Dataframe.png?raw=true)

Once the above tasks had been performed, `pd.get_dummies` was used to split out categorical columns. The dataset was then split between the y (target) values and the X (feature) columns. These pre-processed data were then split into test and train data using `train_test_split`. In order to allow duplication of results by additional testers, a random_state of 42 was used.

The data were then scaled using `StandardScaler` in order to avoid artificial weighting of columns with large ranges.

### Compiling, Training, and Evaluating the Model

Two hidden layers and one output layer were used for the neural network. In an effort to optimize results, the model was also run using three and four hidden layers, but results were not any better than with two, so in an effort to reduce system resource usage, just two hidden layers were required for the final model.

A total of 80 neurons were used in the first input layer, and 40 neurons in the second. Both higher and lower counts were tried in an effort to meet the target ranging from 30/20 to 120/60.

For the output layer, a single neuron was used since this is generally effective on datasets that will result in a single, binary classification. 

Several different activation functions were tried including RELU, Sigmoid, TANH, and Softmax. The best results were with Softmax for the two hidden layers, and Sigmoid for the single output layer. 

The target accuracy identified for the model was 75%. That level of accuracy was not achieved despite multiple efforts to optimize the model. The best result was approximately 73.3% accuracy. In an effort to reach 75%, the following adjustments were tried:

- Removal of the `Status` column since it was overwhelmingly populated with a single value
- Removal of the `Special_Considerations` column which was likewise dominated by a single value
- Modifications to the threshold for `Classification` and `Application_Type` to see if outliers were affecting accuracy of the model
- Addition of more hidden layers
- Adjustments to the number of neurons in each layer
- Modifications to the activation method

## Summary

An improvement of approximately 1.5% was reached vs. the baseline result prior to optimization. At 73.3%, the optimized result still fell short of the target of 75%. 

It is possible that additional manipulation of parameters would reach the target, but I did not see a clear path to achieving the goal. In order to achieve a better result I would recommend one or more of the following:

- Incorporate additional data, either additional features or results from outside Alphabet Soup
- Perform additional data cleansing on the existing data to see if there are outlier initiatives that should be removed from the training dataset. 


