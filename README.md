# Fueling-Clean-Initiatives
Predicting ideal collaborators given empirical renewable energy investment data

# Exploratory Data Visualization
Amount of assistance from 2015 - 2019

<img width="800" alt="Amount of assistance from 2015 - 2019" src="https://user-images.githubusercontent.com/90943803/215337500-630959e5-006e-4afe-9533-8ed66c2ab633.gif">

Amount of investment per state from 2015 - 2019

<img width="800" alt="Amount of assistance from 2015 - 2019" src="https://user-images.githubusercontent.com/90943803/215336904-d50010ec-6610-414a-abbe-465c4a821798.png">
<img width="600" alt="Amount of assistance from 2015 - 2019" src="https://user-images.githubusercontent.com/90943803/215338067-db24dffc-7485-415b-91b5-af9b8280d82d.png">


# Results
## Amount of assistance per state in 2020
<img width="800" alt="predictiongraph" src="https://user-images.githubusercontent.com/90943799/215335689-33297687-b811-48b4-b99f-bf4de3a70fd1.png">

## Top 5 states receiving amount of assistance in 2020
<img width="800" alt="Screenshot 2023-01-29 at 9 36 24 AM" src="https://user-images.githubusercontent.com/90943803/215337341-134e9dd8-ba91-43be-8c6c-b76cee52ca07.png">


## How we built it
We decided to perform a grid search for a random forest, using the GridSearchCV function from scikit-learn library. This grid search tried different combinations of n_estimators and max_depth, and use 5-fold cross-validation to evaluate the performance of the model. I then used RandomForestRegressor fit the training data and made predictions on test data. We originally decided against using time series because data per state does not exhibit a clear trend. However, there is a trend in the overall dataset and since the training dataset isn’t particularly large, we decided to use time series forecast as part of our final ensemble model. That being said, the majority of the production is contributed by a RandomForestRegressor. 

In my final model, I group the DataFrame by state and iterates through each state. For time series, I fit an ARIMA model using the data from the past 5 years, then use the fitted model to predict investment in 2020. Using the best parameters found through grid search, I fit the best RandomForestRegressor model to the entire training data and then predicted the amount of investment for 2020 By processing the feature vectors the same way I processed the training data set. For the ensemble part of my model, through trial and error during training, I found a good ratio for how much weight is given to time series prediction and RandomForestRegressor, which I applied to testing. 

## Challenges we ran into
If we had time, we would try to find datasets to augment the training data, such as data from years before 2015 and/or other data sets that can provide additional feature vectors. I would also use a decision tree to figure out the weight for a ARIMA and random forest instead of using trial and error. 

## Accomplishments that we're proud of
Our data corrected predicted the top five state with the greatest amount of assistance that were the same as those in the testing dataset for 2020.

## What's next for "Fueling" Clean Initiatives
We would love to look into additional datasets and factor in additional variables to help make a more informed decision about choosing investors. Exploring the alternative fuel data more in-depth, for example, would help us identify an economic incentive in investing in states that encourage use of renewable energy. In addition, looking at data within what we were provided such as CO2 emissions, or mapping amount produced to amount invested to identify productivity trends, would make our models more holistic and mitigate the problem this challenge presented better. 
