# SQL Exploratory Data Analysis — Tech Layoffs

> Deep-dive EDA using MySQL to uncover patterns in global tech layoffs (2020–2023)

## 📌 Project Overview

After cleaning the layoffs dataset, this project explores it using advanced SQL techniques to find meaningful business insights.

## 🔍 Analysis Performed

- Total and max layoffs per company
- Layoffs by country and industry
- Date range of the dataset
- Companies that went completely under (100% layoff)
- Monthly rolling totals using CTEs + window functions
- Top 5 companies per year by layoffs using DENSE_RANK

## 🛠️ Tools Used

- **MySQL Workbench**
- **SQL concepts:** GROUP BY, ORDER BY, CTEs, Window Functions (DENSE_RANK, SUM OVER), SUBSTRING on dates, YEAR()

## 📂 Files

- `Exploratory_Data_Analysis.sql` — Full EDA script with comments

## 💡 Key SQL Techniques

```sql
-- Rolling total of layoffs per month using CTE + Window Function
WITH Rolling_Total AS (
  SELECT SUBSTRING(date,1,7) AS month, 
         SUM(total_laid_off) AS total_off
  FROM layoffs_staging2
  WHERE SUBSTRING(date,1,7) IS NOT NULL
  GROUP BY month
  ORDER BY 1 ASC
)
SELECT month, total_off,
  SUM(total_off) OVER(ORDER BY month) AS rolling_total
FROM Rolling_Total;
```

## 📧 Contact

Suraj Vishwakarma 
— [LinkedIn](https://www.linkedin.com/in/suraj-vishwakarma-8761b3354/) 
— sv4235404@gmail.com
