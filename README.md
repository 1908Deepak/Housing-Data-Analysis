# HOUSE DATA ANALYSIS 🏠📊

### Dashboard Link :https://app.powerbi.com/links/GjvxKOR88s?ctid=37d002c9-062c-435d-beff-d1efc9989fe4&pbi_source=linkShare

## Problem Statement

House Data Analysis Dashboard – Power BI

This dashboard helps real estate businesses and analysts understand housing sales trends across different regions, cities, and house types.
It provides insights into units sold, purchase prices, and sales performance, along with KPIs such as Last Year Sales and Last 13-Month Sales.
By analyzing these KPIs and visualizations, decision-makers can track housing market trends, monitor regional performance, and evaluate sales growth by house type and region.

## Key Objective

To provide a single interactive dashboard for housing sales analysis with KPIs, purchase price tracking, and regional insights.


### Steps followed 

SStep 1 – Load Data from Excel workbook

- Connected to  SQL Server Database containing housing sales data.

- Used Get Data → SQL Server  →  SQL Database option in Power BI Desktop.


Step 2: Open Power Query Editor and in the View tab under Data Preview, enabled:

- Enabled:

  - Column distribution

  - Column quality

  - Column profile

- Set profiling to "Based on entire dataset".

Also, changed profiling to “Based on entire dataset”.

Step 3 – Data Quality Checks

- No null values found in critical columns like Purchase Price, House Type, Region.

- Some missing values in Offer Price treated as 0

- Verified Year, Quarter, Month Name, and Day Number consistency...

Step 4: Created Measures:

  -  Sales By Region 
  -  Total ytd Sales
  -  Median Sales Price
  -  Last 12 Month Sales

DAX expression was written;
       
        Last 12 Month Sales = CALCULATE(SUM(Housing[purchase_price]), DATESINPERIOD(Housing[date], MAX(Housing[date]),-12, MONTH))
    
        YoT_Sales_Growth = Var CurrYearSales = CALCULATE(SUM(Housing[purchase_price]), YEAR(Housing[date]) = YEAR(max(Housing[date])))
        Var PrevYearSales = CALCULATE(SUM(Housing[purchase_price]), YEAR(Housing[date]) = YEAR(max(Housing[date]))-1) 
        Return 
        IF(PrevYearSales<>0,(CurrYearSales - PrevYearSales)/ PrevYearSales, BLANK())

        Median Sales Price Sales = 
        var CurrMedianPrice = MEDIANX(FILTER(Housing,YEAR(Housing[date])= YEAR(MAX(Housing[date]))),Housing[purchase_price])
        VAR PrevMedianPrice = MEDIANX(FILTER(Housing,YEAR(Housing[date])= YEAR(MAX(Housing[date]))-1),Housing[purchase_price])
        RETURN
        IF(PrevMedianPrice<>0, (CurrMedianPrice -PrevMedianPrice)/ PrevMedianPrice,BLANK())

        Sales by Region = CALCULATE(SUM(Housing[purchase_price]),ALLEXCEPT(Housing,Housing[region]))  

Step 5 : KPIs
Created card visuals with DAX measures:

          Unit sold in latest Year & Quarter = CALCULATE(DISTINCTCOUNT(Housing [house_id]), YEAR(Housing[date]) = YEAR(MAX(Housing[date])) && QUARTER(Housing[date]) = QUARTER(MAX(Housing[date])))

![kPIs](https://github.com/user-attachments/assets/b2784f08-6835-443f-8e9f-99622444cdf3)

Step 5 – Slicers Added

- Area
- Sales Type
- City
- Region

Step 7 – Formatting & Branding
- Applied professional theme in View tab.
- Added logo, tagline, and design shapes for KPIs.

Step 8 - Publish to Power BI Service 
- Published dashboard for cloud access and sharing with stakeholders.


![Publish_Message](https://github.com/user-attachments/assets/7d6891f7-c2f7-48eb-9412-017fb4bbf831)

# Dashboard :   Index Page 

![dashboard_snapo](https://github.com/user-attachments/assets/870a34e6-b236-4713-a43b-af7fa9e479eb)

 
 # Report Snapshot 1: Home Page

 
![Dashboard_upload](https://github.com/user-attachments/assets/d235b588-f659-4494-91c6-e3898b894146)


 # Report Snapshot 2: House type

 ![Dashboard_upload](https://github.com/user-attachments/assets/c6b7ca08-a9a5-4cd8-ad3e-2b50043ff0bd)



# Report Snapshot 3: Region

 ![Dashboard_upload](https://github.com/user-attachments/assets/514260bf-5321-49ce-966a-c2e941a47d2e)


# Insights

### Sales Performance

- Units sold last year show steady growth compared to previous year..

- Last 12 months highlight seasonal patterns with spikes in festive quarters

### Regional Trends

- Region A dominates sales volume, while Region C shows highest average SQM prices.
- Smaller regions have lower sales but relatively higher median purchase prices.

### Price Insights
- Scatter analysis shows luxury properties skewing market averages.

- Smaller regions have lower sales but relatively higher median purchase prices.

# Conclusion

The House Data Analysis Dashboard provides actionable insights into housing sales, pricing, and regional trends.
By monitoring these KPIs and visuals, businesses can:

- Track YoY and monthly sales growth

- Compare regional performance

- Support decision-making with detailed transaction-level data


   
## Resources

[House Dataset](https://drive.google.com/drive/folders/18MFDeACxqYbxvdwqVEhcJPfnsiN2X791?usp=sharing)

[Templates](https://drive.google.com/drive/folders/18MFDeACxqYbxvdwqVEhcJPfnsiN2X791?usp=sharing)


## Authors

- [1908Deepak](https://github.com/1908Deepak)


## Feedback

If you have any feedback, please reach out to us at deepaksingh190810@gmail.com

