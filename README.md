Business Case: Built a model using SVM algorithm to predict whether to approve a loan or not based on the given features.

Model Use: SVM
(SVM is the Supervised Machine Learning algorithm used for both classification, regression. But mostly preferred for classification)
Steps for Preprocessing:
1. First use basic checking of the dataset.
2. Used y_data profiling for auto EDA
3. In pre-processing techniques, used Scaling and Encoding techniques to transform the feature columns into certain range as required.
4.  Used FunctionTrasformer to use our own custom function for transformation so we will use this custom function when we are defining the pipeline.

### Steps of preprocesing for features:
- LabelEncoder for Married,Credit_histroy
- OrdinalEncoder for Dependents,Education
- One hot encoder for Self Employed,Property_area,Gender
- FucntionTransformer for Loan_Amount_term
- Standard scaler for Applicant Income , CoapplicantIncome and LoanAmount
- Credit histroy will pass through
### Steps of preprocessing for Label
- LabelEncoder for Loan_Status (Approved)

After all the transformation, I pushed it in Column Transformer function and stored it in a variable called preprocessor. Lastly, saving the model in Pickle file for later use.

Steps for SVM Implimentation:
1. Import all the required libraries and modules.
2.  Then imputing the null values with mean/median/mode where it applied as required.
3. After that we load the Preprocessing Pipeline Pikle file to use in the model.
4. Next, Splitted the data into train and test.
5. Then, transforming the feature & target column data using the preprocessor
6. In order to model performs well, the target column data needs to banlanced. For that, used SMOTE technique to the training data to balance the class distribution.


Model Building Steps:

1. Import Support vector classifier from Sklearn.
2.  Fit the SVC to the resampled training data

Validating the model:
1.  Transform the test data using the preprocessor.
2.  Splitted the testing data into x_test, y_test.
3.  Getting predictions from model

Evaluating the model performance:
1. Importing the classification_report function from sklearn.metrics
2.  Printing the classification report comparing the true labels (y_test) and the predicted labels (y_pred)

Hyper Parameter Tuning: 
(To improve the Accuracy score, we use Hyper Parameter Tuning)
Steps:
1. Importing GridSearchCV from sklearn
2. Assigning SVC model into variables
# Defining the grid search using GridSearchCV
 - The parameter grid is defined by param_grid_poly | here in our model we go with param_grid_linear
 - 'refit=True' ensures that the best estimator found during the grid search is refitted on the whole dataset
 - 'verbose=2' controls the verbosity of the grid search process (higher values result in more output) | level of detail, usually 0,1,2 means detail level
 - 'scoring='f1'' specifies the scoring metric for evaluating the model's performance during grid search
 - 'cv=5' specifies 5-fold cross-validation for evaluating each combination of hyperparameters
3.  fitting the model for grid search
After that, Opening a file named "model.pkl" in write-binary mode
4.  Use the best model from grid search to make predictions on the test set

Conclusion
As we can see that the performance of model has increased significatly from Accuracy score 72% to 80%.
