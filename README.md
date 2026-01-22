# PowerCo Customer Churn Prediction

PowerCo is a major European gas and electricity provider serving SME (Small & Medium Enterprise) and residential customers. Following market deregulation, the company faces significant customer losses in their SME segment. With acquisition costs far exceeding retention costs, identifying at-risk customers before they churn is critical to protecting revenue.

## Repo Contents 

**1. client_data.csv** - Customer-specific details and historical data

**2. price_data.csv** - Pricing information across different seasons and periods

**3. data_description.txt** - Detailed explanation of all dataset features

**4. Churn_Analysis.ipynb** - Complete analysis including data cleaning, modeling, and visualizations

## The Challenge 

- **Severe class imbalance**: Only 10% of customers churn, making standard models ineffective
- **Business constraint**: Model must prioritize catching churners over minimizing false alarms

## Approach 

### Data Cleaning & Preparation

Combined both datasets and removed missing values. Eliminated redundant columns that had no clear relationship to churn behavior.

### Baseline Model

Started with Logistic Regression using all features, achieving 62% recall.

### Feature Selection (Logistic Regression) 
Extracted the top 6 most important features, chosen by the previous logisticv regression model i.e.: net_margin	margin_net_pow_ele	forecast_price_energy_off_peak	cons_gas_12m	num_years_antig	price_peak_fix. Logistic Regression with these selected features achieved 63% recall and 14% precision at threshold 0.4.

### Model Improvement

Implemented Random Forest with class weighting ({0:1, 1:10}), using all features, achieving comparable performance: 63% recall and 15% precision at threshold 0.4. Key finding: Feature selection and ensemble methods produced similar results, suggesting the top features capture most of the predictive signal. Chose Random Forest for the final model due to its robustness and ability to capture non-linear relationships.

## Visualizations

Confusion matrix, feature importance analysis, and ROC curve demonstrating model performance are available in the Jupyter notebook.

## Results 

**Model Performance (Random Forest, threshold 0.4):**
- **63% Recall**: Identifies 222 out of 355 churning customers
- **15% Precision**: Strategic trade-off accepting false positives to catch more churners
- **Business Impact**: Enables targeted retention campaigns with potential €200K+ revenue protection

## Key Insights 

- **Low-margin customers are the highest flight risk**: Those already on discounted rates are most likely to churn, revealing that price sensitivity—not absolute pricing—drives defection
- **Meter rental fees matter**: Forecasted meter rental costs emerge as a significant churn predictor, suggesting that charges push price-conscious customers to competitors
- **High consumption increases churn risk**: Larger electricity usage correlates with higher churn rates, as bigger bills make an impact of even small price differences
- **Top predictive features**: Net margin on power subscription, gross margin, forecasted meter rental, and 12-month electricity consumption

## Technical Stack

`Python` `Pandas` `Scikit-learn` `Matplotlib` `Seaborn` `Random Forest` `Imbalanced Learning`



