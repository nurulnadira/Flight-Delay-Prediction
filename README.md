# US Flight Delay Prediction

In 2019, the Federal Aviation Administration (FAA) reported 299,244 flights delayed at the core airports in the USA with delay cost amounting to $33 billion and every year airlines companies are losing more money due to delays. If a prediction model could be developed to forecast future delays, this would be very economical to both airline companies and customers.

There are many factors that potentially contribute to the delayed flights such as weather, security, and many others. This study aims to create a model to predict arrival delays using the historical data of flights in the USA. It also considers all airline, destinations, and
origins of the flights in creating the predictive model. The flight dataset was used to create prediction model using logistic regression,
random forest regression and decision tree. Several data cleansing techniques were applied beforehand to improve the quality of the data such as removal of missing values, filling in the missing values with mean data, outlier detection removal and normalization. For all three
models, the accuracy of the predictive model was tested and analyzed to provide a good recommendation. With the prediction model, the airline companies will be able to predict and minimize potential delays and save their expenditure on flight delays.

The purpose of this study is to forecast the likelihood of all planes arriving late and make recommendations to enhance airline operations by using past data. If a flight arrives 15 minutes beyond its stated arrival time, it is considered delayed. The model will be based on extensive flight data from all major airlines' domestic flights in the United States.

# Source Data
For this analysis, the flight historicAL data was gathered from “Data Expo 2009 – Airline on-time performance”. The data consists of 29 recorded flight characteristics that may be divided into four categories. In total, there are 1,936,753 flights considered.

# Methodology

This is a supervised learning problem as the data contains the input and output data and it is a classification problem as the outcome will be binary, whether the flights are delayed or not. The prediction of flight delays was seen as a regression issue which can be solved using multiple linear regression (Ding,2017). Multiple linear regression was used in research to predict flight delays in flight data based on weather using few attributes as departure and arrival time, origin and destination (Oza et al., 2015). Choi et.al (Choi et al., 2016) applied decision tree, AdaBoost, random forest and k-Nearest Neighbours were applied using flight schedule data and weather to predict delays on individual flights along with sampling techniques to balance the data. In this study, the prediction of flight arrival were computed using three machine learning methods: Logistic regression, random forest regression and decision tree. The data was first cleanse to standardize the format, impute missing values and treat outliers. The categorical data were converted to numeric before modelling. The data was split to train and validation. Lastly, the results were analyze by using the classification based metrics: confusion matrix and ROC curve.


# 1. Data Preparation and Pre-Processing

The initial step taken to perform analysis on the flight cancellations and delays is to ensure the quality of the data. Most of the time and date data were in either integer or float data types. To ensure that the model can be run smoothly, the data types were changed to a standard date-time format. Several patterns of columns with the same amount of missing data, such as 'Arrival Time' and 'Taxi in,' may be seen from here. 

The arrival time and Taxi In have NaN values, indicating that the planes were either cancelled or diverted, according to the data. As  result, the NaN values were replaced with integer numbers. If the flights were cancelled or diverted, technically there would not be any carrier, weather, NAS, Security or Late Aircraft
delay. This is proven to be the case for all cancelled flights that does not have NaN values in the delay reason columns.

Hence, the delay reasons were standardized to 0 for all cancelled and diverted flights. The arriving and departure time will be too large to be converted to numerical data. As such, these two variables were changed to indicate if the flight depart or arrive in the early morning, morning, afternoon, evening or night. As the model output should be whether the flight will be delayed or not, a new column “Delayed” were created and defined as binary 0 or 1 if it is on-time or delayed respectively. 

The missing values for ‘CRS Elapsed Time’ was also replaced by calculating manually the difference between ‘CRS Arrival Time and ‘CRS Departure Time’. For the missing values in delay reason columns, since the number of missing values is about 35% from the whole population, imputation using the mean of the column were done to fill in the gaps. 

Next, the irrelevant and unnecessary column were then removed to avoid overburden the dataset and the remaining rows with missing values were drop from the dataset. Lastly, after the outliers more than 2 standard deviation were removed, the datasets were normalized and categorical data were transformed to numeric data.

**Before Outliers Removal**

![Before removing outliers](https://github.com/nurulnadira/flightdelayprediction/blob/9cc5e08d8111cec18d589d2cc56a7ca38ec2a19f/Outlier%20Detection%201.png)

**After Outliers Removal**

![After outliers removal](https://github.com/nurulnadira/flightdelayprediction/blob/fce51a7d56139db06147e14bfa2ed75dfed169d4/Outlier%20Detection%202.png)

![This is an image](https://github.com/nurulnadira/flightdelayprediction/blob/17e218828e9c42c063d5e29bd8b506936c464f99/ROC.png)


# 2. Features Selection

To improve model results, it is important to determine the correlation between each parameter. Correlation matrix were computed to determine the correlation between each parameter and delays. Since the data contains both continuous and categorical variables, the correlation matrix was created by using correlation ratio from Dython’s library in Python:

![Correlation Matrix](https://github.com/nurulnadira/flightdelayprediction/blob/ffe2958d9528f8c40121cd10f1f716affd6c2c7a/Correlation%20Matrix.png)

Based on the correlation matrix, there is a relationship between arrival delays and departure time, arrival time, unique carrier, taxi in, taxi out, carrier delay, weather delay, NAS Delay, security delay and late aircraft delay. To accurately estimate the prediction, the results will be used as the predictors. 

# 3. Prediction Models

# a. Logistic Regression

The logistic regression was run and confusion with the abovementioned features. The model indicates that the test accuracy is 68.50%. Based on the confusion matrix below, the model has a 0.60 and 0.71 precision to predict whether the flights will not be delayed or delayed respectively.

# b. Decision tree

The decision tree constructs classification models in the form of a tree structure and breaks down the data into smaller groups while simultaneously developing an associated decision tree. Using the same dataset and predictors as logistic regression, the model accuracy is 99.93%. Based on the confusion matrix below, the model has a 1.0 and 1.0 precision to predict whether the flights will not be delayed or delayed respectively. There is no ROC graph that can be computed for decision tree, however, the ROC AUC is very high, 0.9993381319717791.

# c. Random Forest Regression

Similarly, the data were fit into random forest regression. The random forest regression has accuracy of 98.31%. Based on the confusion matrix below, the model has a 1.0 and 0.97 precision to predict whether the flights will not be delayed or delayed respectively. There is no ROC graph that can be computed for decision tree, however, the ROC AUC is also quite high at 0.983098017043973.

# Results and Discussion

Based on the three models above, we can observe that the decision tree has the best prediction accuracyand outperformed random forest and logistic regression
prediction model.

As such, we can recommend the airline companies to investigate the flights that have most delays. Based on above, the companies can focus to investigate and improve flight delays from carriers that have more than 50% chance of delays. Moreover, if the Taxi In, Taxi Out, carrier delay, weather delay, NAS Delay and Security delay issues mitigated, it can reduce the number of flight delays. On another hand, the departure time and arrival time also affects the delay of flights. As
shown in the figure below, in average the night and late-night flights that depart and arrivehave the higher number of flight delays. There may be reasons why is this the pattern such as Page 11 of 12 resource allocation issues during night shift, but, if the night flights can be avoided, it would give a better chance for the flights to not be delayed.

# Conclusion

In conclusion, three predictive model were successfully created using the flight data to predict whether a flight will be delayed or not. Prior to fitting the data into the models. several data cleansing steps were taken, where some of the data were omitted and transformed to maintain data quality. The three models used were the decision tree, random forest and logistic regression models. The random forest and decision tree regression model has better accuracy compared to logistic regression. Based on the model, we can identify that there were 10 features play a significant role if there will be potential delays.
