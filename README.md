# Dynamic Pricing Model for a Ride-Sharing Service

## Project Overview
This project focuses on developing a dynamic pricing model for a ride-sharing service. The primary goal is to optimize ride costs in real-time by balancing supply and demand, thereby maximizing profitability while maintaining customer satisfaction. The project begins with a thorough data analysis to understand key factors influencing ride costs, followed by the implementation of a rule-based pricing strategy, and culminates in the development of a predictive machine learning model to forecast optimal prices.

## Problem Statement
Traditional, static pricing models in the ride-sharing industry often fail to account for real-time market conditions. This can lead to a supply-and-demand imbalance, resulting in either lost revenue during peak demand or a low number of rides during off-peak hours.  
**The challenge** is to create a dynamic pricing system that can intelligently adjust prices based on factors such as rider demand, driver supply, location, and other key variables to ensure profitability and efficiency.

## Project Objectives
- **Data Exploration and Analysis**: Analyze historical ride data to identify key variables and their relationships.  
- **Feature Engineering**: Create demand and supply multipliers to quantify market conditions.  
- **Rule-Based Dynamic Pricing**: Implement a rule-based pricing model to adjust historical costs based on engineered features.  
- **Model Building**: Develop a machine learning model (Random Forest Regressor) to predict optimal ride costs with high accuracy.  
- **Model Evaluation**: Validate the performance of the model using visual and statistical methods.  
- **Deployment Simulation**: Create a function to simulate real-world price predictions using the trained model.  

## Data Dictionary
The project utilizes a dataset named **dynamic_pricing.csv**. Below is a dictionary explaining each column:

| Column Name              | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Number_of_Riders         | The number of customers requesting a ride at a specific time.             |
| Number_of_Drivers        | The number of available drivers in the area.                               |
| Location_Category        | The geographic location of the ride request (e.g., 'Urban', 'Suburban', 'Rural'). |
| Customer_Loyalty_Status  | The loyalty status of the rider (e.g., 'Regular', 'Silver', 'Gold').       |
| Number_of_Past_Rides     | The total number of rides a customer has taken.                           |
| Average_Ratings          | The average rating of the driver for the ride.                             |
| Time_of_Booking          | The time of day the booking was made (e.g., 'Morning', 'Afternoon', 'Evening', 'Night'). |
| Vehicle_Type             | The type of vehicle requested ('Premium' or 'Economy').                   |
| Expected_Ride_Duration   | The anticipated duration of the ride in minutes.                           |
| Historical_Cost_of_Ride  | The original cost of the ride based on a static pricing model.             |
| adjusted_ride_cost       | The new, dynamically calculated cost of the ride.                          |
| profit_percentage        | The percentage change between the adjusted and historical cost.            |

## Key Insights and Analysis

### 1. Descriptive Statistics
- **Supply-Demand Imbalance**: The average number of riders (60.37) is more than double the average number of drivers (27.08). This highlights the need for a pricing model that can respond to this market gap.  
- **Customer Base**: The dataset includes a mix of new and loyal customers, as indicated by the wide range in `Number_of_Past_Rides`.  
- **High Ratings**: Drivers maintain a high average rating of approximately 4.26, suggesting a quality service.  

### 2. Correlation Analysis
- **Strongest Predictor**: `Expected_Ride_Duration` is the most significant factor in determining the `Historical_Cost_of_Ride`, with a strong positive linear relationship.  
- **Market Dynamics**: A notable negative correlation was found between `Number_of_Riders` and `Number_of_Drivers`, reinforcing the supply-demand imbalance problem.  
- **Weak Predictors**: Variables like `Number_of_Past_Rides` and `Average_Ratings` were found to have a weak correlation with the ride cost.  

### 3. Rule-Based Dynamic Pricing
- A rule-based model was implemented using demand and supply multipliers based on percentile values.  
- **Profitability**: The dynamic pricing strategy proved highly effective, with **82.7%** of rides becoming profitable after the price adjustment. Only **17.3%** of rides saw a price reduction, indicating the model successfully optimizes for revenue without overly aggressive price cuts.  
- **Price Variance**: A scatter plot comparing `Expected_Ride_Duration` to the `adjusted_ride_cost` showed a wider variance in pricing for a given duration compared to the historical cost. This demonstrates the model's ability to factor in market conditions beyond just time and distance.  

### 4. Predictive Machine Learning Model
- A **Random Forest Regressor** was chosen to build a more advanced pricing model.  
- The model was trained on key features including `Number_of_Riders`, `Number_of_Drivers`, `Vehicle_Type`, and `Expected_Ride_Duration`.  
- **High Accuracy**: A final evaluation plot of "Actual vs. Predicted Values" showed that the model's predictions are tightly clustered around the ideal diagonal line, confirming that the model has high predictive accuracy and can be reliably used for real-time pricing.  

## Conclusion
This project successfully demonstrates a comprehensive approach to dynamic pricing.  
By first analyzing the data, implementing a robust rule-based model to address key market dynamics, and finally developing a highly accurate predictive machine learning model, a powerful system has been created.  

The results indicate that the dynamic pricing strategy is both **effective** and **profitable**, making it a valuable asset for any ride-sharing service aiming to optimize its operations and revenue.
