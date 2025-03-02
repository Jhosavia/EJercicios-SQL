# EJercicios-SQL
  ** BASIC **
Lesson 101 - SQL TUTORIAL INTRO
Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns.
    SELECT user_id, stars FROM reviews WHERE stars = 3;
    
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
     SELECT card_name, MAX(issued_amount) - MIN(issued_amount) AS difference FROM monthly_cards_issued
     GROUP BY card_name ORDER BY difference DESC;
   *SQL Math Practice Exercise: Big-Mover Months
Display the stocks which had "big-mover months", and how many of those months they had. Order your results
from the stocks with the most, to least, "big-mover months"
     SELECT ticker, COUNT(ticker) FROM stock_prices WHERE (close - open)/open > 0.10 
     OR (close - open)/open < -0.10 GROUP BY ticker ORDER BY count DESC;   

Lesson 207
6. *SQL MATH FUNCTIONS Practice Exercise
Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
For all Merck drugs, output the drug name, and the unit cost for each drug, rounded up to the nearest
dollar. Order it from cheapest to most expensive drug.
Hint: Unit cost is defined as the total sales divided by the units sold.
   SELECT drug, CEIL(total_sales / units_sold) AS unit_cost FROM pharmacy_sales
   WHERE manufacturer = 'Merck' ORDER BY unit_cost ASC;

Lesson 208
7. *SQL DIVISION Practice Exercise
-----Cuenta Premium------

Lesson 209
8. *SQL NULL Practice Exercise
Tesla is investigating production bottlenecks and they need your help to extract the relevant data. Write a query to determine which parts have begun the assembly process but are not yet finished.
     SELECT part, assembly_step FROM parts_assembly WHERE finish_date IS NULL;

Lesson 210
9. *SQL CASE Tutorial Lesson: Superheroes' Likes
Explore the Marvel Avengers dataset and write a query to categorize superheroes based on their average likes as follows:
 - Super Likes: Superheroes with an average likes count greater than or equal to 15,000.
 - Good Likes: Superheroes with an average likes count between 5,000 and 14,999 (inclusive).
 - Low Likes: Superheroes with an average likes count less than 5,000.
Display the actor and character's name, platform, average likes, and the corresponding likes category. Sort the results by average likes.
     SELECT actor, character, platform, avg_likes, CASE WHEN avg_likes >= 15000 THEN 'Super Likes'
     WHEN avg_likes BETWEEN 5000 AND 14999 THEN 'Good Likes' ELSE 'Low Likes' END AS likes_category
     FROM marvel_avengers ORDER BY avg_likes DESC;
   *SQL CASE Laptop vs. Mobile Viewership
Assume you're given the table on user viewership categorised by device type where the three types are laptop, tablet, and phone.
Write a query that calculates the total viewership for laptops and mobile devices where mobile is defined as the sum of tablet and phone viewership. Output the total viewership for laptops as laptop_reviews and the total viewership for mobile devices as mobile_views.
      SELECT SUM(CASE WHEN device_type = 'laptop' THEN 1 ELSE 0 END) AS laptop_views, 
      SUM(CASE WHEN device_type IN ('tablet', 'phone') THEN 1 ELSE 0 END) AS mobile_views FROM viewership;

Lesson 211
10. *SQL JOINS Practice Exercise
Assume you're given the tables containing info about Robinhood users, and the stock trades they placed.
Use a JOIN to output all the information from the trades table joined to the users table.
     SELECT * FROM trades INNER JOIN users ON trades.user_id = users.user_id
    *SQL JOINS Cities With Completed Trades
Assume you're given the tables containing completed trade orders and user details in a Robinhood trading system.
Write a query to retrieve the top three cities that have the highest number of completed trade orders listed in
descending order. Output the city name and the corresponding number of completed trade orders.
      SELECT users.city, COUNT(trades.order_id) AS total_orders FROM trades INNER JOIN users ON trades.user_id = users.user_id
      WHERE trades.status = 'Completed' GROUP BY users.city ORDER BY total_orders DESC LIMIT 3;
    *SQL JOINS Page With No Likes
Assume you're given two tables containing data about Facebook Pages and their respective likes (as in "Like a Facebook Page").
Write a query to return the IDs of the Facebook pages that have zero likes. The output should be sorted in ascending order based on the page IDs.
      SELECT pages.page_id FROM pages LEFT OUTER JOIN page_likes AS likes ON pages.page_id = likes.page_id WHERE likes.page_id IS NULL;

Lesson 212
11. *SQL DATE FUNCTIONS Practice Exercise
   *Average Post Hiatus (Part 1)
Given a table of Facebook posts, for each user who posted at least twice in 2021, write a query to find the number of days
between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the
days between each user's first and last post.
      SELECT user_id, MAX(post_date::DATE) - MIN(post_date::DATE) AS days_between FROM posts
      WHERE DATE_PART('year', post_date::DATE) = 2021 GROUP BY user_id HAVING COUNT(post_id)>1;
     *SQL Second Day Confirmation
Assume you're given tables with information about TikTok user sign-ups and confirmations through email and text. New users on TikTok sign up using their email addresses, and upon sign-up, each user receives a text message confirmation to activate their account.
Write a query to display the user IDs of those who did not confirm their sign-up on the first day, but confirmed on the second day.
      SELECT DISTINCT user_id FROM emails INNER JOIN texts ON emails.email_id = texts.email_id
      WHERE texts.action_date = emails.signup_date + INTERVAL '1 day' AND texts.signup_action = 'Confirmed';
