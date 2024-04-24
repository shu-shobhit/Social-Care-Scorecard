# Social-Care-Scorecard

## Background
Social determinants of health (SDOH), such as where we live, income, education, race, age,
and support systems have a profound impact on our health and well-being. These factors
contribute to health disparities and are strong predictors of both individual and community-level
health outcomes. Understanding an individual's SDOH is crucial, especially when providing care
for those with disabilities, chronic conditions, or when supporting aging loved ones. However,
obtaining a comprehensive picture of someone's social circumstances can be challenging.
Current approaches often rely on surveys or self-reporting, which have limitations and can be
time-consuming.

## Objectives
1. The Heart of the Challenge - The Social Care Scorecard: Imagine a tool that uses
data to paint a picture of an individual's social support needs and potential health risks.
a. Predictive model for a social scorecard based on limited available information
about an individual and flag needs like transportation, healthy food options, etc.
b. An action-based version of the scorecard to assist PNs, physicians, and other
clinical staff (based on their role) in taking action.

## Methodology
#### Approach - 1
1. **Data Segmentation:** Partitioned the dataset according to the 10 pre-defined Social Determinants of Health to
  facilitate focused analysis.
2. **Clustering Analysis:** Executed clustering within each determinant category using K-Means, identifying natural
 groupings within the data.
3. **Risk Labeling:** Assigned risk labels ('high', 'medium', 'low') based on the characteristics of each cluster's
 centroid.
4. **Risk Scoring:** Calculated inverse linear distance scores for each data point relative to cluster centroids to
 quantify risk levels.
5. **Optimal Clusters Determination:** Applied the elbow method to determine the appropriate number of centroids
for the K-Means algorithm.
6. **Clustering Validation:** Validated the K-Means clustering with several metrics, including the Silhouette Score,
  Davies-Bouldin Index, and Calinski-Harabasz Index, to ensure the robustness and relevance of the clusters
  formed.

**_More details are in the report_**

#### Approach - 2
1. Utilized a suite of machine learning models, including Linear Regression, Lasso Regression, Elastic Net,
Decision Tree, Random Forest, Gradient Boosting, SVR, and KNR, to analyze the relationship between
SDOH census tract data and outcomes such as life expectancy and health status.
2. Validated the models against a range of metrics: RMSE, MAPE, MSE, R² score, and Mean Absolute Error.
Linear Regression and XGBoost emerged as the top performers.
3. Determined variable significance through permutation importance, aiming to distill the variables' aggregated
impact on the training dataset, inclusive of all census tracts.
4. To tailor the risk scores to individual census tracts, normalized the feature importance and multiplied by the
variable values, subsequently summing these products to derive category-specific risk scores.

Implemented two methods for calculating risk scores:
1. Direct multiplication of risk scores with variable values.
2. Multiplication of normalized feature importance with variable values. This process was replicated for both the XGBoost and MLR models to ensure robustness.
3. Normalized the final risk scores to a 0-1 scale, providing a standardized metric for assessing and comparing the
impact of SDOH on health outcomes and life expectancy across different census tracts.
