# Pizza Sales Analysis

## Project Overview
This case study presents an interactive dashboard built for a fictional pizza restaurant. The goal was to help the business owners clarify their sales patterns, product performance, and customer behaviour.

The dashboard answers questions such as:

What are the most and least popular pizza types?

What times of the day are the busiest?

How many orders and pizzas are sold daily?

Key takeaway: Veggie pizzas were the least popular, and the restaurant averages 60 orders per day, selling around 2 pizzas per order.

## How Data Was Prepared
The dataset contained several tables with information on orders, pizza types, and pricing. The data was cleaned and prepared using Power BI's built-in Power Query tool. Steps included:

Checking for missing or incorrect values

Ensuring dates and numbers were formatted correctly

Creating a "date table" to allow proper time-based analysis (e.g., daily, monthly, quarterly trends)

A key formula used to generate the date table was:
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
This allowed the dashboard to organise and filter data by year, month, day, and weekday.
#
![Model](https://github.com/user-attachments/assets/d7c57465-2c39-4ed8-9c6f-c7f037ec45f3)

## What Dashboard Shows
**Sales Over Time:** View trends and spot busy or slow periods.

**Peak Hours:** Shows what times of the day bring in the most orders.

**Top & Bottom Products:** Easy-to-read tables show which pizzas are best-sellers and which are underperforming.

**Category & Size Filters:** The dashboard includes options to focus only on certain types (like classic or veggie pizzas) or sizes (small, medium, large).

**Toggle Switch:** Lets users flip between most-loved and least-loved products with one click.

## Business Insights
**The dashboard revealed:**

Veggie pizzas were consistently the least loved and may be candidates for removal.

Evenings (6 – 8 PM) were peak ordering times, useful for staff scheduling.

The restaurant averaged 60 orders daily and 2 pizzas per order, helping with inventory planning.
## Dashboard Visuals
#
![filter](https://github.com/user-attachments/assets/98bdea2c-7b63-4f02-a3e6-b9f94c92d748)
#
![Toggle](https://github.com/user-attachments/assets/f46897c8-5f62-41dd-8391-62f06a04d3ab)
#
![pizza](https://github.com/user-attachments/assets/4a8735f6-4367-4097-b723-9bff828f3a31)
