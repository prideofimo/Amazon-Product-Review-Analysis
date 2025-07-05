# Amazon-Product-Review-Analysis
First portfolio and DSA project: Analyzed Amazon product reviews and pricing data with Excel, delivering insights via pivot tables and a dynamic dashboard.
# Amazon Product Review Analysis

## Company Overview
This project was completed as part of a data analytics case study for RetailTech Insights, a company that provides e-commerce analytics solutions to sellers on platforms such as Amazon. The purpose of this project was to analyze product and customer review data to generate actionable insights that can guide product improvement, marketing strategy, and customer engagement efforts.

The analysis demonstrates advanced Excel skills, including data cleaning, transformation, pivot tables, calculated columns, and dashboard design. The results are presented in an interactive Excel dashboard and documented to highlight key findings and recommendations.

## Dataset Description
The dataset consists of product and customer engagement data scraped from Amazon product pages. Each row represents a unique product with associated metadata and aggregated reviewer information. 

**Dataset characteristics:**
- Total records: 1,465 rows
- Total fields: 16 columns

The analysis is based on the Excel file [ejigha Godswill Amazon product review analysis.xlsx](https://github.com/user-attachments/files/21071056/ejigha.Godswill.Amazon.product.review.analysis.xlsx) which includes five sheets

- `original data`: The raw data as received.
- `cleaned data`: Cleaned and prepared data with only relevant columns retained.
- `structured table`: Tabular data structured as a formal Excel table for pivot analysis.
- `pivot tables`: Pivot tables used to answer specific analysis questions.
- `dashboard`: A dynamic Excel dashboard highlighting key metrics and findings.

## Data Cleaning and Preparation
Significant data cleaning and transformation were necessary to make the dataset suitable for analysis. The following steps were performed:
- Shortened lengthy product names to the first four words for readability.
- Removed duplicate rows based on `product_id`.
- Removed rows with null or invalid values in key numeric columns.
- Dropped irrelevant columns to focus on fields necessary for analysis.
- Created calculated columns:
  - Price range buckets (e.g., < ₹200, ₹200–₹500, > ₹500)
  - Discount range buckets (e.g., 0–10%, 10–30%, 50%+)
  - Total potential revenue (`actual price × number of ratings`)
- Separated product categories into main and sub-categories.

## Business Questions Answered
The following business questions were addressed using pivot tables and calculated fields:
1. What is the average discount percentage by product category?
2. How many products are listed under each category?
3. What is the total number of reviews per category?
4. Which products have the highest average ratings?
5. What is the average actual price versus discounted price by category?
6. Which products have the highest number of reviews?
7. How many products have a discount of 50% or more?
8. What is the distribution of product ratings (e.g., how many products are rated 3.0, 4.0, etc.)?
9. What is the total potential revenue by category?
10. What is the number of unique products per price range bucket?
11. How does the rating relate to the level of discount?
12. How many products have fewer than 1,000 reviews?
13. Which categories have products with the highest discounts?
14. Which are the top 5 products in terms of both rating and number of reviews combined?

## Codes / Formulas Used
Some of the Excel formulas used to implement calculated columns and analysis are documented below.

### Shortened Product Name
Combines the first four words of the product name:
```excel
==TRIM(LEFT(B3,FIND("#",SUBSTITUTE(B3," ","#",4)&"#")-1))
```
### Price Range Bucket
Assigns each product into one of three price segments:

Less than ₹200
Between ₹200 and ₹500
Greater than ₹500
``` excel
=IF([@discounted_price]<200,"<₹200", IF(OR([@discounted_price]=200,[@discounted_price]<=500),"₹200-₹500",">₹500"))
```

### Discount Range Bucket
Groups products by discount level:
``` excel
=IF(M2<=10%,"0 - 10%",IF(M2<=20%,"11 - 20%",IF(M2<=30%,"21 - 30%",IF(M2<=40%,"31 - 40%",IF(M2<=50%,"41 - 50%",IF(M2<=60%,"51 - 60%",IF(M2<=70%,"61 - 70%", IF(M2<=80%,"71 - 80%",IF(M2<=90%,"81 - 90%","91-100%")))))))))
```

### Total Potential Revenue
Calculates potential revenue as actual price multiplied by number of ratings:
``` excel
=[@actual_price]*[@rating_Count]
```

### Top Product Score
Ranks products by rating and number of reviews combined:
``` excel
=[@rating]+([@rating_count/1000)
```
### Discount Range Bucket
to determine which products have a discount of 50% or more
``` excel
=IF([@discount_percentage]>=50%, "50% or more", "<50%")
```

## Dashboard
A dynamic Excel dashboard presents the most important metrics and findings. The dashboard includes:
- Key performance indicators such as average discount and total potential revenue by category
- Top-performing products by ratings and reviews
- Price and discount distributions
- Product rating distribution
- Category-level comparisons

`Dashboard Sample`
<img width="1286" alt="Amazon Dashboard Screenshot" src="https://github.com/user-attachments/assets/61cc4dcf-fa2e-4607-a374-618113bbb549" />

## Tools and Techniques
- Microsoft Excel
- Data cleaning and preparation
- Pivot tables and calculated columns
- Structured tables
- Slicers and conditional formatting
- Dashboard design principles

## Key Insights
- Certain categories generated disproportionately high potential revenue despite having fewer products listed.
- Products with extremely high discounts often correlated with lower average ratings.
- Most products were priced between ₹200–₹500, but higher-priced items contributed significantly to revenue.
- Many products had fewer than 1,000 reviews, suggesting opportunities to increase engagement.
- Some sub-categories exhibited extremely high average discounts, suggesting pricing strategy adjustments.

## Repository Contents
- [ejigha Godswill Amazon product review analysis.xlsx](https://github.com/user-attachments/files/21071056/ejigha.Godswill.Amazon.product.review.analysis.xlsx): Contains raw data, cleaned data, structured table, pivot tables, and dashboard.
- `Screenshot`: PNG snapshots of the dashboard, pivot tables, and cleaned data.

## How to Explore
1. Open `Ejigha Godswill Amazon Product Review Analysis.xlsx` in Microsoft Excel.
2. Navigate to the `dashboard` sheet for a summary view.
3. Review the `pivot_tables` sheet for detailed answers.
4. Examine `cleaned_data` and `structured_table` for prepared data.

## Author
Ejigha Godswill Oluchukwu 
Junior Data Analyst  
RetailTech Insights  
Email: [Godswillejigha16@gmail.com]  
Portfolio: [[Ejigha Godswill Portfolio](https://github.com/prideofimo)]
