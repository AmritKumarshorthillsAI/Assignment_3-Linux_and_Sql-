# Assignment_3-Linux_and_Sql-

**SQL Exercise**
**1) Filtering and Sorting:**
To Create a table called orders with the following columns: order_id, customer_id, order_date, total_amount the following query can be executed:
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2)
);

To insert records following query can be executed:
INSERT INTO orders (order_id, customer_id, order_date, total_amount) VALUES
(1, 101, '2023-09-01', 350),
(2, 102, '2023-08-15', 600),
(3, 103, '2023-09-21', 150),
(4, 104, '2023-07-30', 75),
(5, 101, '2023-08-25', 480),
(6, 105, '2023-09-18', 250),
(7, 106, '2023-07-29', 500);

Query to select orders where the total_amount is between $100 and $500 and then Sort the results by total_amount in ascending order.
After that extend the query to filter orders placed in the last 30 days
where clause is used for filtering and order by clause for sorting
SELECT *
FROM orders
WHERE total_amount BETWEEN 100 AND 500
AND order_date >= (SELECT MAX(order_date) FROM orders) - INTERVAL 30 DAY
ORDER BY total_amount ASC;

**2. Join with Multiple Tables:**
Created customers and products and then inserted data given in excel file of assignment

To join customers and orders the customer_id column is used, and then to display the customer_name and their corresponding total order amount group by clause is used 
SELECT 
    c.customer_name,
    SUM(o.total_amount) AS total_order_amount
FROM customers c
JOIN orders o 
ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
