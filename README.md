# Star Classification Using Machine Learning Techniques

## Abstract

The purpose of this project is to explore machine learning techniques for clustering and classification using the photometric catalog in the optical and infrared region J/ApJ/913/32/sample, titled "Classifications from Gaia & WISE data (Dorn-Wallenstein+, 2021)." This catalog was created with the future goal of facilitating the identification of rare massive stars in infrared observations and employing modern statistical methods to investigate the evolution of massive stellar phenomena in new environments. Given the challenges posed by spectroscopic observations of more distant targets, there is an ambition to assess whether machine learning methods can effectively classify massive stars using broad-band infrared photometry. The Support Vector Machine classifier effectively categorizes massive stars as hot, cold, or emission-line, exhibiting high precision while rejecting low-mass contaminating giants. These classifications serve as training data for our decision tree method.

- Contaminant = C/S/giant stars and yellow dwarfs (126 occurrences)
- Cool = RSGs and YSGs (1059 occurrences)
- EM = Emission: WR stars, LBVs, and OB[e] and OBAe stars (440 occurrences)
- Hot = all OBA star classes, excluding OB[e] and OBAe (2309 occurrences)
- Unknown/Candidate = divergent variables and unknown/candidates (2550 occurrences)

Note that stars classified as contaminants were omitted from the table due to their low occurrence.


## About the Repository

- 'k_means_clustering_and_decision_tree_objects_classification.ipynb': Python code for performing the classifications
- 'astronomical_objects_classification_and_prediction_with_ML.ipynb' : Improved version of the analysis, providing a more in-depth exploration of the correlations and employing a new approach.

## Dependencies

- numpy
- matplotlib
- pandas
- astroquery
- sklearn

## How to Use the Code

Clone this repository or download the 'k_means_clustering_and_decision_tree_objects_classification.ipynb' file to your working environment. Execute the Python code 'k_means_clustering_and_decision_tree_objects_classification.ipynb' in your environment, using a Python environment of your choice, such as Jupyter Notebook or an integrated development environment (IDE).

First, ensure that the image files are present in the same directory as the Python file. The required libraries must be installed in your Python environment.

## Revised Methodology


### K-Means Clustering - Unsupervised Model

In our case, K-Means will be set to K=4, aiming to create subgroups within the "cLabels" groups defined by the table. This method separates our data into clusters based on similarities in data parameters after multiple iterations. Initially, clusters are defined based on the arbitrary position of centroids. Subsequently, the mean distances for each cluster are calculated, and centroids are readjusted until the mean stops varying.

### Decision Tree - Supervised Model

The Decision Tree will use the sample data to separate the data as much as possible. After each separation, a new parameter is used for further refinement. As this model is supervised, the test and training data were split in a 70/30 ratio.

### Nearest Neighbors Regression for Value Prediction

This technique involves predicting values using a regression model, specifically the Nearest Neighbors Regression. The process begins by removing missing values from selected columns, such as 'BP-RP' and 'G-J'. The parameters with the highest correlation are then chosen, and the dataset is split into training and testing sets. A KNeighborsRegressor model is trained with a specified number of neighbors (k_neighbors). The model's performance is evaluated using the R-squared metric, indicating the proportion of the variance in the dependent variable that is predictable from the independent variable.

## Conclusion

The relatively large dataset size (around 6k) in this catalog allowed for the application of these techniques. I chose the evident correlation between G-J color and G-band magnitude for plotting the clustering. The clustering step provided valuable initial insights, along with basic statistics from the table. Cluster separation was successful. After the initial clustering, an attempt for each object classification (cLabels) was made to compare their positions and test new separations within each classification. In the decision tree step, there was a good outcome with high precision and few false classifications (false positive/false negative). The highest concentration of false classifications occurred in the classification of objects considered unknown/candidates, possibly due to their ambiguous identification in catalogs and the low number of data samples available. For future studies, I suggest a more in-depth investigation into the relationship between unknown objects and EM, as there was some confusion in classifying these objects. Additionally, contaminants may impact results, warranting a reevaluation of the project considering them. Now, looking at the 'astronomical_objects_classification_and_prediction_with_ML.ipynb' file: in the regression model, two scenarios are presented, one with 'BP-RP' as the independent variable, resulting in an impressive R-squared value of approximately 97%. However, when using 'Gmag' as the independent variable, the model's performance decreases substantially to around 31%. The abstract emphasizes the importance of thorough parameter analysis for achieving optimal model relationships. Multiple visualizations, including scatter plots of actual data and predicted values, enhance the understanding of the regression outcomes.

## References
Trevor Z. Dorn-Wallenstein et al 2021 ApJ 913 32
