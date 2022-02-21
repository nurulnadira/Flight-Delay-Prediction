# US Flight Delay Prediction

In 2019, the Federal Aviation Administration (FAA) reported 299,244 flights delayed at the core airports in the USA with delay cost amounting to $33 billion and every year airlines companies are losing more money due to delays. If a prediction model could be developed to forecast future delays, this would be very economical to both airline companies and customers.

There are many factors that potentially contribute to the delayed flights such as weather, security, and many others. This study aims to create a model to predict arrival delays using the historical data of flights in the USA. It also considers all airline, destinations, and
origins of the flights in creating the predictive model. The flight dataset was used to create prediction model using logistic regression,
random forest regression and decision tree. Several data cleansing techniques were applied beforehand to improve the quality of the data such as removal of missing values, filling in the missing values with mean data, outlier detection removal and normalization. For all three
models, the accuracy of the predictive model was tested and analyzed to provide a good recommendation. With the prediction model, the airline companies will be able to predict and minimize potential delays and save their expenditure on flight delays.

The purpose of this study is to forecast the likelihood of all planes arriving late and make recommendations to enhance airline operations by using past data. If a flight arrives 15 minutes beyond its stated arrival time, it is considered delayed. The model will be based on extensive flight data from all major airlines' domestic flights in the United States.

# Source Data
For this analysis, the flight historic data was gathered from “Data Expo 2009 – Airline on-time performance”. The data consists of 29 recorded flight characteristics that may be divided into four categories. In total, there are 1,936,753 flights considered.

# Methodology

This is a supervised learning problem as the data contains the input and output data and it is a classification problem as the outcome will be binary, whether the flights are delayed or not. The prediction of flight delays was seen as a regression issue which can be solved using
multiple linear regression (Ding,2017). Multiple linear regression was used in research to predict flight delays in flight data based on weather using few attributes as departure and arrival time, origin and destination (Oza et al., 2015). Choi et.al (Choi et al., 2016) applied decision tree, AdaBoost, random forest and k-Nearest Neighbours were applied using flight schedule data and weather to predict delays on individual flights along with sampling techniques to
balance data. In this study, the prediction of flight arrival were computed using three machine learning methods: Logistic regression, random forest regression and decision tree. The data was first cleanse to standardize the format, impute missing values and treat outliers. The categorical data were converted to numeric before modelling. The data was split to train and validation. Lastly, the results were analyze by using the classification based metrics: confusion matrix and ROC curve.


