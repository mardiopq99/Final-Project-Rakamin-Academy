# Project : E-Commerce Sales Analysis

# Introduction

This project aims to explore and analyze sales data from an e-commerce company using Exploratory Data Analysis (EDA). The main objectives of EDA are:
- Extract initial insights and identify patterns or trends.
- Understand variable relationships to guide further analysis or modeling.
EDA provides a foundation for business recommendations based on observed insights.

# Dataset Overview

The dataset contains 128,975 rows and key columns, including:
- Order ID: Unique ID for each order.
- Date: Order date.
- Fulfillment: Indicates whether orders were fulfilled by Amazon or other merchants.
- Sales Channel: Platform used for transactions.
- Category: Product category (e.g., Kurta, Saree).
- Size: Product size.
- Qty: Quantity ordered.
- Order Price: Total order price.
- Ship Service Level: Shipping speed (e.g., expedited, standard).
- Status: Order status (e.g., shipped, returned, canceled).

# Summary of Insights from EDA

1. Unique Order ID: The dataset includes 120,378 unique Order IDs, indicating multiple items per order.
2. Peak Order Frequency: A significant spike in order frequency occurred in early May 2022.
3. Distribution of Quantity and Price:
   - Most quantities are centered around 1.
   - Order prices approximate a normal distribution.
4. Fulfillment by Amazon: Orders fulfilled by Amazon dominate, showing reliance on Amazon's logistics.
5. Amazon.in Dominance: Amazon.in is the primary sales platform, indicating its effectiveness.
6. B2C Transactions: Most transactions are Business-to-Consumer (B2C), focusing on retail sales.
7. Popular Product Categories: "Set" and "Kurta" are the most ordered categories, with nearly 10,000 entries.
8. Preferred Shipping Level: Expedited shipping is more popular than standard.
9. Most Ordered Sizes: Sizes M, L, and XL dominate orders.
10. Weak Correlation Between Quantity and Price: Quantity and Order Price have a low correlation (0.07).
11. Successful Deliveries by Size: Most items in sizes M, L, XL, XXL, S, and XS are delivered successfully.
12. High Average Price Categories: "Set," "Saree," and "Western Dress" have the highest average order prices.
13. Top Regions: Maharashtra and Karnataka have the highest order volumes.

# Data Preprocessing for Amazon Sales Dataset

## Dataset Description
The dataset covers sales transactions on Amazon, including columns such as Date, Status, Category, Qty, and Amount. Preprocessing was conducted to clean, transform, and enhance data quality.

## Preprocessing Steps

### 1. Handling Missing Values
- Dropped columns with high missing values:
  - Courier Status, currency, Amount, ship-city, ship-state, ship-postal-code, ship-country, promotion-ids, fulfilled-by, Unnamed: 22.

### 2. Data Type Adjustments
- Converted Date to datetime.
- Converted B2B to numeric.

### 3. Duplicate Removal
- Removed duplicate rows for uniqueness.

### 4. Outlier Handling
- Applied log transformations to highly skewed columns:
  - Qty → Qty_log
  - Amount → Amount_log

### 5. Feature Encoding
- Ordinal Encoding:
  - Mapped Size values (e.g., XS, S, M, L) to numeric levels.
- One-Hot Encoding:
  - Encoded Category and Region columns.
- Geographical Mapping:
  - Mapped ship-state into geographic regions (e.g., North, South).

### 6. Class Imbalance Handling
- Mapped Status into numeric labels:
  - Shipped - Delivered to Buyer → 3
  - Shipped - Returned to Seller → 2
  - Shipped - Rejected by Buyer → 1
- Balanced class distribution using SMOTE.

### 7. Feature Engineering
- Added date-related features:
  - Day (numeric day in the month).
  - Day_Type ("Weekday" or "Weekend").
- Added binary indicator:
  - Is_Weekend (1 for weekends, 0 for weekdays).

### 8. Feature Selection
- Dropped irrelevant or redundant columns:
  - index, ship-postal-code, Sales Channel, Status.

# Additional Project Information

## Execution Process
The project followed these main stages:
1. **Data Collection and Exploration**: Data was sourced from the e-commerce company's logistics system and explored for patterns and distributions.
2. **Data Preprocessing**:
   - Missing Values: Filled missing data based on patterns or averages.
   - Encoding: Applied techniques like One-Hot Encoding and Label Encoding.
   - Normalization: Ensured consistent scaling of numeric features.
3. **Feature Engineering**: Created new features, such as weekday/weekend indicators, to assess delivery effectiveness.
4. **Modeling**:
   - Algorithms: Logistic Regression, kNN, Random Forest, and XGBoost.
5. **Team Collaboration and Tools**:
   - Tools: Google Colab, Jupyter Notebook.
   - Libraries: Pandas, Scikit-learn.

## Challenges Faced
- **Team Communication**: Busy schedules among team members were managed with scheduled meetings and group chats.
- **Numerical Data Limitations**: Addressed through feature engineering to add new information.

## Key Outcomes
- **Model Performance**: XGBoost achieved a recall of 85%.
- **Feature Importance**:
   - Regions (South and West) significantly influenced shipment status predictions.
   - Product categories and delivery timing (weekends) were also impactful.
- **Business Impact**:
   - Proactive handling of returns reduced lost sales by 15%.
   - Predictions enabled early notifications to sellers.

## Recommendations
1. **Regional Focus**: Optimize logistics in high-return regions (South, West).
2. **Product Categories**: Improve descriptions, size guides, and visuals for high-return categories.
3. **Delivery Scheduling**: Avoid weekend deliveries to reduce return risks.
4. **Customer Education**: Conduct campaigns to enhance understanding of shipping and return processes.

