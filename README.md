# Customer Satisfaction Analysis

## Project Overview

This Customer Satisfaction Analysis project aims to evaluate customer feedback and identify key factors driving both satisfaction and dissatisfaction.

The dataset is sourced from a customer satisfaction survey conducted at Kashmir Café, focusing on the quality of service provided through food delivery. The analysis seeks to uncover insights that can guide strategic decisions to improve customer satisfaction, optimize delivery processes, and enhance overall service quality.

This analysis emphasizes four main areas of customer feedback:

- Delivery Experience
- Food Quality 
- Delivery Speed
- Order Accuracy

## Objectives

- Assess overall customer satisfaction levels.
- Identify areas where Kashmir Cafe excels and where improvements are needed.
- Measure the impact of delivery speed, food quality, and order accuracy on customer satisfaction.
- Provide data-driven recommendations to improve customer satisfaction.

## Data Sources

The dataset used in this analysis was obtained from **Kaggle** and is titled **"Customer Satisfaction Survey at Kashmir Cafe."** It contains customer feedback on their delivery experience, food quality, delivery speed, and order accuracy.
This dataset originally consisted of 10,616 rows and 5 columns, each representing different aspects of customer satisfaction.

### Column Descriptions / Data Dictionary

1.	**Customer_ID**: A unique identifier for each customer.
2.	**Delivery_Experience**: Customer's rating on a scale of 1 to 5 for their delivery experience.
3.	**Food_Quality**: Customer's rating on a scale of 1 to 5 for the quality of the food.
4.	**Delivery_Speed**: Customer's rating on a scale of 1 to 5 for the delivery speed.
5.	**Correct_Order**: Indicates whether the customer's order was accurate, with responses recorded as Yes or No.

### Rating Scale Interpretation

For the Delivery_Experience, Food_Quality, and Delivery_Speed columns, customer ratings are measured on a 1 to 5 scale:
- 1 – Extremely Dissatisfied
- 2 – Dissatisfied
- 3 – Neutral
- 4 – Satisfied
- 5 – Extremely Satisfied
Only ratings **1** and **5** were explicitly defined in the original dataset. Ratings **2**, **3**, and **4** were introduced during the analysis to provide a more detailed breakdown of customer sentiment.

## Tools
**Power BI:** Creating DAX measures, and visualizing insights.

**Power Query:** Data cleaning , transformation, and creating custom columns.

## Problem Statements

- What is the overall customer satisfaction rate across all service areas?
- How do customers rate their experience with delivery, food quality, and delivery speed?
- What percentage of customers are satisfied, neutral, or dissatisfied across each service category?
- What is the relationship between order accuracy and customer satisfaction?
- Which service factor (delivery experience, food quality, or delivery speed) has the greatest influence on customer satisfaction?
- How many customers did not provide responses, and what impact does this have on the analysis?

## Data Cleaning and Transformation 

1. **Renamed Columns**
   
The dataset initially contained five columns with detailed headers. These were renamed for consistency and clarity:

- Customer - Customer_ID
- How satisfied were you with your overall delivery experience at Ali? -  Delivery_Experience
- How satisfied were you with the quality of food at Alis? - Food_Quality
- How satisfied were you with the speed of delivery at Alis? - Delivery_Speed
- Was your order accurate? Please respond Yes or No - Correct_Order

2. **Changed Data Types**
   
Data types were standardized to ensure accurate calculations in Power BI.

3. **Handling Missing Values**
   
**Delivery_Experience** (418 null values), **Food_Quality** (252 null values), **Delivery_Speed** (239 null values):

Null values were replaced with the mode (most frequent value) of each column using Power Query.

[Insert screenshot showing how the mode was obtained using GROUP BY for Delivery_Experience.]

The same method was applied to Food_Quality and Delivery_Speed.

**Correct_Order** (660 blank rows):

Blanks were replaced with "No Response" using the "Replace Value" function in Power Query.

4. **Checked for Duplicates**
   
A duplicate check was conducted on Customer_ID, and no duplicates were found.

5. **Creating Custom Columns**
   
To enhance analysis, the following custom columns were created:

- Overall_Satisfaction

- Delivery_Experience_Category

- Food_Quality_Category

- Delivery_Speed_Category

 [Insert screenshots showing the formulas used to create each custom column.]


## Data Analysis and Visualization



### DAX Measures

To facilitate detailed analysis, the following DAX measures were created:

1. Total Responses - Count of unique customer survey responses.
   
```DAX
Total Responses = DISTINCTCOUNT(Customer_survey_data[Customer_ID])
```










