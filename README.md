# Wellbeing in Shanghai

In order to predict the wellbeing in Shanghai through the prediction of 3 elements (clean, noise, smell), the work have been done in 4 steps:

Cleaning the data of datasets (cendus_poi, dianping_poi, flickr, mobike, real_estate, taxi_speed, weibo)

  - Procces: removing the NA value in longitude, latitude and interresting columns
  - Removing the points that are far from Shanghai
  - Removing the duplicated rows
  - Projection of the points in meters (epsg: 4326 to epsg:4479)
Creating relevant criteria from the cleaned datasets.

Getting the target dataframe with the criteria ready for the training part (this file has some comment of this step: prediction-decisionTree.ipynb)

  - I have created a lot of criteria during the previous step but some of them contains too many NA to be exploitable.
  - I had to create 2 functions that are used to clean the columns with too many NA unless the proprotion of each class will be kept if we removed the corresponding rows.
Fitting some models

## Results
(I have put some comments in ./prediction/prediction-decisionTree.ipynb)

**First I tried to predict clean, noise and smell in Shanghai**

The first model I used was the decision tree, I didn't have so good result (score: 77.9% and f1_score: 0.1 for the noise for example)
The under-represented class, the lack of values in the target and the subjectivity of the people that have respond the form make the prediction really difficult.


**Then I created a new element to predict called "Wellbeing"**
It has been creating by separating clean into 2 classes 0 clean / 1 not clean and concatenating the value of noise and smell. So the best class would be 000.

With the decision tree, I had a score of 41% and a weighted f1_score of 0.33 for 7 classes.

From the decision tree it is also important to know that the average onesquaremeter meter price, the number of bedroom, the number of companies, mobike and some other point of interest were used to build the model. Therefore we know that these criteria as an impact on the wellbeing in Shanghai.

To conclude, I would suggest the city of Shanghai to use my model Random Forest to predict the area of Shanghai where people think is not clean, quiet or good to breath in order to work on these area and improve Shanghai people life and wellbeing.