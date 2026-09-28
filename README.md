# End-to-End-Power-BI-Reporting-JCars
An end-to-end Power BI business intelligence solution analyzing sales, profitability, and logistics for JCars.
This repository contains a comprehensive Power BI solution developed for JCars Logistics. It demonstrates the ability to audit raw flat-file data, standardize international currencies, build an optimized analytical data model, and write explicit DAX measures to answer critical management questions regarding gross profit margins, delivery operations, and sales channel performance.
## Project Objective
The objective of this project is to develop an interactive Power BI solution for JCars Logistics to analyze sales, profitability, vehicle performance, and logistics efficiency. The project involves transforming a raw, messy flat dataset into a reliable analytical model to support management decision-making.

## 1. Data Quality Audit & Cleaning (Power Query)
Upon initial inspection of the `Jcars_data.csv` flat file, several data quality issues were identified and resolved using Power Query:
* **Inconsistent Text Formatting:** Columns like `Car Make`, `City`, and `Sales Rep` contained invisible spaces and mixed casing (e.g., "MARY", "Mary Wanjiku"). These were standardized using Trim, Clean, and Capitalize Each Word transformations.
* **Typographical Errors:** Identified and replaced manual data entry typos in the `Sales Rep` column (e.g., "Br1an" to "Brian", "A1sha" to "Aisha").
* **Mixed Date Formats:** The `Order Date` and `Delivery Date` columns contained a mix of standard text dates and Excel serial numbers (e.g., 46066). These were resolved before converting the columns to the Date data type.
* **String Percentages:** The `Discount` column was stored as text (e.g., "7%"). The percentage symbols were removed, and the values were divided by 100 to convert them into usable decimal numbers (0.07).
* **Missing/Invalid Values:** Text placeholders like "missing", "TBD", and Excel `#VALUE!` errors in financial columns were replaced with 0 to prevent DAX calculation errors.

## 2. Currency Standardization Approach
The monetary columns (`Unit Selling Price`, `Unit Cost`, `Delivery Fee`, `Logistics Cost`, and `Revenue Recorded`) contained mixed currencies (USD, ZAR, EUR/?, KES/KSh) and text suffixes ("M" for millions). 

To standardize all financial data to Kenya Shillings (KES) as required by management, a Custom Column M formula was applied to extract the numerical values and apply the following assumed exchange rates:
* **USD ($):** 130 KES
* **EUR (?):** 170 KES
* **ZAR (R):** 7 KES
* **Suffix "M":** Multiplied base value by 1,000,000

## 3. Data Validation
A critical validation check was performed by comparing the company's `Revenue Recorded` column against a mathematical calculation of true revenue (`Clean Unit Selling Price` * (1 - `Discount`) * `Units Sold`). 
* **Finding:** The recorded revenue contains significant discrepancies and negative error values, making it unreliable for management reporting. Moving forward, explicit DAX measures will be used to calculate true revenue and profitability.

## 4. Data Modeling


## 5. DAX Measures & Business Logic


## 6. Key Insights & Recommendations
