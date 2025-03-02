# EJercicios-SQL
  ** BASIC **
Lesson 101
Lesson 102
1. *SQL SELECT Practice Exercise
   Your given a products table, which contains data about different Microsoft Azure cloud products.
   SELECT * FROM products;
Lesson 103
3. *SQL WHERE Practice Exercise
  Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause.
  Only display the user_id and stars columns.
   SELECT user_id, stars FROM reviews WHERE stars = 3;
Lesson 104
4. *SQL WHERE AND Practice Exercise
   Let's practice using AND along with WHERE to filter Amazon reviews based on all 4 of these conditions:
    - the review should have 4 or more stars
    - the review ID is less than 6000
    - the review ID is more than 2000
     the review can't come from user 142
    SELECT * FROM reviews WHERE stars>=4 AND review_id > 2000 AND review_id < 6000 AND user_id<>142;
5. *SQL WHERE AND OR Practice Exercise
    Let's practice using AND along with WHERE to filter Amazon reviews based on these two conditions:
    - the start count is greater than 2, and less than or equal to 4
    - the review must come from either user 123, 265, or 362
Pro Tip: Try coding up, and executing, each filtering condition, one at a time. It's too easy to try to code this all up in one go, and mess something up!
  SELECT * FROM reviews WHERE stars > 2 AND stars <=4 AND (user_id = 123 OR user_id =265 OR user_id = 362);
Lesson 105
6. *SQL BETWEEN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the BETWEEN SQL command to find data on medicines:
    - which sold between 100,000 units and 105,000 units
    - AND were manufactured by either Biogen, AbbVie, or Eli Lilly
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE units_sold BETWEEN 100000 AND 105000
   AND (manufacturer = 'Eli Lilly' OR manufacturer = 'AbbVie' OR manufacturer = 'Biogen');
Lesson 106
7. *SQL IN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the IN SQL command to find data on medicines:
    - which were manufactured by either Roche, Bayer, or AstraZeneca
    - and did not sell between 55,000 and 550,000 units
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE manufacturer  
   IN ('Roche', 'Bayer', 'AstraZeneca') AND NOT units_sold BETWEEN 55000 AND 550000;
Lesson 107
8. *SQL LIKE % Practice Exercise
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers whose first name starts with "F" and the last letter in their last name is "ck".
     SELECT * FROM customers WHERE customer_name LIKE 'F%ck' ;
9. *SQL LIKE _ Practice Exercise
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers where the 2nd and 3rd letter in their name is "e".
     SELECT * FROM customers WHERE customer_name LIKE '_ee%';
Lesson 108
10. *SQL Filtering Practice Exercise #1
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers who are between the ages of 18 and 22 (inclusive), live in either Victoria, Tasmania,
   Queensland, their gender isn't "n/a", and their name starts with either 'A' or 'B'.
     SELECT * FROM customers WHERE age BETWEEN 18 AND 22 AND state IN ('Tasmania', 'Queensland', 'Victoria')
     AND gender != 'n/a' AND (customer_name LIKE 'A%' OR customer_name LIKE 'B%');
Lesson 109
11. *SQL ORDEN BY
    ORDEN BY colum ASC
    ORDEN BY colum DES
------------------------------------
  ** INTERMEDIO **
Lesson 201 INTERMEDIATE SQL
Lesson 202  
1. *SQL COUNT Practice Exercise
**Output the number of rows in the pharmacy_sales table. **
   SELECT COUNT(*) FROM pharmacy_sales;
   *SQL SUM Practice Exercise
 Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
 Output the total number of drugs manufactured by Pfizer, and output the total sales for all the Pfizer drugs.
    SELECT COUNT(*), SUM(total_sales) FROM pharmacy_sales WHERE manufacturer = 'Pfizer';
   *SQL AVG Practice Exercise
 Write a SQL query using AVG to find the average open price for Google stock (which has a stock ticker symbol of 'GOOG').
    SELECT AVG(open) FROM stock_prices WHERE ticker = 'GOOG';
   *SQL MIN Practice Exercise
 Use SQL's MIN command in this practice exercise, to find the lowest Microsoft stock (MSFT) ever opened at.
    SELECT MIN(open) FROM stock_prices WHERE ticker = 'MSFT';
   *SQL MAX Practice Exercise
 Use SQL's MAX command in this practice exercise, to find the highest Netflix stock (NFLX) ever opened at.
   SELECT MAX(open) FROM stock_prices WHERE ticker = 'NFLX';
Lesson 203
2. *SQL GROUP BY Practice Exercise
For every FAANG stock in the stock_prices dataset, write a SQL query to find the lowest price each stock ever
opened at? Be sure to also order your results by price, in descending order.
     SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker ORDER BY min DESC;
   *SQL GROUP BY Practice Exercise: Candidate Skills
Suppose you are given a table of candidates and their skills. How many candidates possess each of the
different skills? Sort your answers based on the count of candidates, from highest to lowest.
   SELECT skill, COUNT(candidate_id) FROM candidates GROUP BY skill ORDER BY count DESC;
Lesson 204
3. *SQL HAVING MIN Practice Exercise
  Use SQL's HAVING & MIN commands to find all FAANG stocks whose open share price was always greater than $100.
    SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker HAVING MIN(open) > 100;
   *SQL HAVING Practice Exercise
  Given a table of candidates and their technical skills, list the candidate IDs of candidates who have more than 2 technical skills.
     SELECT candidate_id FROM candidates GROUP BY candidate_id HAVING COUNT(candidate_id) > 2; 
Lesson 205
5. *SQL DISTINCT Practice Exercise
    Assume you're given a table containing data on Amazon customers and their spending on
    products in different category. Write a query using COUNT DISTINCT to identify the number
    of unique products within each product category.
       SELECT category, COUNT (DISTINCT product) FROM product_spend GROUP BY category;
Lesson 206
5. *SQL ARITHMETIC Practice Exercise
CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug
can only be produced by one manufacturer. Write a query to find the top 3 most profitable drugs sold, and how much profit
they made. Assume that there are no ties in the profits. Display the result from the highest to the lowest total profit.
     SELECT drug, total_sales - cogs AS total_profit FROM pharmacy_sales ORDER BY total_profit DESC LIMIT 3;
   *SQL Cards Issued Difference
Your team at JPMorgan Chase is preparing to launch a new credit card, and to gain some insights, you're analyzing how many
credit cards were issued each month. Write a query that outputs the name of each credit card and the difference in the number
of issued cards between the month with the highest issuance cards and the lowest issuance. Arrange the results based on the largest disparity.
    
   *SQL 

   
Lesson 207
6. *SQL MATH FUNCTIONS Practice Exercise


Lesson 208
7. *SQL DIVISION Practice Exercise


Lesson 209
8. *SQL NULL Practice Exercise


Lesson 210
9. *SQL CASE Practice Exercise


Lesson 211
10. *SQL JOINS Practice Exercise


Lesson 212
11. *SQL DATE FUNCTIONS Practice Exercise

