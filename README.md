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


📁 Dataset Overview

The dataset was sourced from Kaggle and was originally scraped from Zepto’s official product listings. It mimics what you’d typically encounter in a real-world e-commerce inventory system.

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks.

🧾 Columns:

sku_id: Unique identifier for each product entry (Synthetic Primary Key)

name: Product name as it appears on the app

category: Product category like Fruits, Snacks, Beverages, etc.

mrp: Maximum Retail Price (originally in paise, converted to ₹)

discountPercent: Discount applied on MRP

discountedSellingPrice: Final price after discount (also converted to ₹)

availableQuantity: Units available in inventory

weightInGms: Product weight in grams

outOfStock: Boolean flag indicating stock availability

quantity: Number of units per package (mixed with grams for loose produce)

🔧 Project Workflow
Here’s a step-by-step breakdown of what we do in this project:

1. Database & Table Creation
We start by creating a SQL table with appropriate data types:

CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
2. Data Import
Loaded CSV using pgAdmin's import feature.

If you're not able to use the import feature, write this code instead:

   \copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
  FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV UTF-8 format.
3. 🔍 Data Exploration
Counted the total number of records in the dataset

Viewed a sample of the dataset to understand structure and content

Checked for null values across all columns

Identified distinct product categories available in the dataset

Compared in-stock vs out-of-stock product counts

Detected products present multiple times, representing different SKUs

4. 🧹 Data Cleaning
Identified and removed rows where MRP or discounted selling price was zero

Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability

5. 📊 Business Insights
Found top 10 best-value products based on discount percentage

Identified high-MRP products that are currently out of stock

Estimated potential revenue for each product category

Filtered expensive products (MRP > ₹500) with minimal discount

Ranked top 5 categories offering highest average discounts

Calculated price per gram to identify value-for-money products

Grouped products based on weight into Low, Medium, and Bulk categories

Measured total inventory weight per product category
