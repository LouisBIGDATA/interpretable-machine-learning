# Interpretable-machine-learning
Many people say machine learning models are 'black boxes', in the sense that they can make good predictions but you can't understand the logic behind those predictions. However, data scientists need to try their best to explain machine learning results, and tell a good story about them. Here are three different ways to explain a Machine Learning model, they are
- Permutation importance
- Partial dependence plots
- SHAP values

## Permutation importance
Usually a machine learning model involves many input variables. A natural question we might ask of a model is what features have the biggest impact on the final predictions?<br>
This concept is called feature importance. Training a model that accurately predicts outcomes it great, but most time you don't just need predictions, you want to be able to interpret your model. Feature importance is the most useful interpretation tool, and data scientists regularly examine model parameters ( such as the coefficients of linear models), to identify important features.<br>
Permutation importance is a common, reasonably efficient, and very reliable technique. It directly measures variable importance by observing the effect on model accuracy of randomly shuffling each predictor variable. This technique is broadly applicable because it doesn't rely on internal model parameters, such as linear regression coeffcients(which are really just poor proxies for feature importance).<>br>
### problems in random forest feature importance
The most common mechanism to compute feature importances and the one used in scikit-learn RandomForestClassifier and RandomForestRegressor, is the mean decrease impurity or gini importance mechanism. . The mean decrease in impurity importance of a feature is computed by measuring how effective the feature is at reducing uncertainty (classifiers) or variance (regressors) when creating decision trees within RFs. The problem is that this mechanism, while fast, does not always give an accurate picture of importance. 
### How to to permutation importance
Record a baseline accuracy (classifier) or R2 score (regressor) by passing a validation set or the out-of-bag (OOB) samples through the Random Forest. Permute the column values of a single predictor feature and then pass all test samples back through the Random Forest and recompute the accuracy or R2. The importance of that feature is the difference between the baseline and the drop in overall accuracy or R2 caused by permuting the column. The permutation mechanism is much more computationally expensive than the mean decrease in impurity mechanism, but the results are more reliable. The permutation importance strategy does not require retraining the model after permuting each column; we just have to re-run the perturbed test samples through the already-trained model.
## Partial Dependence Plots
While feature importance shows what variables most affect predictions, partial dependence plots show how a feature affects predictions - relationship is positive or negative.

## SHAP value
We can use permutation importance and dependence plots to extract general insights from a Machine Learning model. But what if we want to break down how the model works for an individual prediction?<br>

SHAP value (SHapley Additive exPlanations) break down a prediction to show the impact of each feature. SHAP values interpret the impact of having a certain value for a given feature in comparison to the prediction we’d make if that feature took some baseline value.
