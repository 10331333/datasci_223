# Exercise 4/5 - emnist classification models exercise
**Instructions**
1. Download [exercise4.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4.ipynb) and [exercise4-5.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4-5.ipynb).
2. Open exercise.ipynb and clear outputs. (There should not be any, but do this if necessary.)
3. Create a fresh virtual environment by running the first code box to download the required packages. Python 3.11.2 was used. 
4. Run the rest of the code. 

---
# Notes

## Task 1: Classify all symbols (Classification model for all letters was already done after week 4)
This exercise is in [exercise4.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4.ipynb). 
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

## Task 2 Option 1: Classify digits vs. letters model showdown
This exercise is in [exercise4.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4.ipynb). 
### Select candidate models, hyperparameter options, and evaluation metric
All specified in matrix dictionary `candidate_metrics_dict`. 

### Results of models trained over K splits (use k-fold or train/test split)
|       | logistic_regression | xgboost | random_forest | neural_network | 
| ----- | ----- | ----- | ----- |  ----- | 
| accuracy | 0.848063 | 0.902446 | 0.894742 | 0.832673 | 
| precision | 0.864072 | 0.917008 | 0.897381 | 0.881869 |
| recall | 0.971859 | 0.971712 | 0.987519 | 0.925235 | 
| f1 | 0.914797 | 0.943565 | 0.940290 | 0.902590 | 

Promote `random_forest` as the final model (highest recall) and apply to the entire dataset. 

### Performance matrix of final model 
| accuracy | precision | recall | f1 | 
| ----- | ----- | ----- | ----- | 
| 0.899107 | 0.902084 | 0.986601 | 0.942451 | 

## Task 2 Option 2: Model showdown: upper vs lowercase on abcXYZ
This exercise is in [exercise4-5.ipynb](https://github.com/10331333/datasci_223/blob/homework/exercises/4-classification/exercise4-5.ipynb).

