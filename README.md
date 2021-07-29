# UCB-Neural_Network_ML-A19

Appying neural network for Charity Organisation Analysis 

### Overview 

- **Aim** : Creating a binary classifier with neural network to predict whether applicants to a charity, Alphabet Soup, will be successful with their funding request. 

- **Dataset** : csv file with over 34,000 organisations who received funding from Alphabet Soup. Columns of the dataset:
      - EIN and Name : Identification 
      - APPLICATION_TYPE : Alphabet Soup application type 
      - AFFILIATION : Affiliated sector of industry
      - CLASSIFICATION : Government organisation classification 
      - USE_CASE : Use case for funding 
      - ORGANISATION : Organisation type 
      - STATUS : Active status 
      - INCOME_AMT : Income classification 
      - SPECIAL_CONSIDERATIONS : Special consideration for application 
      - ASK_AMT : Amount of Funding requested 
      - IS_SUCCESSFUL : Was the monet used effectively 

- **Goal** : To build a model that achieve over 75% accuracy rate in predicting the success for funding application from the given data.

## Results 
## Preparation (Pre-processing)

1. To examine and pre-process the dataset: 
      - Target variable : ["IS_SUCCESSFUL"].
      - Unwanted data : ["EIN"], ["NAME"].
      - All other columns were potientially featured for the model. 
2. To bin, encode and scale the data 
      - Bin ["APPLICATION_TYPE"] < 1000 entries to ["OTHER"].
      - Bin ["CLASSIFICATION"] < 1000 entries to ["OTHER"].
      - ALL "object" type columns are encoded using OneHotEncoder.
      - The ["SPECIAL_CONSIDERATIONS_N"] column was dropped, as it was redundant to the ["SPECIAL_CONSIDERATIONS_Y"] column.
      - All columns were then scaled using StandardScaler.

## Compiling, Training, and Evaluating

- Initial Model: 
      - 2 layers 
            - 1st with 80 neurons 
            - 2nd with 45 neurons 
                  - Gives 6,891 total and trainable parameters 
                  - Applied "relu" activation function for both layers
                  - Applied "sigmoid" activaiton function for the output layer 
      - Accuracy : 72.6%

- Additional 3 Optimisation Models: 
      - Binned ["INCOME_AMT"] > $5M into a "5M+" bin.
      - Added a 3rd hidden layer.
      - Increased the total number of training parameters to 9,411. 
      - Increased training epochs from 100 to 150, then to 300. 
      - Applied both "adamax" and "nadam" optimisers when compiling the model.
      - Used "tanh" activation functions on the hidden layers. 
      - unbinning certain values by lowering the threshold to 700 for both ["APPLICATION_TYPE"] and ["CLASSIFICATION"]
      - Accuracy : ~73% 

## Summary

- Increasing the parameters for taining or training epochs do not have a huge effect on the accuracy. 

- Other methods need to be implemented to obtain a higher accuracy for model prediction. 


