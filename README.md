# Project Title
What Drives the Price of a Used Car?

## Description
This repo contains the CRISP-DM framework applied on Used car data set from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data)

* [Jupyter Notebook](https://github.com/ddurgoji/used-cars-price-prediction/blob/main/used-cars-price-prediction.ipynb)
    * Jupyter Notebook containing code used to perform this analysis.
* [Readme](https://github.com/ddurgoji/used-cars-price-prediction/blob/main/README.md)
    * Project description
* [Dataset](https://github.com/ddurgoji/used-cars-price-prediction/blob/main/data/vehicles.csv)
    * This dataset is from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data). It is collected from Craiglist website.

## Summary
#### Business Understanding
The prices of new cars are fixed by manufacturer with additonal cost like sales tax, destination charges etc. so its very important for customers that the money they invest is worthy. After covid due to chip shortage new car production rate went drastically down. This caused increase in demand for used cars. Due to Russia-ukraine war, Supply chain got disrupted which made used car demand shoot up even higher.

Due to rising inflation in united states, People have less money to spend and this has caused used car demand to go up even higher. For consumer its very important to get a good quality car for the money they spend and its very important for Car dealership to build their inventory with good cars which helps them in increasing their revenue and also increase customer satisfaction.

In this project, i am trying to build various regression models which helps in predicting used car prices with high accuracy and provide some insights to car dealership on what features customers value more and drives the car prices high.

#### Data Understanding
* Read CSV Dataset using Pandas.
* Used Pandas Profiling report to understand data columns better.
* Using Plotly plotted various histograms to understand distrinution of various columns.

#### Data Preparation
* Removed VIN, state, region columns.
* Numerical Features
  * Year
  * Odometer
* Categorical Features
  * Manufacturer
  * Model
  * Condition
  * Cylinders
  * Fuel
  * Title status
  * Transmission
  * Drive
  * Size
  * Type
  * Paint color
* Used below estimator and cross_val_score to find best estimator with lower MSE to replace all Nan values in categorical features. BayesianRidge gave better performance.
  * BayesianRidge
  * DecisionTreeRegressor
  * ExtraTreesRegressor
  * KNeighborsRegressor
* Removed the outliers from Price, Odometer and Year numerical features.
  * Applied Logarithm on Price target feature since it was skewed and not normally distributed.
* Using plotly and seasborn plotted few graph post Data Preparation work.

#### Modelling
* Scaled numerical and Target feature columns.
* Created Train(90%) and Test(10%) dataset.
* Built below Regression models:
  * Linear Regression with RFE and GridSearchCV with KFold(n_splits=5) - Accuracy=63.231%
  * Ridge Regression with CV, alphas = 10**np.linspace(10,-2,400) - Accuracy=63.244%
  * Lasso Regression with CV, alphas = 10**np.linspace(10,-2,400) - Accuracy=63.008%
  * Random Forest Regression - Accuracy=91.142%
Here is the table showing Performance/Accuracy of all above models. Random Forest Regression model was best performing model with 91% accuracy.
| Model Name                | Accuracy(%) |
|---------------------------|-------------|
|Linear Regression with RFE | 63.231%     |
|Ridge Regression           | 63.244%     |
|Lasso Regression           | 63.008%     |
|Random Forest Regression   | 91.142%     |

#### Evaluation
* Random Forest Regression model had higher accuracy.
* Plotted a line graph to compare performance of all 4 models that were built.


#### Deployment
* Developed a Python function which accepts below features and provides price prediction using Random Forest Regression model.
  * Manufacturer
  * Model
  * Condition
  * Cylinders
  * Fuel
  * Title status
  * Transmission
  * Drive
  * Size
  * Type
  * Paint color
We can deploy a basic Django/Flask application which uses this function to show used car price prediction.

#### Recommendation to Car dealership
* Year, Odometer are most important items which consumers value most and determines price range of the car.
* Diesel and Electric can sell for higher prices when compared to gas car.
* Higher No of cylinders drive the car price up.
* Title status and condition affects the prices. Salvaged cars are penalized more and brings down prices.
* rwd are penalized more when compared to fwd/4wd. Rwd cars have lower price points.
* Automatic and other transmission type have higer price points and Manual reduces the car price.

These are some of recommendation which car dealership can use to procure used car to drive sales up and provide great customer satisfaction.
Complete details are in [Jupyter Notebook](https://github.com/ddurgoji/used-cars-price-prediction/blob/main/used-cars-price-prediction.ipynb).

## Technologies Used
Below are some of important technologies used in this project.
* [Python](https://www.python.org)
* [Jupyter Lab Notebook](https://jupyter.org)
* [Plotly](https://plotly.com)
* [Seaborn](http://seaborn.pydata.org)
* [Pandas](http://pandas.pydata.org)
* [Scikit-learn](https://scikit-learn.org/stable/)
and some more.


## Author
Dhiraj Durgoji (djdhiraj.8189@gmail.com)
