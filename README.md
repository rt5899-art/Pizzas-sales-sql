# Project Overview
The SQL Pizza Sales Analysis Project is a comprehensive data analysis initiative designed to extract actionable business insights from transactional data of a pizza store. By leveraging structured relational database concepts, the project transforms raw data into answers for critical operational questions—such as tracking sales trends, understanding customer ordering behaviors, evaluating pizza popularity, and monitoring revenue generation. 
The analysis operates across four core database tables:
##### orders:
Captures high-level order information including dates and times.  
##### order_details: 
Contains details of specific pizzas ordered within each unique transaction.  
##### pizzas:
Houses pizza variant sizing and exact pricing metrics.
##### pizza_types:
Stores descriptive metadata regarding pizza names and culinary categories.  
## System Requirements
To replicate, execute, or build upon this analysis, the environment must meet the following baseline requirements:
##### Database Management System: 
MySQL Server (v8.0 or higher recommended for full Window Function compatibility).
#### Interface Client:
MySQL Workbench, DBeaver, or an equivalent SQL IDE.
#### Dataset Dependencies:
The relational database model must have the 4-table transactional structure (orders, order_details, pizzas, pizza_types) populated with store transactional history.
## Tools and Technologies Used
##### MySQL:
The primary relational database engine used for storing, querying, and structuring transactional datasets. 
##### Data Aggregations:
Intensive application of functions such as COUNT(), SUM(), AVG(), and ROUND() to calculate macroscopic business performance metrics. 
##### Relational Joins: Heavy utilization of INNER JOIN and standard JOIN conditions to bridge transaction-level data with product pricing and category metadata.  
##### Subqueries:
Implemented nested queries to isolate temporal calculations and establish reference values for high-level operations (such as overall revenue benchmarks). 
##### SQL Window Functions: 
Leveraged advanced analytical concepts, specifically RANK() OVER (PARTITION BY ... ORDER BY ...) and cumulative summing SUM() OVER (ORDER BY ...), to extract multi-level ranking and chronological progress.  

## Challenges Faced

##### Multi-Layer Table Normalization: 
Connecting fragmented operational information across four distinct tables required constructing multi-layered join statements. Ensuring that logic remained structurally sound across order_details, pizzas, and pizza_types simultaneously was essential to prevent duplication.  
#### Isolating Time and Granular Metrics: 
Extracting hourly behavior out of timestamp formats (using HOUR(order_time)) and grouping date metrics accurately required precise functions to prevent timezone or parsing mismatches.  
##### Advanced Category Sorting: 
Creating a localized ranking system that determines the top 3 highest revenue-generating items within each individual category (rather than globally) required wrapping window-based rankings inside dynamic subqueries to bypass standard SQL execution order restrictions.

## Insights Discovered

#### 1. Macro Revenue and Base Volumes
##### Total Transactions:
The store successfully completed a total baseline volume of 21,350 unique orders.
##### Daily Average Throughput: 
On any active operating day, the store processes an average volume of roughly 138 pizzas. 

#### 2. Customer Preferences and Physical Variables
##### Sizing Demographics:
Large ("L") sizes dominate order quantities with 18,526 instances, followed heavily by Medium ("M") at 15,385 and Small ("S") at 14,137. Extra Large ("XL") represents a niche segment with only 544 orders. 
##### Top-Selling Varieties:
Volume-wise, "The Classic Deluxe Pizza" leads with 2,453 pizzas ordered, closely contested by "The Barbecue Chicken Pizza" (2,432) and "The Hawaiian Pizza" (2,422). 
##### Category Dominance:
When looking at total quantities ordered, the "Classic" pizza category ranks highest with 14,888 items, followed by Supreme (11,987), Veggie (11,649), and Chicken (11,050).

#### 3. Financial and Revenue Analysis
##### Premium Benchmarks:
The single highest-priced product offering in inventory is "The Greek Pizza" tracking at a premium cost of 35.95.  
##### Gross Income Drivers:
When evaluating total gross revenue, "The Thai Chicken Pizza" leads individual product standings by bringing in 43,434.25, followed by "The Barbecue Chicken Pizza" at 42,768. 
##### Revenue Breakdown by Category: 
The overall financial contribution is relatively balanced across the catalog. Classic leads revenue generation at 26.91%, with Chicken holding 23.96%, Veggie holding 23.68%, and Supreme driving 25.46%.  

#### 4. Peak Operational Timelines
##### Hourly Peak Demand:
Order volumes demonstrate sharp concentration during dinner hours. Demand spikes heavily at 17:00 (5:00 PM) with 2,336 orders, peaks at 18:00 (6:00 PM) with 2,399 orders, and maintains high volume at 19:00 (7:00 PM) with 2,009 orders. Operations during early mornings (9:00 AM - 10:00 AM) or late nights (23:00 PM) show minimal traffic.

## Recommendations for Improvement
##### Optimize Peak-Hour Staffing and Prep:
Align kitchen staffing schedules and prep work specifically with the high-demand window between 16:00 and 20:00 (4:00 PM – 8:00 PM). Pre-stretching dough and preparing ingredients for high-volume options like Classic and Supreme types before 16:00 can reduce order fulfillment delays. 
##### Targeted Promotions for Low-Volume Sizing:
Since XL sizes represent an extremely small fraction of total orders (544 units), consider introducing targeted bundle promotions (e.g., "Family-Size Weekend Deals") to increase the average order value. 
##### Capitalize on Revenue Drivers:
"The Thai Chicken Pizza" and "The Barbecue Chicken Pizza" generate the highest revenue. Feature these products prominently on physical and digital menus to drive high-margin selections.  
##### Database Optimization (Indexing):
To preserve quick query performance as transactional tables scale past millions of rows, implement database indexes on frequently joined primary/foreign key columns (order_id, pizza_id, and pizza_type_id), as well as frequently filtered columns like order_date and order_time.  
