# Zomato Restaurant Performance & Market Insights Dashboard

## Project Description
This project delivers an end-to-end analytical solution to evaluate **restaurant performance, customer preferences, and market trends** using a publicly available **Zomato restaurant dataset**. The objective is to transform raw restaurant-level data into meaningful insights that support **data-driven decision-making** for platform strategy, restaurant onboarding, and service optimization.

The analysis was conducted using **SQL for data exploration and aggregation** and **Power BI for interactive visualization**. Key performance dimensions such as **customer ratings, votes, pricing, cuisine types, online delivery adoption, and table booking availability** were examined to understand their impact on customer engagement and satisfaction across multiple cities.

---

## Problem Statement
Food delivery platforms handle large volumes of restaurant and customer interaction data. However, identifying:
- High-performing cities and cuisines  
- Optimal pricing segments  
- The impact of online delivery and table booking on engagement  

requires structured analysis and clear visualization.  
This project addresses these challenges by building a **centralized analytics dashboard** that provides actionable insights into restaurant performance and market behavior.

---

## Tools & Technologies
- **SQL** – Data cleaning, aggregation, CTEs, window functions  
- **Power BI** – Interactive dashboards, KPIs, slicers, and visuals  
- **Excel / CSV** – Source dataset  

---

## Dataset Overview
The dataset contains restaurant-level information including:

- Restaurant Name & ID  
- City & Country Code  
- Cuisines  
- Average Cost for Two  
- Price Range  
- Aggregate Rating & Rating Text  
- Number of Votes  
- Online Delivery Availability  
- Table Booking Availability  
- Latitude & Longitude  

> **Disclaimer:** This dataset is publicly available and used strictly for educational and portfolio purposes. No proprietary or confidential data is included.

---

## SQL Analysis Approach
SQL was used to perform structured analysis across multiple dimensions:

- **City-level analysis** to identify restaurant density and performance
- **Cuisine-level aggregation** to understand popularity and customer satisfaction
- **Rating and vote analysis** to eliminate bias from low-engagement restaurants
- **Pricing segmentation** to evaluate cost vs rating relationships
- **Service adoption analysis** to assess the impact of online delivery and table booking

The results of these queries directly power the visuals and KPIs in the Power BI dashboard.

---

## Sample SQL Queries

### Restaurant Distribution by City
```sql
SELECT 
    city,
    COUNT(*) AS total_restaurants
FROM zomato_restaurants
GROUP BY city
ORDER BY total_restaurants DESC;
```
### Average Rating & Engagement by City
```sql
SELECT 
    city,
    ROUND(AVG(aggregate_rating), 2) AS avg_rating,
    SUM(votes) AS total_votes
FROM zomato_restaurants
GROUP BY city
ORDER BY avg_rating DESC;
```

### Top Rated Restaurants (Vote Filter Applied)
```sql
SELECT 
    restaurant_name,
    city,
    aggregate_rating,
    votes
FROM zomato_restaurants
WHERE votes >= 200
ORDER BY aggregate_rating DESC
LIMIT 10;
```

### Cuisine Popularity & Performance
```sql
SELECT 
    cuisines,
    COUNT(*) AS restaurant_count,
    ROUND(AVG(aggregate_rating), 2) AS avg_rating
FROM zomato_restaurants
GROUP BY cuisines
ORDER BY restaurant_count DESC;
```

### DASHBOARD

<img width="1013" height="565" alt="image" src="https://github.com/user-attachments/assets/ad49aba9-5004-46e6-9af2-a668c6625d99" />

<img width="1018" height="570" alt="image" src="https://github.com/user-attachments/assets/92bdb60a-3ed0-43cc-8c14-13e345fdfdbc" />

<img width="1015" height="570" alt="image" src="https://github.com/user-attachments/assets/70dad4c4-8aeb-4305-afcb-62864f3861b7" />

<img width="1015" height="572" alt="image" src="https://github.com/user-attachments/assets/b19adf6e-67c3-48df-8546-f36593d94397" />


