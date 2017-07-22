# Predicting MLB Ticket Sales by Category
## Introduction
In Spring 2017, the Wharton Analytics Fellows were tasked with helping a MLB baseball team answer the following question: how can we predict and optimize the number of tickets sold across our various ticket categories (group tickets, special event tickets, etc.)? To answer this question, we tested a variety of different models and features before building a predictive engine in R that could intake user inputs and forecast ticket sales over time. As a result of this engagement, our client was able to:

* Predict ticket sales across three major ticket categories
* Model results over time to drive decision-making
* Mine for insights throughout the modeling process:
  * Do specific features, such as our team's win record, have a significant impact on ticket sales?
  * How do ticket sales vary over time?
  * How are ticket sales concentrated for each group?
  * When do Group sales drop-off?

Specific names, data sources, and insights have been withheld to preserve our client's privacy.

## Approach
### Start with "Model Selection" Code
* **Load data sources**
  * Join tables
  * Set parameters
  * Rename columns
* **Engineer features**
  * Scrape external data sources (Baseball-Reference.com) to develop additional features (e.g., win-loss difference, home-span, etc.)
  * Explore different feature combinations using our 50+ variables
* **Clean and filter dataset before adding new features**
  * Remove NAs
  * Limit timeframe
* **Build statistical models and visualize descriptive statistics**
  * Select features for use in modeling
  * Divide into test and training sets (80/20%)
  * Models tested
    * Multivariate linear regression
    * Random Forest
    * NBD regression
  * Perform 10-fold cross-validation to optimize parameters
  * Visualize results
* **Compare error terms and visuals to identify best model and covariates**
  * Minimize out-of-sample forecast error (preferring Median Average Percent Error to other potential error metrics)
  * Examine predicted vs. actual plots to visually inspect fit
  * Review forecasts to ensure they align with non-time-varying estimates
  * Select final model (NBD)
   * Decision rationale
    * Though the boosted Random Forest’s error terms were slightly better, we’d prefer not to use a “black box” model due to its uninterpretable results
    * The NBD regression is relatively simple to implement; many different tools and technologies can automatically run this type of model (e.g., Excel)
    * Our selected model and features are well-aligned with academic research within this space (Fader, Suher, etc.)
    * There wasn’t much variation in percent error between model types across our three ticket categories, as depicted below
* **Develop user-friendly engine** (called "Final Model")
   * Automate formulas
   * Remove excess steps / features
   * Intake user inputs
   * Export forecasts
  
## Code Descriptions
There are two R files in this repository:
* **Model Selection** - Test OOS MAPE of multiple models before choosing the best fit.
* **Final Model** - Intake user inputs via .csv before making final forecasts using the NBD regression.

## Potential Improvements
* Scale ticket sales to limit effects of outliers and improve computational performance
* Test more sophisticated models (e.g., RNNs)
* Trim code for efficiency

