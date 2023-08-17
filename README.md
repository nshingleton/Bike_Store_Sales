# Bike Store Sales Query

Here is the query I used to extract a dataset for my Bike Store Sales analysis. The [link](https://public.tableau.com/app/profile/naomi.shingleton/viz/BikeStoresDashboard_16906594631380/Dashboard1) to the Tableau Dashboard can be found below as well.

This data was obtained from the company's relational database and retrieved using SQL. The script generated a dataset with the fields: order ID, customer's first and last name, the customer's city and state, the order date, sales volume, revenue, product name, product category, brand name, store name, and sales rep. The fields were dispersed across nine different tables in the bike stores database. So this query performed a series of multiple direct
and indirect table joins to generate the exact data necessary for the analysis.

Here is an in depth description of the query:

At the beginning of the script, I took the two separate fields "first name"
and "last name" and concatenated them together to create one field, with the alias “customers”.

The "order ID" and "order date" are contained in the sales.orders table. The customer's
first name, last name, city and state are contained in the sales.customers table. I joined these two tables on their customer ID field. 

To obtain the sales volume I used SUM(ite.quantity) with the alias "total_units". For total revenue generated I used SUM(ite.quantity * ite.list_price) with the alias "revenue".

The quantity and list price fields are contained in the sales.order_items table. I joined this table to the sales.orders table on the order ID field.

To find the name of the products that were purchased I joined the productions.product table to the sales.order_items table on the product ID field.

To find the category of the products that were purchased I selected the category name field. This field is found in the production.categories table. I joined this table with the productions.product table on the category ID field.

To find the store name, I selected the store name field, which is found in the sales.stores table and joined this to the sales.orders table on the store ID field.

To find the sales rep that made the sale, I used the CONCAT function again to merge the first and last name of the rep into just one field. I then used the alias “sales_rep”. The first and last name fields are in the sales.staffs table which I joined to the sales.orders table on the staff ID field.

Because there are functions in the query, I used the GROUP BY function so that the query executes properly.

Description of files:

- [SQL Script](https://github.com/nshingleton/Bike_Store_Sales/blob/main/BikeStoresQuery.sql)- This is the script executed to obtain the unique dataset needed to complete the analysis.

- [Dashboard](https://public.tableau.com/app/profile/naomi.shingleton/viz/BikeStoresDashboard_16906594631380/Dashboard1)- This is a custom interactive dashboard displaying bike sales metrics to the executive team.
