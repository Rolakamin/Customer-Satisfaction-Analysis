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
- What is the distribution of customer responses regarding order accuracy?
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

![Delivery Experience Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/delivery_experience.png)

![Delivery Experience Count Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/delivery_experience_count.png)

![Delivery Experience Count Sorted Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/delivery_experience_%20sorted%20descending.png
)

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

![Overall Satisfaction Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/overall_satisfaction.png)

![Delivery Experience Category Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/deliver_experience_category.png
 )

 ![Food Quality Category Screenshot](https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/food_quality_category.png)

![Delivery Speed Category Screenshot]( https://github.com/Rolakamin/Customer-Satisfaction-Analysis/blob/main/delivery_speed_category.png
)


## Data Analysis and Visualization

### DAX Measures

To facilitate detailed analysis, the following DAX measures were created:

1. Total Responses - Count of unique customer survey responses.
   
```DAX
Total Responses = DISTINCTCOUNT(Customer_survey_data[Customer_ID])
```

2. Average Ratings - Mean values for Delivery Experience, Food Quality, and Delivery Speed.

 ```DAX
Avg Delivery Experience = AVERAGE(Customer_survey_data[Delivery_Experience])
```

 ```DAX
Avg Food Quality = AVERAGE(Customer_survey_data[Food_Quality])
```

 ```DAX
Avg Delivery Speed = AVERAGE(Customer_survey_data[Delivery_Speed])
```

3. Correct Order % - Percentage of accurately fulfilled orders.

 ```DAX
   Correct Order % = 
DIVIDE(
    COUNTAX(
        FILTER(Customer_survey_data, Customer_survey_data[Correct_Order] = "Yes"), 
        1
    ),
    [Total Responses],
    0
)
```

4.	Dissatisfied Customers - Count of customers who reported dissatisfaction.

 ```DAX
Dissatisfied Customers = 
CALCULATE(
    COUNT(Customer_survey_data[Customer_ID]), 
    Customer_survey_data[Overall_Satisfaction] = "Not Satisfied"
)
```

5. Satisfied Customers - Count of customers who reported satisfaction

 ```DAX
 Satisfied Customers = 
CALCULATE(
    COUNT(Customer_survey_data[Customer_ID]),
    Customer_survey_data[Overall_Satisfaction] = "Satisfied"
)
```

6. No Response Count - Number of customers who did not provide order accuracy feedback.

 ```DAX
No Response Count = 
CALCULATE(
    COUNT(Customer_survey_data[Customer_ID]), 
    FILTER(Customer_survey_data, Customer_survey_data[Correct_Order] = "No Response")
)
```

7.	Satisfaction Rate (%) - Percentage of satisfied customers.

 ```DAX
Satisfaction Rate % = 
DIVIDE([Satisfied Customers], [Total Responses], 0)
```

8. Net Satisfaction Score (NSS) - Difference between satisfied and dissatisfied customers as a percentage of total responses.

```DAX
Net Satisfaction Score (NSS) = 
DIVIDE(
    [Satisfied Customers] - [Dissatisfied Customers], 
    [Total Responses], 
    0
)
```

### Service_Attribute_Table and Avg_Service_Attribute

In addition to the above measures, a dynamic method was implemented for analyzing customer satisfaction across key service attributes such as Delivery Experience, Food Quality, and Delivery Speed.
A new table, **Service_Attribute_Table** was created to simplify the analysis and allow for easy comparison.This table was manually created using a Service Attribute column and holds the three key service attributes: Delivery Experience, Food Quality, and Delivery Speed.The table was then used to dynamically filter and calculate average ratings for each attribute.

**DAX Formula for creating Service_Attribute_Table:**

 ```DAX
 Service_Attribute_Table = 
DATATABLE("Service Attribute", STRING, { 
    {"Delivery Experience"},
    {"Food Quality"},
    {"Delivery Speed"}
})
```

The **Avg_Service_Attribute** measure was also created to calculate the average rating dynamically.The measure uses the **SWITCH function** to return the appropriate average rating for either Delivery Experience, Food Quality, or Delivery Speed.It was utilized in the visual to dynamically display the average ratings for each service attribute when selected, providing a clear view of customer satisfaction with each aspect of the service.

**DAX Formula for Avg_Service_Attribute:**

 ```DAX
Avg_Service_Attribute = 
SWITCH(
    SELECTEDVALUE(Service_Attribute_Table[Service Attribute]),
    "Delivery Experience", [Avg Delivery Experience],
    "Delivery Speed", [Avg Delivery Speed],
    "Food Quality", [Avg Food Quality]
)
```



### Data Visualization

The customer satisfaction survey data was analyzed using Power BI and presented in a single-page dashboard. This dashboard offers comprehensive insights into customer ratings, satisfaction levels, and key service factors influencing the overall experience. It features interactive visuals that allow stakeholders to explore metrics such as satisfaction rates, net satisfaction scores, average service ratings, and order accuracy distributions.
You can view the dashboard [here](https://github.com/Rolakamin/Adidas-Sales-Analysis/blob/main/adidas_sales_dashboard%20.png)

### Results & Findings

- Only 29.77% of customers reported being satisfied. This indicates a substantial opportunity for service improvement.
- The Net Satisfaction Score (NSS) stood at -40.47%. This reveals that dissatisfaction outweighed satisfaction among customers.
- The average ratings for Delivery Experience (3.39), Food Quality (3.37), and Delivery Speed (3.36) suggest that customers had a neutral experience overall, with none of the categories excelling.
- 66.98% of customers received accurate orders and 26.8% experienced inaccuracies,highlighting a key area needing attention.

### Recommendations

- Out of 10,616 total responses, 660 customers provided no answers. Though a small portion, it's important to investigate the cause which could be due to survey fatigue, unclear questions or repetitive 
  questions. Consider simplifying the feedback form or ensuring the length and tone encourage completion.
- Strive to gather full responses by communicating the value of feedback to customers and possibly offering incentives. This ensures more comprehensive insights and reduces analysis bias.
- Enhance customer satisfaction by focusing on reducing **Order Inaccuracies** through improved quality checks and regular staff training. In addition,boost **Delivery Speed** and improve **Food Quality** by 
  reviewing operational workflows and investing in logistics or food preparation standards.
- Establish a routine for analyzing customer feedback.This allows the business to quickly spot trends and proactively address areas needing improvement.

### 

1. The dataset included 660 non-responses(6.2%) out of 10,616 total responses. This non-response rate introduced potential bias, as the characteristics and opinions of non-respondents may have differed 
   systematically from those who participated. Such discrepancies could have affected the representativeness of the results, potentially skewing the overall understanding of customer satisfaction.
   
2. The dataset lacked timestamps or defined time periods for the survey responses. This absence made it impossible to analyze trends over time, such as monthly improvements or seasonal fluctuations. 
   Consequently, the analysis could not assess progress or identify time-based patterns in customer satisfaction.

3. The dataset did not contain information on customer demographics or specific order details. This limitation restricted the ability to compare characteristics between respondents and non-respondents, making it 
   challenging to identify any existing patterns or biases in response behavior.

   These limitations highlight areas for improvement in future data collection efforts to enhance the depth and accuracy of customer satisfaction analyses.​















  










