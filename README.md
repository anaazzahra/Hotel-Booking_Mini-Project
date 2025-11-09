# Hotel Business Performance Analysis (2017–2019)
This project is data visualization task using python, but I finished this task with Python (data preparation + cleaning + prediction "is_canceled" + Visualization), looker studio (visualization), Ms. Excel (data cleaning + visualization). This is my mini project during my bootcamp at Rakamin Academy.

#Work Environment:




<img width="80" height="80" alt="image" src="https://github.com/user-attachments/assets/0b9093d1-ea31-49b4-a751-da37f0bbd950" /> <img width="80" height="80" alt="image" src="https://github.com/user-attachments/assets/70105574-1eab-4778-888e-177afa1dcfd9" />     <img width="80" height="80" alt="image" src="https://github.com/user-attachments/assets/0cee50c6-ce78-4bb4-bac0-f5556a25576a" />


Google Colab (Syntax and Code): https://colab.research.google.com/drive/1W2_IRFhuaVmxt5dt_4B8XWRdZvvodHe6?usp=sharing

Looker studio: https://lookerstudio.google.com/reporting/96b13104-5e3f-47a6-a3ba-7bfd69544b00


# Project Recap
This project is an initiative to support the management of Company X, which operates in the property sector, specifically in managing its hotel units: the City Hotel and the Resort Hotel.

For strategic planning and operational optimization, management required a comprehensive review of business performance over a three-year period: 2017, 2018, and 2019. The primary focus of the analysis is to identify trends, risks, and opportunities to enhance revenue and customer loyalty

# Business Objectives
This analysis aims to answer three key business questions:

1. Volume & Trend: How did total bookings, cancellations (cancel), and repeat bookings move on a monthly basis throughout the 2017–2019 period?

2. Cancellation Risk: What factors most significantly influence the high Cancellation Rate (Cancel Rate)? (e.g., Lead Time, Customer Type, or Market Segment).

3. Customer Loyalty: What booking characteristics drive guests to become repeat customers (Repeated Guest), and how can we leverage this to improve loyalty?

# Process Flow (Python + Looker)
## 1. Data Understanding
  All data sourced from Rakamin Academy. There is one table in CSV form, namely hotel_booking_data. There are 19 columns and 119390 entries. There are four data type, such as float, int, string/object, and boolean (is_cancelled and is_repeated column). Checking descriptive statistics to see the trend and pattern of the data, and also display unique value. 

## 2. Data Cleaning
  Data integrity was established by removing 33,223 duplicate entries. Missing values were managed by deleting affected rows in the 'city' column and imputing zero (0) into the numerical fields: 'children', 'agent', and 'company'. Extreme values in 'lead_time' and 'waiting_list' were kept as valid data points, with the understanding that robust analytical methods are required for accurate predictive modeling.

## 3. Predictive Modeling and Evaluation
  Beyond exploratory data analysis (EDA), a predictive model was built to identify which factors best predict whether a customer will cancel a booking.

  Feature Selection and Model Choice:
  1. Feature Engineering and Selection
     - Goal: To determine the optimal set of features for predicting the target variable: is_canceled.
     - Methodology: Feature selection was primarily conducted using a Heatmap analysis to visualize correlations between variables. Features exhibiting extremely high correlation (multicollinearity) were excluded to prevent model instability.
     - Exclusions: All personally identifiable information (PII) and date-related columns (as the date group feature was used for time series analysis) were excluded from the final training set
  2. Model Selection
     - Target Variable: is_canceled (A binary classification task: 0 = Not Canceled, 1 = Canceled).
     - Model: The Random Forest Classifier was selected for this task. This model was chosen specifically for its robustness to outliers (which were present in variables like lead_time and waiting_list), its ability to handle non-linear relationships, and its strong performance in imbalanced classification problems. 
 
Model Evaluation:
The model achieved an overall Accuracy of 80.15%. However, a detailed look at the Classification Report reveals nuances in its performance, particularly concerning the minority class (Canceled bookings, class 1).
<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/10d51503-01ce-4d52-acf4-1b9fe925dd25" />


# Visualization Feature Importance + Evaluation + Looker
<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/ab28841a-3197-4e84-bab6-bde3052ea2a4" />
<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/fce43d43-9867-4bf7-80d5-6a728b6d7063" />
<img width="663" height="797" alt="image" src="https://github.com/user-attachments/assets/405f2cbb-3403-457f-a05c-5b2b80315c6f" />





# Data Problem Statement (tool: MS. Excel)
The raw data provided for this analysis includes over 85,000 rows of booking transactions spanning three years. The sheer volume of this data presents significant challenges during the pre-processing stage:

1. Date Data Fragmentation: Arrival date information was split into three separate columns (arrival_date_year, arrival_date_month, arrival_date_day_of_month), requiring accurate merging (concatenation) and data type conversion to be analyzed as a valid time series in Excel.
2. Data Quality (Missing Values & Inconsistency): Missing values were found scattered across critical columns (such as city, company, and several numerical columns), as well as inconsistent categorical values (e.g., 'Undefined' or blank cells).
3. Tool Limitation: The project must be executed using Microsoft Excel, which necessitates efficient data cleaning and analysis techniques (such as Go To Special, Text to Columns, and PivotTable features) to process this volume of data without crashing and to produce responsive output.

# Methodology and Key Metrics
<img width="500" height="672" alt="image" src="https://github.com/user-attachments/assets/0810db84-68fe-40b0-ac6a-5a4a9e590cbf" />

# Dashboard using Ms.Excel
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/2c288531-951b-43f7-bca6-8fefe74885d9" />

# Conclusion and Actionable Business Recommendations
1. Strategic Business Actions
   - Lead Time Risk Mitigation (Factor No. 1): Implement stricter deposit policies (non-refundable) or launch targeted re-confirmation campaigns for bookings with very long lead times (>180 days).
   - Pricing & Commitment Strategy (ADR, Factor No. 2): Avoid offering large ADR discounts without a high commitment guarantee (e.g., non-refundable or high deposit).
   - Agent Performance Management (Factor No. 3): Identify and renegotiate contracts with agents that have the highest cancellation rates.
  
2. Data Science Recommendations
   - Prioritize Recall: Conduct hyperparameter tuning and adjust the model's decision threshold to increase Recall (minimizing losses from missed cancellations).
   - Address Data Imbalance: Explore over-sampling techniques like SMOTE to make the model more sensitive to the characteristics of the cancellation class (minority).



