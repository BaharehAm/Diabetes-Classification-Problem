# Diabetes-Classification-Problem
This classification problem is a supervised machine learning problem with a binary outcome. 
Four classification methods were trained on the given dataset to predict if an individual is likely to have diabetes or not. 
The classifiers are K-Nearest Neighbors, Logistic Regression, Decision Tree classifier, and Multi Layer Perceptron (MLP).
Based on the target variable distribution, of the 500 data points, 334 are labeled as 0 (not
having diabetes) and 166 as 1 (having diabetes). The dataset is quite unbalanced, and we should take
this into account when we split it into training, validation, and testing sets.

![image](https://user-images.githubusercontent.com/46126394/193379283-11758a3b-e2a0-4353-a731-15eb4bdf5f27.png)

The StandardScaler() function of the “scikit-learn” package was used to normalize the features so
that each feature will have the mean value of μ = 0 and a standard deviance of σ = 1. This was
applied to all numeric features except for features with binary values, i.e., "Social smoker" and
"Social drinker" as their mean and variance do not provide useful information in our analysis. the dataset was split into three parts, namely, training,
validation, and test datasets with the ratios of 50%, 30%, and 20%, respectively. To ensure
that the distribution of target variable in all three subsets is the same as the original dataset, the
stratifying parameter of the train_test_split function was set to the target variable. 
As there is an explicit validation set in this question, the Cross Validation (K-fold CV)
approach of “scikit-learn” package is not applicable here. To address this issue, another package
called “hypopt” was used in this case as it works in both situations of having explicit or implicit
(K-fold CV) validation sets. Creating 100 random values, 100 different validation sets were built. A
function named tune() was written to handle the optimization process and it was called in another
function (evaluate()) where for each random number, the dataset is split into its subsets and the
tune()function finds the best set of hyper-parameters of a given model. Indeed, we trained,
validated and tested each model 100 times and compared the models according to their results on
average. This way, we could overcome the effect of random numbers in our model comparisons. 
The results are shown below:

![image](https://user-images.githubusercontent.com/46126394/193379258-493b9521-cb22-4983-b67e-e4a6f68ddc1c.png)

as it cann be seen from the above figure, both MLP and Logistic Regression classifiers have the
highest average accuracies of around 0.77 on test sets. However, in terms of sensitivity and
specificity, the MLP maintains a better balance between the two metrics (indicated by blue). Overall,
although MLP was slightly better than other classifiers, the performance of all models was
comparable to each other. Based on the results, the average values of sensitivity and specificity of
the MLP classifiers were found to be 0.866 and 0.578, respectively. This means that for each 100
individuals having diabetes, this classifier is able to detect 87 of them correctly and for each 100
individuals who do not have diabetes, this classifier is able to detect 58 of them correctly.
