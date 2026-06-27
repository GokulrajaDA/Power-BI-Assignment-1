# E-commerce Sales Analytics Dashboard - Power BI Assignment

## 📊 Project Overview
This project involves building an end-to-end Business Intelligence solution for an E-commerce store using Microsoft Power BI. The assignment covers data import, cleaning, modeling, DAX measures, and interactive dashboard creation.

## 📁 Dataset
- **Source**: E-commerce store dataset
- **Files Used**:
    - List of orders.csv
    - Order Details.csv
    - Sales Target.csv
- **Total Records**: 490+ transactions

## ✅ Tasks Completed

### 1. Data Import & Connection
- Imported 3 CSV files using `Get Data` → `Text/CSV`
- Loaded data into Power BI Desktop with proper data types
- Established relationships between tables in Model View

### 2. Data Cleaning & Transformation - Power Query
- **Remove Duplicates**: Eliminated duplicate Order IDs from List of Orders
- **Missing Values**: Handled nulls and blanks in Discount, Profit columns
- **Data Types**: Set correct types - Date for Order_Date, Decimal for Amount/Profit
- **Formatting**: Applied proper formatting for currency and percentage fields
- **Text Transformation**: Used `Text.Proper` for Customer Name standardization
- **Custom Columns**:
    - `Location` = City & ", " & State
    - `Profit Margin` = Profit / Amount
    - `Profit Status` = IF logic for Loss/Break-Even/Profit

### 3. Data Modeling & Relationships
- Created Star Schema with Fact and Dimension tables
- **Fact Table**: Sales_Fact with Order_ID as primary key
- **Dimension Tables**: Customer_Dim, Product_Dim, Store_Dim, Date_Dim
- Established One-to-Many relationships using Order_ID, Product_ID, Customer_ID
- Set Cardinality and Cross-filter direction for optimal performance

### 4. DAX Measures & Calculated Columns
Created key business metrics using DAX:
```dax
Total Sales = SUM(Sales_Fact[Amount])
Total Profit = SUM(Sales_Fact[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
Total Orders = DISTINCTCOUNT(Sales_Fact[Order_ID])
Sales vs Target = [Total Sales] - SUM(Sales_Target[Target])
YTD Sales = TOTALYTD([Total Sales], 'Date'[Date])
High Value Orders = CALCULATE([Total Orders], Sales_Fact[Amount] > 1000)5. Interactive Dashboard & Visualizations
Built 2-page interactive report:Page 1: Sales Overview DashboardKPI Cards: Total Sales, Total Profit, Total Orders, Avg Order ValueBar Chart: Sales by Product Category - Sports, Electronics, Home, Beauty, ClothingLine Chart: Monthly Sales Trend with Target comparisonMap Visual: State-wise Sales distribution across USADonut Chart: Sales by Payment Type - Credit Card, COD, PayPalTable: Top 10 Products by SalesPage 2: Customer & Product AnalysisMatrix: Category vs State sales breakdownBar Chart: Top 10 Customers by RevenueScatter Plot: Discount % vs Profit Margin correlationSlicers: Interactive filters for Year, State, Category, Payment_Type6. Advanced Features
Drill-through: Click Category to see Product-level detailsTooltips: Custom tooltips showing Profit, Quantity on hoverBookmarks: Saved views for Executive Summary vs Detailed AnalysisConditional Formatting: Red/Green indicators for Profit StatusCross-filtering: All visuals interact with each other📈 Key Insights
Top Category: Sports leads with highest revenue contributionBest State: Vermont shows maximum sales performanceProfit Driver: Low discount orders have 3x higher profit marginsCustomer Pattern: 20% customers contribute 60% revenuePayment Trend: PayPal most used with 181 transactionsSeasonality: Q4 shows 40% higher sales vs other quarters📂 Deliverables
Power BI File: Assignment_YourName.pbix with all transformations and visualsPDF Export: Assignment_Report.pdf - Dashboard screenshotsData Model: Star schema with documented relationships🛠️ Tools & Features Used
Power Query Editor | DAX | Data Modeling | Relationships | KPI Cards | Bar Chart | Line Chart | Map | Matrix | Slicers | Drill-through | Bookmarks | Conditional Formatting | CALCULATE | TOTALYTD | DIVIDE📝 How to Use
Download Assignment_YourName.pbixOpen in Power BI DesktopRefresh data if promptedNavigate between Page 1 and Page 2 using tabsUse slicers on the right to filter by State, Category, YearClick any visual element to cross-filter entire dashboardRight-click on Category bars → Drill through to see product details📊 Data Model DiagramjavascriptCustomer_Dim ←→ Sales_Fact ←→ Product_Dim
                    ↕
                Store_Dim
                    ↕
                Date_Dim
