# Predictive-Analysis-of-High-Dimensional-Data
Exploration of different dimensionality reduction techniques.
We receive the data for the supervised learning and there are 400 examples of the data. The
number of variables is 500. We can say that the dimensionality of this data is very high and in
fact the number of variables is larger than the number of data points (Case of p>n). This make
the direct use of learning techniques like Logistic Regression on this data impossible. 
Also, k-nearest neighbor is also not feasible because it performs poorly for high dimensional data. For
such a high dimensional data, we must eventually try to implement dimensionality reduction.
Also, we check the proportion of 0 and 1 in order to check whether it is rare event
phenomenon and find that the data is balanced.
We check for any missing values in the data and find that there are no missing values. Then we
test some statistical properties of the data, including, average, maximum, minimum and
standard deviation. We see that all these are within normal value and there are no real
“outliers” in the data.
We next try to ascertain whether there exists any correlation between the variables. Initially we
use correlation matrix to do so. However, we find that finding and mapping correlation in a 500
by 500 dataset is not an efficient process. We apply PCA to explain 95% variance and get 258
variables. This may suggest that a lot of the variables are correlated with each other.
We initially try to model the raw data with techniques like Neural Network, Random Forest etc but get very
poor Cross validation accuracy. We then scale the dataset and obtain the 95% PCA value. We
employ methods like Decision Trees, Neural Networks, XGBoost(Extreme Gradient Boosting, a Gradient Boosted Tree method), 
Random Forest on the PCA Data. 
We find that the Cross-validation accuracy has not improved much compared to
using without PCA (about 50% CV error). Since PCA did not give us good results, we suspect the
relationship among the data is probably non-linear. We try out other techniques. With kernel PCA, 
During XGBoost hyperparameter tuning, we discover that we are getting better results with
“dart” booster which utilizes a tree-based model compared to “gbtree” which utilizes a linear
function. Also, we get good results when we max out the “depth” of the splitting to which the
model can go. This shows that the data is highly non-linear and complex and not a “linear
function”. However, since it is boosted algorithm, we can be sure that we are not overfitting
the data. We get a CV error rate of 0.20 with the best algorithm which is a great improvement
from the initial results.
