# Supermarket_sales_analysis
## 📌 Project description  
This project analyzes supermarket sales data, allowing to obtain  
key analytical metrics, visualize trends, and integrate external data  
via the National Bank of Ukraine's API.  

The project was implemented in Power BI, and the data was downloaded as a CSV file.  
The API is used to load the current exchange rate, which allows you to  
dynamically change analytical indicators depending on the currency.  

## 🛠️ Technologies used  
- Power BI is the main tool for analytics and visualization.  
- DAX (Data Analysis Expressions) - for calculating metrics.  
- API of the National Bank of Ukraine - to get the exchange rate.  
- CSV (Supermarket Sales dataset) - data source.

## 📊 Основні аналітичні метрики  
- Revenue by month *(Total by Currency | Monthly Revenue)*.  
  - The bar chart shows the total revenue of the supermarket by month.  
  - The data is displayed in two currencies (UAH/USD) with the ability to switch.  

- Total sales for the year and month *(Total by Currency | Total by Year & Month)*.  
  - The line graph shows the change in total revenue in the selected currency by year and month.  

- Payment methods *(Total by Currency | Payment Category)*.  
  - Pie chart shows the distribution of sales by payment method (**cash, e-wallet, credit card**).  
  - The percentage ratio helps to understand which payment method prevails.  

- Average price by product category *(Average price | Product Line)*.  
  - The bar chart shows the average price of products in each product category (**fashion, electronics, food, etc.**).  

- Number of products sold by city *(Quantity | City & Product Line)*.  
  - The bar chart shows the distribution of products sold in three cities (**Mandalay, Naypyitaw, Yangon**).  
  - Color grouping shows the distribution by product category.  

- Currency filter *(Currency switch: UAH/USD)*  
  - Allows you to switch analytical indicators between the hryvnia and the US dollar using the exchange rate from the NBU API.


```DAX
Total by Currency = IF(MAX('Currency'[Currency]) = "UAH";SUM('supermarket_sales - Sheet1 (1)'[Total])*SUM(Cur[rate]);SUM('supermarket_sales - Sheet1 (1)'[Total]))
Monthly Revenue = CALCULATE(SUM('supermarket_sales - Sheet1 (1)'[Total]);'supermarket_sales - Sheet1 (1)'[Date])
Averege pricce = IF(Max('Currency'[Currency]) = "UAH";AVERAGE('supermarket_sales - Sheet1 (1)'[Unit price]) * SUM(Cur[rate]);AVERAGE('supermarket_sales - Sheet1 (1)'[Unit price])) 
