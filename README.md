# Household-Food-Consumption-And-Price-Trend-Analysis-In-Nigeria
<img width="1036" height="550" alt="FULL TABLE" src="https://github.com/user-attachments/assets/9b8c699a-5e42-44af-980f-31844e935e00" />


<img width="1003" height="535" alt="Screenshot 2025-07-10 at 23-14-41 Nigeria Average Food Price pdf" src="https://github.com/user-attachments/assets/502d7d10-716a-44bf-8b59-c1e65323d8e5" />


## INTRODUCTION

Food prices are a major economic concern especially in countries like Nigeria, where a large share of households income go into food. Food inflation in Nigeria has been a major concern, with recent reports showing it is a key driver of overall inflation. Factors contributing to the high food inflation include rising prices of staples items like rice,beans, and cooking oil, as well as the impact of floods destroying farmland.

## OBJECTIVE
The primary purpose of the project is to transform this complex and unorganized food price data into a meaningful tool, that will enable citizens to:

* Real time tracking of national average prices.
* Inspect the MoM and YoY price change of essential food items
* Find out where food prices are highest and lowest in different states.
* Investigate the region with the most purchased food items.
* Facilitate a data-driven decision making for consumers and policymakers.
  
## 📂DATA SOURCE
The data used in this project was sourced from the National Bureau of Statistics (NBS),Nigeria , who are known for regularly publishing, collecting, compiling and analyzing monthly reports on market trends and environmental activities. They serves as the authoritative source and custodian of official statistics in Nigeria, providing data to guide policy-making and national development.

## 🛠️ TOOLS AND METHODOLOGY
### Tools
The entire project process , from data cleaning to visualization, was conducted within the Microsoft Power BI Desktop environment:

* Power Query Editor: For data extraction, transformation, and loading (ETL). This includes unpivoting, date parsing, data type conversions, and data cleaning.

* DAX (Data Analysis Expressions): For creating calculated columns, Tables and measures to perform complex aggregations, time intelligence calculations, and conditional logic.
Power BI Visualization Engine: For designing interactive and insightful charts, tables, and slicers.

## 🧪 Methodology

### 1. Data Acquisition and Initial Loading
Get data from Excel files containing (Data tables (‘selected food ‘, ‘Zone Data’)) are imported into Power Query Editor from their respective source files.

### 2. Data Transformation in Power Query Editor (ETL)

• Merged files into one table for easy analysis .

• Unpivoting: Monthly price columns (e.g., “Oct 2024 Price”, “Nov 2024 Price”, “Dec 2024 price”) are unpivoted to create `Attribute` (containing the month-year string) and `Value` (containing the price) columns. The “Value” column is renamed to ‘’Average Price”. Repeated the same process for MoM change, YoY change, Highest price, Highest State, Lowest price, Lowest state.

• Advanced Date Parsing and Correction:

A critical step involves correcting dates where the year was erroneously ‘2025’, but the day indicated the true year (e.g., ‘10/23/2025' meant ‘October 2023', ‘10/24/2025’ meant ‘October 2024').

• A new custom column, ‘Cleaned Date’, is created using Power Query . This extracts the actual month from the date string, dynamically determines the correct year (2023 or 2024) based on the day component (23 or 24), and constructs a new date, standardizing the day to the 1st of the month for consistent monthly analysis.

• Data Type Assignment: All columns are assigned appropriate data types (e.g., Cleaned Date as ‘Date’, Average Price as ‘Decimal Number’, Item, State as ‘Text’).

Original unneeded columns are removed, and final columns are renamed for clarity.

### 3. Data Modeling

. A comprehensive Dates table is generated using DAX’s ‘CALENDAR’ function, spanning from the minimum to the maximum Cleaned Date found in the selected food table. This table includes essential time attributes like Year, Month Name, and Month Number. The Dates table is marked as a “Date table” in Power BI’s model view.

• Relationship Establishment: An active “One-to-Many” relationship is created between `Dates[Date]` and selected food[Cleaned Date], with a “Both” cross-filter direction, ensuring seamless date-based filtering and calculations.

### 4. DAX Measures for Analysis

• Total National Average Price is calculated using ‘AVERAGE’ to get the average price per item across all available data.

• Previous Month Average Price (Alt): Calculates the average price for the prior month using explicit date filtering (‘EOMONTH’ and `FILTER(ALL(‘Dates’))’).

• MoM Price Change (Alt): Derives the month-over-month percentage change using the current and previous month average prices.

• Previous Year Average Price (Alt): Calculates the average price for the same month in the prior year using explicit ‘YEAR’ and ‘MONTH’ filtering (`FILTER(ALL(‘Dates’))’).

• YoY Price Change (Alt): Derives the year-over-year percentage change.

• Is Latest Month: A helper measure to dynamically identify the most recent month in the dataset for filtering visuals.

Highest items price value
### 5. Report Visualization and Interactivity

## 🔍 KEY METRICS
The data presented in the household food consumption dashboard highlights several pressing trends affecting Nigerian households.

### 🧾 National Average Food Price: ₦2,920 per Kg
* The average price across all your selected items.

### 📈 Month-on-Month Change: +2.91%
* Calculates the Average Month-on-Month change.

### 📆 Year-on-Year Change: +108.72%
* Calculate the Average Year-on-Year change.

### 💸 Highest Priced Item: ₦6,470/ Kg
* Identifies the single most expensive food item among your selected items.

### 🧾 Regional Average Price: ₦2,880
* Average price of the geopolitical zone, across all selected items.

### 🔢 No of Zone: 6
* Calculate the number of zones present in the dataset

### Unique items: 43
* Distinctly count the number of unique items.

## 🔍 KEY QUESTONS AND ANALYTICAL INSIGHTS:

### 1. What is the overall percentage increase in food prices within the month period?

  <img width="497" height="192" alt="MONTH" src="https://github.com/user-attachments/assets/45e5bbe2-47cf-42fa-b8b9-39ada2766080" />

 ### ✅ Insight:
* Sharp increase in Monthly Average Prices
* From Oct to Dec 2024, prices continued to rise slightly (from ₦1325 to ₦2920), suggesting no relief from food inflation.
* Percentage increase = [((2920 — 1325) / 1325) × 100] ≈ 120.38%
* The price of selected food items has more than doubled within a year and three months.
  
### 2. Which category dominates the top spots? What does this ranking reveal about consumer protein options?
  <img width="495" height="193" alt="TOP 10 By AVerage Price" src="https://github.com/user-attachments/assets/6ffc39ac-8138-402d-9959-a0f48af43f8b" />
  
### ✅ Insight:
* Frozen Chicken, Boneless Beef, and Catfish (dried) top the price list, with Frozen Chicken hitting ₦2,380.
* These are protein Protein consumption in Nigeria is already low due to affordability challenges. A continuous rise in protein costs risks.
  
### 3. Which food item shows the widest regional price difference?
  <img width="578" height="319" alt="1O" src="https://github.com/user-attachments/assets/57ac8805-3373-467d-9fdb-6e024e1de619" />
  
  ### ✅ Insight:
 * South East ( ₦6,527) has the highest regional average, which may be due to high consumption, longer transport routes, or greater reliance on preserved or imported items,
* North West ( ₦4,343) has the lowest overall average, which may indicates lower cost of production or higher availability of proteins.
* Catfish dried shows the most significant variation, which results to differences in preservation costs, accessibility to fish farming, or probably market demand.

### 4. Which item is the most expensive and in which state?
<img width="531" height="307" alt="STATE-WISE PRICE VARIATION OF SELECTED FOOD ITEMS IN NIGERIA" src="https://github.com/user-attachments/assets/6815ca0d-706a-4fc6-ae68-03c65de3c4c4" />
### ✅ Insight:

* Catfish (Dried) at ₦12,190 in Imo State.

* Dried catfish, likely due to post-harvest processing and transport costs, is the priciest item in the dataset.

* Taraba, Adamawa, and plateau state feature frequently in the lowest price column.

* Local availability of Chicken, fish and meat.

* Shorter supply chains.

* Lower cost of living or economic pressure on pricing.
  
### 5. Which region has the highest average food price?
  <img width="365" height="332" alt="AVERAGE PRICE" src="https://github.com/user-attachments/assets/18f3e890-86a7-477e-8b89-d08543cf6aea" />
  
### ✅ Insight:

* South East (₦3,400) has the highest regional average.
* This may be due to high consumption, longer transport routes, insecurity in farming areas, or greater reliance on imported or preserved protein.
* North West (₦2,500) has the lowest overall average.
* Suggests relatively lower cost of production or higher local availability of meat and fish.
  
 ## RECOMMENDATION

### 1. Boost Local Production in high cost zone
* Promote fish, poultry, and livestock farming especially in high cost zones.
  
* Expand agricultural extension service and access to feed, and tools that can make production easy.

### 2. Encourage intra-regional food supply Chains:

* Improve Food transportation road networks from low cost Northern state (eg Taraba) to high demand region in the Southern state (eg Imo State).
  
* Reduce losses and transport cost through the use of cold chain logistics and middlemen.
  
* Partner with private agribusinesses and cooperatives to scale infrastructure.
  
### 3. Deploy Regional Production

* Promote regional trade fairs and food vouchers to link producers to buyer across state.

* Support low income households to maintain balance amid inflation.
  
* Provide access to training, and equipment for local farmers.
  
### 4. Policy and Monitoring Systems

* Strengthen data collection and real time market monitoring to detect early inflation signals.
  
* Encourage public-private partnership for food security.

## 📌 CONCLUSION
This data goes beyond mere numbers, it reflects the daily struggles of Nigerian households facing soaring food costs and unequal access. Each figure represents a tough decision between hunger and health. Solving this crisis demands immediate, focused efforts to make food affordable and accessible for everyone, across all regions.
