# Sales--Performance-analysis
Sales Performance Analysis
Project Overview
The Sales Performance Analysis project is designed to provide in-depth insights into the sales data of a retail company using the Superstore dataset. This dataset contains detailed information about orders, products, customers, and regions. By analyzing this data, the project aims to identify key sales trends, top-performing regions, best-selling products, and calculate the average order value.

The project is structured to leverage powerful tools like Excel, SQL Server, and Power BI. Initially, the data is cleaned and prepared in Excel, then imported into SQL Server for structured querying. Finally, an interactive dashboard is built in Power BI to visualize the findings and present actionable insights.

Tools Used
Excel: Used for data cleaning, preparation, and initial analysis using PivotTables.
SQL Server Management Studio (SSMS): Utilized for importing data into a SQL database, managing the data, and executing SQL queries for advanced analysis.
Power BI: Employed to create interactive dashboards that visually represent the sales data, making it easier to interpret and share insights.
GitHub: Used for version control and project submission, ensuring the project is well-documented and accessible for future reference.
Project Workflow
Step 1: Data Cleaning in Excel
Data Cleaning:

Removed duplicates based on Order ID to ensure data accuracy.
Standardized date formats and filled in missing values.
Cleaned up product names, especially those containing commas, to prevent issues during the data import process.
Handling Product Names:

Enclosed product names with commas within double quotes to ensure they are correctly processed during the CSV import.
Saved Cleaned Data:

Exported the cleaned Excel data as a comma-delimited CSV file for subsequent import into SQL Server.
Step 2: Importing Data into SQL Server
SQL Server Setup:

Installed SQL Server Management Studio (SSMS) and created a new database named SuperstoreSalesDB.
Table Schema:

Defined the table schema to match the dataset structure, including columns such as:
RowID (Primary Key)
OrderID, OrderDate, ShipDate, ShipMode, CustomerID, CustomerName
Segment, Country, Region, City, State, PostalCode
ProductID, Category, SubCategory, ProductName, Sales (Decimal)
Data Import:

Used the BULK INSERT command to import the cleaned CSV file into the SQL Server database.
Example SQL command:
sql
Copy code
BULK INSERT Superstore
FROM 'C:\path\to\file.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);
Step 3: SQL Queries for Initial Analysis
Sales by Region:

Query: SELECT Region, SUM(Sales) FROM Superstore GROUP BY Region;
Purpose: Identify regions with the highest sales to understand geographical performance.
Monthly Sales Trends:

Query: SELECT FORMAT(OrderDate, 'yyyy-MM') AS Month, SUM(Sales) FROM Superstore GROUP BY FORMAT(OrderDate, 'yyyy-MM');
Purpose: Analyze sales over time to identify trends and seasonal patterns.
Top-Selling Products:

Query: SELECT ProductName, SUM(Sales) FROM Superstore GROUP BY ProductName ORDER BY SUM(Sales) DESC;
Purpose: Determine which products are the most profitable.
Average Order Value:

Calculation: Average Order Value = SUM(Sales) / COUNT(OrderID);
Purpose: Measure the average value of orders to gauge customer spending behavior.
Step 4: Power BI Dashboard Creation
Importing Data into Power BI:

Imported data from SQL Server into Power BI to create visual representations of the analysis.
Verified data relationships to ensure accurate visualizations.
Key Metrics and Visualizations:

Total Sales by Region: A bar chart to highlight regions with the highest sales.
Monthly Sales Trends: A line chart to track sales trends over time.
Top-Selling Products: A bar chart displaying the top 10 products by sales volume.
Average Order Value: A card visual representing the calculated average order value using a custom measure in Power BI:
DAX
Copy code
Average Order Value = SUM(Sales) / COUNT(OrderID)
Additional Visuals:

Cards: Display total sales, total orders, and average order value for quick insights.
Drill-through functionality: Allows users to explore detailed data by Region, Category, and Product Name.
Step 5: Project Submission on GitHub
GitHub Repository Creation:
Created a repository titled Sales-Performance-Analysis to host all project files.
Uploaded the cleaned dataset, SQL scripts, Power BI dashboard (.pbix file), and project documentation.
Included a README file with comprehensive project details, instructions, and a summary of the analysis.
Conclusion
The Sales Performance Analysis project successfully leveraged data analysis techniques to uncover insights from the Superstore dataset. Through a combination of Excel, SQL Server, and Power BI, we were able to create a dynamic and informative dashboard that provides valuable business insights into sales performance, helping stakeholders make informed decisions.

Feel free to explore the repository and the interactive Power BI dashboard for a deeper understanding of the project outcomes.

