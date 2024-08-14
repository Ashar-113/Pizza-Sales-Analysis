# Pizza-Sales-Analysis

## Dashboard Summary
This dashboard gives insights into a pizzeria. This dashboard answers the most loved products and least loved products by the customers. Moreover, it illustrates the sales trend, peak hours in a day, etc. It also shows the KPIs such as how many orders this pizzeria receives in a day and how many products they sell per order. It is observed that their least-loved pizzas come from the veggie category. Furthermore, this pizzeria receives an average of 60 orders per day meanwhile selling an average of two pizzas per order.

## Data Preparation and Modelling
This dataset consists of multiple tables hence, containing information on multiple aspects of the pizzeria. The information on sales, pizza size and category, peak hours of the business, etc. The dataset was loaded into the Power Query to clean or transform the data to produce meaningful insights. Checking for data types and null values is also a part of data cleaning and sorting which gave a reason to make a date table which will be discussed in the section below.
### Data Modelling
Working with multiple tables requires building relationships among the tables so that it becomes viable to evaluate metrics across all the tables while designing the dashboard. This data model has relationships among _Order id_, _pizza id_, and _pizza id type_. These values are common among all the tables hence connecting the tables. Since this dashboard involves analysing the sales trend, it is evident that a date should be designed to correspond with the dates provided in the dataset. DAX expressions are used to make this date table and other measures to evaluate the KPIs therefore the data type is accurate for the analysis and convenient in building a relationship with the table with the data existing in it related to dates. DAX expression is as follows:
```
Date Table = ADDCOLUMNS(
     CALENDAR(MIN(Orders[Date]), MAX(Orders[Date])),
     "Year", YEAR([Date]),
     "Month", FORMAT([Date], "mmm"),
     "Month No.", MONTH([Date]),
     "Quater", FORMAT([Date], "\QQ"),
     "Day", FORMAT([Date], "ddd"),
     "Day No.", WEEKDAY([Date])
)
```
#
![Model](https://github.com/user-attachments/assets/d7c57465-2c39-4ed8-9c6f-c7f037ec45f3)
### Measure Table
The measure table consists of DAX expressions to evaluate the KPIs, for gathering key insights from the dataset.
#
**Total Sales:** To calculate total sales for this dataset, the cost is multiplied by the quantity sold for a specific _Order id_. It is expressed in a DAX expression as follows:
```
Total Sales = 
SUMX(
    'Order Details', 'Order Details'[Quantity] * RELATED(Pizzas[Price])
)
```
**Average Orders in a Day:** To determine how many pizzas were sold in a day order expression is as follows:
```
Avg. orders in a day = DIVIDE(
     DISTINCTCOUNT('Order Details'[Order Id]),
     DISTINCTCOUNT(Orders[Date])
)
```
**Average Pizza per Order:** To evaluate how many pizzas were sold per order the expression is:
```
Avg. pizzas per order = DIVIDE(
     DISTINCTCOUNT('Order Details'[Order Details Id]),
     DISTINCTCOUNT(Orders[Order Id])
)
```
**Total Orders:** The total amount of orders present in the dataset is given by:
```
Order Count = DISTINCTCOUNT('Order Details'[Order Id])
```

## Dashboard Overview
This dashboard has visualisations that give a clear insight into the sales trend of this pizzeria, the trend of busy days in a week their peak hours during the day, what is their most sold category and size. This dashboard also highlights the products that are most sold and least sold. This gives insights and the ability to make a business decision regarding which product can be eliminated from the menu. The dashboard also has filters by size and category to get deeper insights so that stakeholders can make sense of the data not just accumulatively but based on individual categories and sizes. Another filter for the five most loved and least loved products is added to toggle between the tables to show the sales amount for the most sold and least sold pizzas.
#
![filter](https://github.com/user-attachments/assets/98bdea2c-7b63-4f02-a3e6-b9f94c92d748)
#
![Toggle](https://github.com/user-attachments/assets/f46897c8-5f62-41dd-8391-62f06a04d3ab)
#
![pizza](https://github.com/user-attachments/assets/4a8735f6-4367-4097-b723-9bff828f3a31)
