# foodpanda-sql
End-to-end Customer Behavior Analysis project using PostgreSQL, Python, and Power BI on the Foodpanda dataset. Features RFM scores, churn rate calculation, retention analysis, and performance metrics. Demonstrates identifying high-churn segments, improving retention strategies, and optimizing platform efficiency for better customer engagement.

# FoodPanda Customer Behaviour Analysis

## *Data-Driven Customer Behaviour Analytics for Food Delivery Platforms*

# Executive Summary 
This project applies advanced customer analytics to the Foodpanda dataset, uncovering opportunities to reduce churn, improve retention, and optimize platform performance. The analysis utilizes DuckDB (in Colab), Python, and Power BI to create a framework for RFM scoring, churn calculation, retention proxy, and performance KPIs. The goal was to demonstrate how quantitative insights can identify at-risk segments, enhance engagement, and boost revenue, making it applicable to real-world platforms like Foodpanda.

# Problem Statement
Food delivery platforms lose billions annually due to high churn: users sign up but don't return, low retention erodes loyalty, and poor performance (e.g., delays) drives cancellations. The challenge is to answer: Which segments churn most? How to measure retention without repeat data? What factors (ratings, delivery) impact performance? This project uses the Foodpanda dataset to simulate these with data-backed solutions.

# Data Sources and Engineering

## Data Sources

- [FoodPanda Analysis Dataset](https://github.com/aarushijain16/foodpanda-sql/blob/main/Foodpanda%20Analysis%20Dataset.csv) : Core dataset with ~6k orders across 5 cities, demographics, and transaction details.

- Files derived from Python cleaning and Clustering:

  - [Islamabad Data](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_data.csv)
 
  - [Karachi Data](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_data.csv)
 
  - [Multan Data](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_data.csv)
 
  - [Lahore Data](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_data.csv)
 
  - [Peshawar Data](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_data.csv)

- Files derived from SQL Queries:

  - [Islamabad Churn by Demographics](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_churn_by_demo.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_churn_by_demo.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_churn_by_demo.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_churn_by_demo.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_churn_by_demo.csv))
 
  - [Islamabad Churn by Features](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_churn_by_features.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_churn_by_features.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_churn_by_features.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_churn_by_features.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_churn_by_features.csv))
 
  - [Islamabad Churn by RFM](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_churn_by_rfm.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_churn_by_rfm.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_churn_by_rfm.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_churn_by_rfm.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_churn_by_rfm.csv))
 
  - [Islamabad Retention by Demographics](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_retention_by_demo.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_retention_by_demo.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_retention_by_demo.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_retention_by_demo.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_retention_by_demo.csv))
 
  - [Islamabad Retention by Features](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_retention_by_features.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_retention_by_features.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_retention_by_features.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_retention_by_features.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_retention_by_features.csv))
 
  - [Islamabad Retention by RFM](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_retention_by_rfm.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_retention_by_rfm.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_retention_by_rfm.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_retention_by_rfm.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_retention_by_rfm.csv))
 
  - [Islamabad Performance Overall](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_performance.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_performance.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_performance.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_performance.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_performance.csv))
 
  - [Islamabad Performance by Restaurants](https://github.com/aarushijain16/foodpanda-sql/blob/main/Islamabad_performance_by_restaurant.csv) ( and similar for [Karachi](https://github.com/aarushijain16/foodpanda-sql/blob/main/Karachi_performance_by_restaurant.csv), [Lahore](https://github.com/aarushijain16/foodpanda-sql/blob/main/Lahore_performance_by_restaurant.csv), [Multan](https://github.com/aarushijain16/foodpanda-sql/blob/main/Multan_performance_by_restaurant.csv) and [Peshawar](https://github.com/aarushijain16/foodpanda-sql/blob/main/Peshawar_performance_by_restaurant.csv))
 
  - [Churn by City](https://github.com/aarushijain16/foodpanda-sql/blob/main/churn_by_city.csv)
 
  - [Retention by City](https://github.com/aarushijain16/foodpanda-sql/blob/main/retention_by_city.csv)
 
  - [Overall Churn Rate](https://github.com/aarushijain16/foodpanda-sql/blob/main/overall_churn.csv)
 
  - [Overall Retention Rate](https://github.com/aarushijain16/foodpanda-sql/blob/main/overall_retention.csv)

- Files Derived for BI Visualization:

  - [Combined Churn By Demoraphics](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_churn_by_demo.csv) ( and similar for [Features](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_churn_by_features.csv) and [RFM](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_churn_by_rfm.csv))
 
  - [Combined Retention by Demographics](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_retention_by_demo.csv) ( and similar for [Features](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_retention_by_features.csv) and [RFM](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_retention_by_rfm.csv))
 
  - [Combined Performance Overall](https://github.com/aarushijain16/foodpanda-sql/blob/main/performance_overall.csv)
 
  - [Combined Performance by Restaurants](https://github.com/aarushijain16/foodpanda-sql/blob/main/combined_performance_rest_df.csv)
 
## Engineering

- Started with the FoodPanda dataset in Python (Pandas), performed cleaning (whitespace removal, date formatting, duplicates/nulls/outliers handling, inconsistency checks).

- Conducted EDA (descriptive statistics, unique/values counts, distributions/visualisations, correlations, derived metrics).

- Calculated RFM scores per customer (recency from last_order_date, frequency from order_frequency, monetary from sum order_value).

- Clustered customers on RFM scores (KMeans for 3 clusters), then layered city for analysis.

- Saved city-wise files with all details + RFM columns for granular SQL queries.

- Performed churn, retention (proxy), and performance analysis in SQL on city files.

- Combined SQL results in Python for visualisation convenience in Power BI.

## Methodology

- **Data Preparation and Schema :** Built city-wise files in Python, queried using DuckDB in Colab for analysis.

- **RFM Scoring :** Calculated recency, frequency, monetary per customer in Python.

- **Churn Analysis :** Rates overall, by RFM, city, demographics, features in SQL.

- **Retention Analysis :** Proxy using order_frequency, rates overall, segmented by RFM, city, demographics, features in SQL.

- **Performance Analysis :** KPIs like revenue, AOV, ratings, delivery success, segmented by restaurant/category/status in SQL.

- **Visualisation and Reporting :** Synthesized insights into a 4-page Power BI dashboard, bridging analytics and business decisions.

# Key Findings

## *From Delivery Insights to FoodPanda Opportunities*

| **Analytical Lens** | **Key Finding** | **Strategic Relevance** | **Estimated Impact** |
|:-------------------:|:---------------:|:-----------------------:|:--------------------:|
| **RFM Scoring** | Low RFM (3–5): 85–94% retention; High RFM (13–15): 100% retention | Prioritize high-RFM loyalty; low-RFM shows 45–60% churn | $10–20M from targeted retention |
| **Churn by City** | Lahore highest churn (51.85%); Peshawar lowest (47.87%) | Tailor campaigns to high-churn cities | $5–15M from reduced churn |
| **Churn by Demographics** | Adult/Male highest (52.55%); Senior/Male lowest (46.03%) | Segment-specific engagement strategies | $3–10M from targeted engagement |
| **Churn by Features** | High rating & delayed: 57.5% churn; Low rating & cancelled: 44.73% | Improve delivery reliability for high-rating orders | $10–20M from lower cancellations |
| **Retention Proxy** | Overall retention 98.02%; Peshawar highest (98.49%) | Use order frequency to define loyalty tiers | $15–30M from re-engagement |
| **Retention by RFM** | High RFM (13–15): 100% repeat; Low RFM (3–5): 85–94% repeat | Incentivize low-RFM customers | $5–15M annual uplift |
| **Performance KPIs** | Revenue $2.8M (Islamabad); AOV $2,389; Avg rating 1.71 | Optimize high-AOV cuisines like Italian | $20–45M growth |
| **Delivery Success** | 34.29% on-time (Islamabad); 32.77% cancelled | Reduce cancellations in low-rating deliveries | $10–25M saved in lost sales |
| **Top Restaurants** | KFC highest revenue ($679K), avg rating 1.80 | Partner with top performers for exclusive promotions | $5–15M from strategic partnerships |

# Strategic Recommendations

| **Area** | **Recommendation** | **Expected Outcome** | **Implementation Timeline** |
|:--------:|:------------------:|:--------------------:|:---------------------------:|
| **RFM Scoring** | Implement RFM-based segmentation for personalized emails; reward high-RFM customers with discounts | Reduced churn in low-RFM segments; $10–20M uplift | 1–3 months |
| **Churn Reduction** | Analyze high-churn demographics (Adult/Male) and deploy targeted offers | $5–15M from lower churn | Immediate |
| **Retention Proxy** | Use frequency proxy for loyalty tiers; re-engage low-frequency users with promotions | $3–10M from improved retention | 1 month |
| **Delivery Performance** | Prioritize on-time delivery for high-rating orders; identify root causes of cancellations | $10–20M recovered revenue | 1–2 months |
| **Performance Optimization** | Launch exclusive deals with top restaurants (e.g., KFC); optimize low-AOV categories | 20–30% growth in high-value segments | Immediate |
| **Overall** | Integrate all insights into Power BI dashboards for weekly monitoring | $25–60M total annual impact | Ongoing |

# Tools and Technologies
| **Category** | **Tools / Libraries** |
|:------------:|:---------------------:|
| **Programming** | Python (Pandas, Scikit-learn) |
| **Database & SQL** | DuckDB (in Google Colab) |
| **Visualization** | Power BI |
| **Modeling** | SQL (aggregations) |

# Link to Dataset, Code and Power BI Dashboard

- [Dataset](https://github.com/aarushijain16/foodpanda-sql/blob/main/Foodpanda%20Analysis%20Dataset.csv)

- [Code (Python and SQL)](https://github.com/aarushijain16/foodpanda-sql/blob/main/Foodpanda.ipynb)

- [Power BI Dashboard](https://github.com/aarushijain16/foodpanda-sql/blob/main/BI.pdf)

*Note :* This project uses publicly available Foodpanda dataset, allowing for full responsibility of the analysis.

# Final Note

This project showcases how data analytics can transform food delivery customer behavior from a retention challenge to a growth driver. By integrating SQL, Python, and Power BI, it provides actionable insights for reducing churn, boosting retention, and optimizing performance- skills directly applicable to roles in customer analytics.

