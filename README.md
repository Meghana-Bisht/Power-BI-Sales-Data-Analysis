# Sales Performance & Profitability Dashboard - ElectroHub

### Problem Statement

This dashboard helps ElectroHub understand its sales performance and profitability across various product categories such as Electronics, Clothing, and Home Appliances. It identifies the top and bottom-performing products by sales, profit, and quantity to help in inventory management.

By analyzing sales trends over time (daily, monthly, quarterly, annually), the business can identify peak seasons and potential downturns. Additionally, the dashboard evaluates the impact of different promotion categories on average discounts and total orders, allowing for data-driven decisions on future marketing strategies

### Overall Inferences

1. Total Orders: The business processed a total of 3.51K orders

2. Top Performer: The Apple iPhone 14 is the leading product across all major metrics: Sales (21M), Profit (2.1M), and Units Sold (281)

3. Sales Trends: There is a consistent sales trend from 2020 through 2023, followed by a significant projected dip in 2024 that requires investigation

4. Promotion Effectiveness: The Weekend Flash Sale offers the highest average discount (23K), whereas the Festive Diwali promotion currently shows 0K average discount in the sampled data

### Steps followed -

Step 1: Load the sales dataset into Power BI Desktop. 

Step 2: Open Power Query Editor and use "Column Distribution", "Column Quality", and "Column Profile" to ensure data integrity. 

Step 3: Perform data cleaning to handle any null values in critical fields like Profit, Net Sales, and Discount Percentage.

Step 4: In the Report View, select a professional theme and insert the ElectroHub logo and company name using the Insert tab.

Step 5: Add Visual Filters (Slicers) for the following fields to meet business requirements : Date (Range Slider) Customer Name Product Name Promotion Name 

Step 6: Create KPI Cards to represent high-level metrics: Total Sales (e.g., 97M for Date Filter 1) Total Profit (e.g., 9.7M for Date Filter 1) Total Quantity Sold (e.g., 5.7K for Date Filter 1) 

Step 7: Add a Scatter Plot to show the relationship between Profit vs. Net Sales, demonstrating the correlation between revenue and earnings. 

Step 8: Add Bar/Column Charts to represent: Top/Bottom 5 Products by Sales, Profit, and Unit Sold . Average Discount by Promotion Categories (Weekend Flash, Clearance, etc.) . Net Sales by City (Bhopal, Kanpur, Indore, etc.). 

Step 9: Insert a Line Chart to visualize Sales Trends by Period (2020–2024). 

Step 10: Create a Table Visual to show raw order details including OrderID, CustomerID, Product ID, and Net Sales. 

Step 11: Use DAX measures to create dynamic comparisons between any two periods selected by the user (Date Filter 1 vs. Date Filter 2) . DAX Expressions Used Total Count of Orders: Total Sales (Filter 1): 

### Snapshot of Reports 

![Overview](<img width="632" height="353" alt="Image" src="https://github.com/user-attachments/assets/e3b5bef2-7cea-4576-b82d-2f9d4da74314" />)

![TopBottomAnalysis](<img width="626" height="355" alt="Image" src="https://github.com/user-attachments/assets/15183613-8f1e-4355-83ea-3d93cdf5dcd9" />)

![SalesProfitQuantity](<img width="619" height="328" alt="Image" src="https://github.com/user-attachments/assets/1fac8df5-93ae-4e9c-9d38-e1c2ebaac461" />)

![TableVisual](<img width="627" height="358" alt="Image" src="https://github.com/user-attachments/assets/2d87843b-e4c5-4076-8456-4d2f013bb908" />)

 Insights The following inferences can be drawn from the dashboard:
 
Product Performance Top 5 by Sales: Apple iPhone 14 (21M), Apple MacBook Air (20M), Sony Bravia 55" TV (19M), Samsung Galaxy S21 (15M), HP Pavilion Laptop (14M) . 

Bottom 5 by Profit: Colgate Toothpaste (2K), Dove Soap Pack (8K), Nivea Body Lotion (8K), L'Oreal Shampoo (17K), Tupperware Lunch Box (26K) . 

Geographic Trends The city of Bhopal generates the highest Net Sales, followed by Kanpur and Indore. 

Cities like Bangalore and Hyderabad show lower sales volume in this specific dataset. 

Discount & Promotions The Weekend Flash Sale and Clearance Sale are the primary drivers of discounts, together accounting for over 40K in average discount value. Summer Sales and New Year Specials have more conservative discount structures. 

Time-Period Comparison When comparing two periods (e.g., 2020-2024 vs. 2021-2024), total sales dropped from 97M to 75M as the window narrowed, indicating that early-period sales (2020) were significant contributors to overall revenue .

### Column created using DAX Query

1. DateTable1 = CALENDARAUTO()
2. DateTable2 = CALENDARAUTO()


### DAX Measures created

1. Sum dim = sum('Fact Table'[Net Sales])

2. Sum of NetSales = CALCULATE(SUM('Fact Table'[Net Sales]),all('DateTable1'),USERELATIONSHIP(DateTable2[Date],'Fact Table'[Date (dd/mm/yyyy)]))

3. Sum of TotalProfit = CALCULATE(sum('Fact Table'[Profit]),all(DateTable1),USERELATIONSHIP(DateTable2[Date],'Fact Table'[Date (dd/mm/yyyy)]))

4. Sum of TotalQuantiySold = CALCULATE(sum('Fact Table'[Units Sold]),all(DateTable1),USERELATIONSHIP(DateTable2[Date],'Fact Table'[Date (dd/mm/yyyy)])) 
