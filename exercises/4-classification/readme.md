# Exercise 4/5 - emnist classification models exercise
**Instructions**
1. Download [exercise4.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise.ipynb) and [exercise4-5.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4-5.ipynb).
2. Open exercise.ipynb and clear outputs. (There should not be any, but do this if necessary.)
3. Create a fresh virtual environment by running the first code box to download the required packages. Python 3.11.2 was used. 
4. Run the rest of the code. 

---
# Notes

## Task 1: Classify all symbols (Classification model for all letters was already done after week 4)
This exercise is in [exercise4.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise.ipynb). 
### - Model Choice
Classification will be done using neural network because handwritten letters can have complex patterns that can be better analyzed by neural networks. 

### - Model training
Parameter tuning: No parameter tuning was done with the model. 
Formatting input data: Image data needs to be converted into tensors. The images arrays are later flattened in the model.  

### - Evaluate the model
Model evaluation on test set: 
| accuracy | precision | recall | f1 | 
| -------- | --------- | ------ | ----- | 
| 0.717115 | 0.699434 | 0.717115 | 0.697316 | 

### - Investigate subsets  
Classes that the model performs well/poorly:  `['1', 'l', 'I', 'i']` , `['o', 'O', 'O']`, `['Z', 'z', '2']`
Results show that all evaluation matrices increased by only including those that are easy to classify. 
| accuracy | precision | recall | f1 | 
| -------- | --------- | ------ | ----- | 
| 0.741899 | 0.747542 | 0.741899 | 0.737913 | 

### - Improve performance
Since we know that there are sets of symbols that are commonly confused, we can use ensemble methods with a few model that specializes in differentiating between commonly misclassified symbols sets, and another overall model that handles the rest of the classification task. The final prediction could be a combination of the predictions from both models.

## Task 2: Model showdown: upper vs lowercase on abcXYZ
### Train and tune models

Perform a full model training and hyperparameter tuning.

1. Select candidate models, hyperparameter options, and evaluation metric
2. Set aside a validation hold-out dataset
3. Train models over K splits (use k-fold or train/test split)
    1. Split train using k-fold with the number of folds equal to the number of parameter combinations
    2. Train on k-fold split
    3. Record performance of each set of parameters
    4. Use winning set of parameters to train model on full training set
    5. Record each model's performance on that split's test set
4. Evaluate model performance and promote one model as the winner
5. Train winning model on both train + test
6. Check model performance on the validation hold-out


## Task 3: (_Optional_) Model comparison: classify even vs odd

**NOTE:** This is a larger dataset (~400k rows) so it will require more memory and time to train models on it. 

Alternatively, you can train models on smaller subsets of the data to get a feel for which models perform better than others. Then train the winning model on the full dataset and validate against the hold-out.

### Subset the data

Select only digits and add a column for 'is_even'. Be sure to create a validation hold-out dataset for later.

### Build and compare models

Train at least two different models, compare the results and choose a winner based on an evaluation metric of your choice.
