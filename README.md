# Trees-Classification-Project
Flatiron School - Phase 3 Classification project

Using data from NYC Opendata, create a machine-learning model to predict whether a tree is in need of care and/or replacement
Provide NYC Parks department with an optimized model to prioritize trees needing care, minimizing resources to fix and increase the canopy across the city


## Predictor Variables
Two sets of predictor variables were assessed - Life status (Dead/Stump vs alive) and "Problems" vs. no problems. Problems were classified whether any value (other than 'None') was input into the problems variable. 

## Predicting Life Status
When building the base model for Life Status, it was observed that the model had 100% accuracy. Upon further EDA of the predictor variables, it was clear that any tree classified as "Dead/Stump" had little further information on the tree plot - therefore, it was best to scrap this target variable, and build a new model. This model was kept as part of our Conclusions/Next steps, in order to further better the dataset.

## Predicting Problems Status

Problems status was the clearest indicator of a tree needing attention within the dataset (before turning to dead/stump). A multitude of predictor variables were included: 
* Community support (community board, steward(s), assessor)
* Tree details (species, guards, trunk diameter, alive/dead status)
* Geography (block location, district, borough, geo-coordinates)

### Baseline Model
The baseline model resulted in 98% precision, 88% Accuracy, and 70% recall. The goal is to aim for higher recall, to minimize chance a tree with problems is classified as “normal”, when in fact it needs attention. 

### Optimized Model
A few different hyper-parameters were tuned in order to increase the scores of the baseline model. This included the following:
* Increased iterations
* Threshold of 35%: lowering the threshold did slightly decrease accuracy, though the offsetting increase in recall was substantial enough to use this value
* Lower regularization strength: given that the dataset was largely regular to begin with, it made sense to lower this parameter


## Conclusions & Next Steps
