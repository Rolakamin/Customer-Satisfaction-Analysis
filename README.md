# Customer Satisfaction Analysis

## Project Overview

This Customer Satisfaction Analysis project aims to evaluate customer feedback and identify key factors driving both satisfaction and dissatisfaction.

The dataset is sourced from a customer satisfaction survey conducted at Kashmir Café, focusing on the quality of service provided through food delivery. The analysis seeks to uncover insights that can guide strategic decisions to improve customer satisfaction, optimize delivery processes, and enhance overall service quality.

This analysis emphasizes four main areas of customer feedback: Delivery Experience, Food Quality, Delivery Speed, and Order Accuracy.

## Objectives

- Assess overall customer satisfaction levels.
- Identify areas where Kashmir Cafe excels and where improvements are needed.
- Measure the impact of delivery speed, food quality, and order accuracy on customer satisfaction.
- Provide data-driven recommendations to improve customer satisfaction.

## Data Sources

The dataset used in this analysis was obtained from **Kaggle** and is titled **"Customer Satisfaction Survey at Kashmir Cafe."** It contains customer feedback on their delivery experience, food quality, delivery speed, and order accuracy.
This dataset originally consisted of 10,616 rows and 5 columns, each representing different aspects of customer satisfaction.

### Column Transformations

The dataset initially contained five columns with detailed headers. For consistency and clarity, these columns were renamed during the data cleaning process. Below are the original column names and their corresponding transformed names:
1.	Customer → Customer_ID
2.	How satisfied were you with your overall delivery experience at Ali? → Delivery_Experience
3.	How satisfied were you with the quality of food at Alis? → Food_Quality
4.	How satisfied were you with the speed of delivery at Alis? → Delivery_Speed (originally renamed as Time, but revised for better clarity)
5.	Was your order accurate? Please respond Yes or No → Correct_Order
These transformations standardized the column names, making them easier to reference throughout the analysis.


### Column Descriptions / Data Dictionary

1.	Customer_ID: A unique identifier for each customer.
2.	Delivery_Experience: Customer's rating on a scale of 1 to 5 for their delivery experience.
3.	Food_Quality: Customer's rating on a scale of 1 to 5 for the quality of the food.
4.	Delivery_Speed: Customer's rating on a scale of 1 to 5 for the delivery speed.
5.	Correct_Order: Indicates whether the customer's order was accurate, with responses recorded as Yes or No.

### Rating Scale Interpretation

For the Delivery_Experience, Food_Quality, and Delivery_Speed columns, customer ratings are measured on a 1 to 5 scale:
•	1 – Extremely Dissatisfied
•	2 – Dissatisfied
•	3 – Neutral
•	4 – Satisfied
•	5 – Extremely Satisfied
Only ratings 1 and 5 were explicitly defined in the original dataset. Ratings 2, 3, and 4 were introduced during the analysis to provide a more detailed breakdown of customer sentiment.

## Tools
**Power BI:** Creating DAX measures, and visualizing insights.
**Power Query:** Data cleaning ,  transformation, and creating custom columns




