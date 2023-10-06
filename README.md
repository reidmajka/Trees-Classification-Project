# Trees-Classification-Project
Flatiron School - Phase 3 Classification project

New York city has over 680,000 trees planted on "the street" (sidewalk, medians, etc.). It's no surprise that it takes a substantial Parks Department to manage these trees, and ensure optimal health and growth. Maintaining an urban canopy is crucial to the health and success of a city's environment and human population - it's estimated that $60M is diverted from the healthcare system annually through the existence of our urban canopy (1).

Using data from NYC Opendata, create a machine-learning model to predict whether a street tree is in need of care and/or replacement. This will provide NYC Parks department with an optimized model to prioritize trees needing care, minimizing resources to fix and increase the canopy across the city

## Predictor Variables
Two sets of predictor variables were assessed - Life status (Dead/Stump vs alive) and "Problems" vs. no problems. Problems were classified whether any value (other than 'None') was input into the problems variable. The shape of the original dataset from NYCOpenData includes 683,788 rows (trees) and 42 columns. A vast majority of the columns include categorical data - the only two continuous numeric variables we used were trunk diameter at breast-height of 54" (tree_dbh) and geographical coordinates (longitude, latitude).

## Predicting Life Status
When building the base model for Life Status, it was observed that the model had 100% accuracy. Upon further EDA of the predictor variables, it was clear that any tree classified as "Dead/Stump" had little further information on the tree plot - therefore, it was best to scrap this target variable, and build a new model. This model was kept as part of our Conclusions/Next steps, in order to further better the dataset.

## Predicting Problems Status
Problems status was the clearest indicator of a tree needing attention within the dataset (before turning to dead/stump). A multitude of predictor variables were included: 
* Community support (community board, steward(s), assessor)
* Tree details (species, guards, trunk diameter, alive/dead status)
* Geography (block location, district, borough, geo-coordinates)

### Baseline Model
The baseline model resulted in 98% precision, 88% Accuracy, and 70% recall. The goal is to aim for higher recall, to minimize chance a tree with problems is classified as “normal”, when in fact it needs attention. 

Note: a decision tree model was constructed after the base logistic regression model, and the scores were significantly lower; therefore, logistic regression models

### Optimized Model
A few different hyper-parameters were tuned in order to increase the scores of the baseline model. This included the following:
* Increased iterations
* Threshold of 35%: lowering the threshold did slightly decrease accuracy, though the offsetting increase in recall was substantial enough to use this value
* Lower regularization strength: given that the dataset was largely regular to begin with, it made sense to lower this parameter
* Balancing the dataset: given the large amount of data rows, downsizing on the majority class (no problems) was performed, resulting in lower scores across the board. Therefore, the original dataframe was retained in the optimal model.
* solvers and penalties: ridge penalty and liblinear solver was assessed, returning lower scores than lasso and lbfgs solvers.
  
The resulting optimized Logistic Regression model returned scores of 90% precision, 87% Accuracy, and 75% recall. 

## Conclusions & Next Steps 
Overall the model is strong enough to predict whether a given tree might have a problem, and the model will be used to improve trees across the city.
Prioritize re-planting at these sites with dead trees (or 
stumps)
* Predictions on Health status vary – the model is good at predicting if the tree is alive, but more information is needed to predict if it is in sub-optimal health
* Most importantly: just go outside and check! Call 311 if you see a tree in need.

### Next Steps:
* Partner with parks department to revisit trees in suboptimal health, and gather better data parameters in order to better tune the model
* utilize different modeling tactics (clustering) to find hotspots in the city that may have a higher proportion of trees in need
* Gather incremental data to increase performance: Zoning district, air quality, demographics of surrounding population


Sources:
(1): 2 - Nowak, D.J., et al., Modeled PM 2.5 removal by trees in 10 U.S. cities and associated health effects. Environmental Pollution, 2013. 178: p. 395-402.
