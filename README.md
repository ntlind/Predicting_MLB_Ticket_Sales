# Predicting Ticket Sales by Category for a MLB Team
## Introduction
In Spring 2017, the Wharton Analytics Fellows were tasked with helping a MLB baseball team answer the following question: how can we predict and optimize the number of tickets sold across our various ticket categories (group tickets, special event tickets, etc.)? To answer this question, we tested a variety of different models and features before building a predictive engine in R that could intake user inputs and forecast ticket sales over time. As a result of this engagement, our client was able to:

* Predict ticket sales across three major ticket categories
* Model results over time to drive decision-making
* Mine for insights throughout the modeling process:
  * Do specific features, such as our team's win record, have a significant impact on ticket sales?
  * How do ticket sales vary over time?
  * How are ticket sales concentrated for each group?
  * When do Group sales drop-off?
  * ... and others

Specific names, data sources, and insights have been withheld to preserve our client's privacy.

## Approach
### Start with "Model Selection" Code
* **Engineer features**
  * Scrape external data sources (Baseball-Reference.com) to develop additional features (e.g., win-loss difference, home-span, etc.)
  * Explore different feature combinations using our 50+ variables
* **Clean and filter dataset before adding new features**
  * Remove NAs
  * Limit timeframe
* **Build statistical models and build descriptive statistics**
  * Divide into test and training sets (80/20%)
  * Perform 10-fold cross-validation to optimize parameters
  * Models tested
    * NBD regression 
* **Automate formulas to improve

Compare error terms and visuals to identify best model and covariates
Minimize out-of-sample forecast error (preferring Median Average Percent Error to other potential error metrics)
Examine predicted vs. actual plots to visually inspect fit


Use statistically-significant features to model results over time
Add day_diff (t-minus days ‘til game) and last_week (captures spike in the last week of ticket sales) to model results over time
Review forecasts to ensure they align with non-time-varying estimates


Two sets of code in this repository:
* **Model Selection** - Test OOS MAPE of multiple models before choosing the best fit.
* **Final Model** - Intake user inputs via .csv before making final forecasts using the NBD regression.
