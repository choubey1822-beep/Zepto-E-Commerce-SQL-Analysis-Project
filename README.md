This project involves a comprehensive end-to-end data analysis of a real-world e-commerce dataset from Zepto, a leading quick-commerce platform. The goal was to simulate the workflow of a Data Analyst by cleaning, processing, and analyzing inventory data to extract actionable business insights. Using PostgreSQL, I explored product listings, pricing strategies, stock availability, and revenue potential to help drive data-informed decision-making.

Key Features & Insights
Data Cleaning & Transformation: Handled data type conversions, managed character encoding issues (UTF-8), and standardized currency units (converting Paisa to Rupees) for accurate reporting.

Inventory Analysis: Identified stock-out risks for high-MRP items and categorized products based on weight (Low, Medium, Bulk) for warehouse planning.

Revenue Optimization: Estimated potential revenue per category by calculating the total value of available inventory.

Pricing Strategy: Analyzed discount distributions to find the "best value" products and identified popular high-priced items that maintain sales without heavy discounts.

Market Trends: Discovered which categories (e.g., Fruits & Vegetables) offer the highest average discounts to understand promotional behavior.

Tech Stack
Database: PostgreSQL (PG Admin 4)

Language: SQL

Dataset Source: Scraped Zepto product listings (Kaggle)

Key SQL Skills Demonstrated
Data Definition (DDL): Schema design, table creation with primary keys and constraints.

Data Manipulation (DML): Complex updates and conditional deletions.

Aggregations & Joins: GROUP BY, SUM, AVG, and ROUND for financial metrics.

Conditional Logic: Utilized CASE WHEN statements for custom product segmentation.

Filtering & Sorting: Advanced use of HAVING, DISTINCT, and nested logical operators.
