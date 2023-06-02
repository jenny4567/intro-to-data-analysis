# Using statistics to make predictions based on data

---
## Learning objectives
- Understand the concept and applications of predictive analytics
- Learn about regression analysis and its types, including simple linear regression, multiple linear regression, and logistic regression
- Understand the concept of time series analysis and its components, such as decomposition and forecasting with ARIMA
- Learn about clustering and its purpose in data exploration, summarisation, and segmentation.
- Understand when to use what technique.


---
## Introduction
### Why predictive analytics?
Predictive analytics is a branch of data analysis that uses historical data and statistical algorithms to make predictions about future events or outcomes. The goal of predictive analytics is to identify patterns and trends in the data that can be used to forecast future trends, behaviours, and events.

What is important in this module, and possibly the most key thing to take away, is to learn when you need apply which model dependent on the data you are exploring and analysing.

### Applications
Predictive analytics can be used in a wide range of applications, including marketing, finance, healthcare, and operations management. For example, a retailer might use predictive analytics to forecast demand for a particular product, based on historical sales data, weather patterns, and other variables. This could help the retailer to optimise its inventory and pricing strategies and ensure that they have sufficient stock to meet customer demand.
In healthcare, predictive analytics can be used to identify patients who are at risk of developing a particular condition or disease based on their medical history and other risk factors. This can help healthcare providers to develop targeted interventions and preventative strategies and improve patient outcomes.

---
## Methods and techniques
### Regression Analysis
Regression analysis is a statistical method used in descriptive analytics to examine the **relationship between a dependent variable and one or more independent variables**. The primary goal of regression analysis is to understand how changes in the independent variables affect the dependent variable.
Regression analysis is often used to make predictions or forecasts based on historical data. It is also used to identify trends, relationships, and patterns in the data. There are several different types of regression analysis, including 
- **simple linear regression** and **multiple linear regression**
    -  Linear regression is suitable when you have a continuous dependent variable and want to understand the relationship between that variable and one (**simple**)or more (**multiple**) independent variables.  (Use when variable you are predicting is a number in a range that is not a count.)
- **logistic regression**.
    - Logistic regression is used when the dependent variable is binary or categorical. It models the probability of an event occurring based on independent variables. (Use when variable you are predicting is either `1` or `0`.)

### Time Series Analysis
Time series analysis is used to analyse data that is measured over time, where the goal is to understand the patterns and trends in the historical data. In comparison with Regression Analysis, we do not look into different variables. We **use the historical data alone to predict future values** based on previous patterns and trends.
    - Time series analysis is used when you have data collected over time and want to understand and model the patterns, trends, and dependencies within the data.  (Use when data is changing over time.)

### Clustering
Clustering is a technique that aims to group similar objects or data points based on their characteristics or features without predefined labels or categories. The aim of clustering is to **identify patterns or similarities** in the data that can help in data exploration, summarisation, or segmentation. Clustering can be used to identify **natural groupings in the data** that can help in making business decisions or identifying customer segments, among other things.
    - Clustering is used to identify groups or clusters in your data based on similarities or patterns. (clustering is useful in scenarios where there is a need to identify natural groupings or patterns in data.)

### Which method to choose?

The choice on which of these techniques to use depends on the data you are analysing and the specific goal of your analysis. It's important to carefully assess your data, the question you are attempting to answer, and the assumptions and limitations of each of these techniques in order to make an informed decision. In some cases, a combination of these techniques or incorporating multiple methods may be necessary to gain a comprehensive understanding of the data and address the research question effectively.

**You are not expected to know these methods inside out, nor are you to be expected to explain in detail the mathematics behind them. As long as you know which method to use when exploring your data - your predictions will make sense. That's a good start for Predictive Statistics.**

---
## Chapters
The module is split into these chapters: 

**Regression Analysis**
- [Simple Linear Regression](./bites/01_simple_linear_regression_intro.md)
- [Simple Linear Regression - Model Validation](./bites/02_linear_simple_linear_regression_model_validation.md)bites/
- [Multiple Linear Regression ](./bites/03_multiple_linear_regression.md)
- [Logistic Regression](./bites/04_logistic_regression.md)
- [Logistic Regression - Model Validation](./bites/05_logistic_regression_model_validation.md)

**Time Series Analysis**bites/
- [Time Series](./bites/06_timeseries.md)
- [Time Series - Decomposition](./bites/07_time_series_decomposition.md)
- [Time Series - Forecasting with ARIMA](./bites/08_timeseries_forecasting_with_ARIMA.md)

**Clustering**
- [Clustering](./bites/09_clustering.md)

<BR>

## Get started

[Simple Linear Regression](./bites/01_simple_linear_regression_intro.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites02%2F00_intro_prescriptive_stats.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites02%2F00_intro_prescriptive_stats.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites02%2F00_intro_prescriptive_stats.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites02%2F00_intro_prescriptive_stats.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites02%2F00_intro_prescriptive_stats.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
