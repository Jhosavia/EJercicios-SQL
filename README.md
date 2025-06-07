# EJercicios-SQL
#  ** BASIC **

# Lesson 101 - SQL TUTORIAL INTRO
Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns.

    SELECT user_id, stars FROM reviews WHERE stars = 3;
    
# Lesson 102

1. *SQL SELECT Practice Exercise
   Your given a products table, which contains data about different Microsoft Azure cloud products.
   
   SELECT * FROM products;

# Lesson 103

3. *SQL WHERE Practice Exercise
  Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause.
  Only display the user_id and stars columns.
  
   SELECT user_id, stars FROM reviews WHERE stars = 3;

# Lesson 104

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

    SELECT * FROM reviews WHERE stars > 2 AND stars <=4 AND (user_id = 123 OR user_id =265 OR user_id = 362);

# Lesson 105

6. *SQL BETWEEN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the BETWEEN SQL command to find data on medicines:
    - which sold between 100,000 units and 105,000 units
    - AND were manufactured by either Biogen, AbbVie, or Eli Lilly
   
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE units_sold BETWEEN 100000 AND 105000
   AND (manufacturer = 'Eli Lilly' OR manufacturer = 'AbbVie' OR manufacturer = 'Biogen');

# Lesson 106

7. *SQL IN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the IN SQL command to find data on medicines:
    - which were manufactured by either Roche, Bayer, or AstraZeneca
    - and did not sell between 55,000 and 550,000 units
   
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE manufacturer  
   IN ('Roche', 'Bayer', 'AstraZeneca') AND NOT units_sold BETWEEN 55000 AND 550000;

# Lesson 107

8. *SQL LIKE % Practice Exercise
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers whose first name starts with "F" and the last letter in their last name is "ck".
     
     SELECT * FROM customers WHERE customer_name LIKE 'F%ck' ;

9. *SQL LIKE _ Practice Exercise
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers where the 2nd and 3rd letter in their name is "e".

      SELECT * FROM customers WHERE customer_name LIKE '_ee%';

# Lesson 108

10. *SQL Filtering Practice Exercise #1
   You have a table of 1000 customer records from a small-business based in Australia.
   Find all customers who are between the ages of 18 and 22 (inclusive), live in either Victoria, Tasmania,
   Queensland, their gender isn't "n/a", and their name starts with either 'A' or 'B'.
     
     SELECT * FROM customers WHERE age BETWEEN 18 AND 22 AND state IN ('Tasmania', 'Queensland', 'Victoria')
     AND gender != 'n/a' AND (customer_name LIKE 'A%' OR customer_name LIKE 'B%');

# Lesson 109

11. *SQL ORDEN BY
    ORDEN BY colum ASC
    ORDEN BY colum DES
    
------------------------------------
#  ** INTERMEDIO **
Lesson 201 INTERMEDIATE SQL

# Lesson 202  
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

# Lesson 203
2. *SQL GROUP BY Practice Exercise
For every FAANG stock in the stock_prices dataset, write a SQL query to find the lowest price each stock ever
opened at? Be sure to also order your results by price, in descending order.
   
     SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker ORDER BY min DESC;
   
   *SQL GROUP BY Practice Exercise: Candidate Skills
Suppose you are given a table of candidates and their skills. How many candidates possess each of the
different skills? Sort your answers based on the count of candidates, from highest to lowest.
   
     SELECT skill, COUNT(candidate_id) FROM candidates GROUP BY skill ORDER BY count DESC;

# Lesson 204

3. *SQL HAVING MIN Practice Exercise
  Use SQL's HAVING & MIN commands to find all FAANG stocks whose open share price was always greater than $100.
    
    SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker HAVING MIN(open) > 100;
   
   *SQL HAVING Practice Exercise
  Given a table of candidates and their technical skills, list the candidate IDs of candidates who have more than 2 technical skills.
     
     SELECT candidate_id FROM candidates GROUP BY candidate_id HAVING COUNT(candidate_id) > 2; 

# Lesson 205

5. *SQL DISTINCT Practice Exercise
    Assume you're given a table containing data on Amazon customers and their spending on
    products in different category. Write a query using COUNT DISTINCT to identify the number
    of unique products within each product category.
       
       SELECT category, COUNT (DISTINCT product) FROM product_spend GROUP BY category;

# Lesson 206

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

# Lesson 207

6. *SQL MATH FUNCTIONS Practice Exercise
Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
For all Merck drugs, output the drug name, and the unit cost for each drug, rounded up to the nearest
dollar. Order it from cheapest to most expensive drug.
Hint: Unit cost is defined as the total sales divided by the units sold.
   
   SELECT drug, CEIL(total_sales / units_sold) AS unit_cost FROM pharmacy_sales
   WHERE manufacturer = 'Merck' ORDER BY unit_cost ASC;

# Lesson 208

7. *SQL DIVISION Practice Exercise
-----Cuenta Premium------

# Lesson 209

8. *SQL NULL Practice Exercise
Tesla is investigating production bottlenecks and they need your help to extract the relevant data. Write a query to determine which parts have begun the assembly process but are not yet finished.
    
     SELECT part, assembly_step FROM parts_assembly WHERE finish_date IS NULL;

# Lesson 210

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

# Lesson 211

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

# Lesson 212

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

#  ** ADVANCED SQL **

# Lesson 301 ADVANCED INTRO
We are going to go deeper into the SQL abyss in the advanced SQL tutorial, and start to cover material that typical SQL tutorials don't teach.

We'll cover higher-level concepts such as:

how to write clean, maintainable SQL
what's happening inside a database when a SQL query runs
how to pivot & unpivot data in SQL (similar to Excel)
Most importantly, we'll put it all together to solve a real Instacart SQL Data Analytics case study, where we'll write long SQL queries to solve an open-ended business problem.

# Lesson 302 CTE vs. SUBQUERY

1. SQL Tutorial Lesson: Top-Selling Artists
   
As the lead data analyst for a prominent music event management company, you have been entrusted with a dataset containing concert revenue and detailed information about various artists.

Your mission is to unlock valuable insights by analyzing the concert revenue data and identifying the top revenue-generating artists within each music genre.

Write a query to rank the artists within each genre based on their revenue per member and extract the top revenue-generating artist from each genre. Display the output of the artist name, genre, concert revenue, number of members, and revenue per band member, sorted by the highest revenue per member within each genre.

WITH ranked_concerts_cte AS (
  SELECT artist_name, concert_revenue, genre, number_of_members,
    concert_revenue / number_of_members AS revenue_per_member,
    RANK() OVER ( PARTITION BY genre
      ORDER BY concert_revenue / number_of_members DESC) AS ranked_concerts FROM concerts
)
SELECT artist_name, concert_revenue, genre, number_of_members,
  revenue_per_member FROM ranked_concerts_cte
WHERE ranked_concerts = 1
ORDER BY revenue_per_member DESC;

2. Supercloud Customer

A Microsoft Azure Supercloud customer is defined as a customer who has purchased at least one product from every product category listed in the products table.

Write a query that identifies the customer IDs of these Supercloud customers.

WITH supercloud_cust AS (
  SELECT customers.customer_id, 
    COUNT(DISTINCT products.product_category) AS product_count
  FROM customer_contracts AS customers INNER JOIN products 
    ON customers.product_id = products.product_id
  GROUP BY customers.customer_id
)
SELECT customer_id
FROM supercloud_cust
WHERE product_count = (
  SELECT COUNT(DISTINCT product_category) FROM products
);

3. Swapped Food Delivery

Zomato is a leading online food delivery service that connects users with various restaurants and cuisines, allowing them to browse menus, place orders, and get meals delivered to their doorsteps.

Recently, Zomato encountered an issue with their delivery system. Due to an error in the delivery driver instructions, each item's order was swapped with the item in the subsequent row. As a data analyst, you're asked to correct this swapping error and return the proper pairing of order ID and item.

If the last item has an odd order ID, it should remain as the last item in the corrected data. For example, if the last item is Order ID 7 Tandoori Chicken, then it should remain as Order ID 7 in the corrected data.

In the results, return the correct pairs of order IDs and items.

WITH order_counts AS (
  SELECT COUNT(order_id) AS total_orders FROM orders
)
SELECT
  CASE
    WHEN order_id % 2 != 0 AND order_id != total_orders THEN order_id + 1
    WHEN order_id % 2 != 0 AND order_id = total_orders THEN order_id
    ELSE order_id - 1
  END AS corrected_order_id, item
FROM orders
CROSS JOIN order_counts
ORDER BY corrected_order_id;

# Lesson 303 WINDOW FUNCTION

*Card Launch Success

Your team at JPMorgan Chase is soon launching a new credit card. You are asked to estimate how many cards you'll issue in the first month.

Before you can answer this question, you want to first get some perspective on how well new credit card launches typically do in their first month.

Write a query that outputs the name of the credit card, and how many cards were issued in its launch month. The launch month is the earliest record in the monthly_cards_issued table for a given card. Order the results starting from the biggest issued amount.

WITH card_launch AS (
  SELECT card_name, issued_amount,
    MAKE_DATE(issue_year, issue_month, 1) AS issue_date,
    MIN(MAKE_DATE(issue_year, issue_month, 1)) OVER (
      PARTITION BY card_name) AS launch_date
  FROM monthly_cards_issued
)
SELECT card_name, issued_amount FROM card_launch
WHERE issue_date = launch_date
ORDER BY issued_amount DESC;

# Lesson 304 SQL RANKING

1. *Top 5 Artists

Assume there are three Spotify tables: artists, songs, and global_song_rank, which contain information about the artists, songs, and music charts, respectively.

Write a query to find the top 5 artists whose songs appear most frequently in the Top 10 of the global_song_rank table. Display the top 5 artist names in ascending order, along with their song appearance ranking.

If two or more artists have the same number of song appearances, they should be assigned the same ranking, and the rank numbers should be continuous (i.e. 1, 2, 2, 3, 4, 5). If you've never seen a rank order like this before, do the rank window function tutorial.

WITH top_10_cte AS (
  SELECT artists.artist_name,
    DENSE_RANK() OVER (
      ORDER BY COUNT(songs.song_id) DESC) AS artist_rank
  FROM artists
  INNER JOIN songs
    ON artists.artist_id = songs.artist_id
  INNER JOIN global_song_rank AS ranking
    ON songs.song_id = ranking.song_id
  WHERE ranking.rank <= 10
  GROUP BY artists.artist_name
)
SELECT artist_name, artist_rank
FROM top_10_cte
WHERE artist_rank <= 5;

2. *Histogram of Users and Purchases

This is the same question as problem #13 in the SQL Chapter of Ace the Data Science Interview!

Assume you're given a table on Walmart user transactions. Based on their most recent transaction date, write a query that retrieve the users along with the number of products they bought.

Output the user's most recent transaction date, user ID, and the number of products, sorted in chronological order by the transaction date.

WITH latest_transactions_cte AS (
  SELECT transaction_date, user_id, product_id, 
    RANK() OVER ( PARTITION BY user_id 
      ORDER BY transaction_date DESC) AS transaction_rank 
  FROM user_transactions) 
SELECT transaction_date, user_id,
  COUNT(product_id) AS purchase_count
FROM latest_transactions_cte
WHERE transaction_rank = 1 
GROUP BY transaction_date, user_id
ORDER BY transaction_date;

3. *Odd and Even Measurements

This is the same question as problem #28 in the SQL Chapter of Ace the Data Science Interview!

Assume you're given a table with measurement values obtained from a Google sensor over multiple days with measurements taken multiple times within each day.

Write a query to calculate the sum of odd-numbered and even-numbered measurements separately for a particular day and display the results in two different columns. Refer to the Example Output below for the desired format.

Definition:

Within a day, measurements taken at 1st, 3rd, and 5th times are considered odd-numbered measurements, and measurements taken at 2nd, 4th, and 6th times are considered even-numbered measurements.
Effective April 15th, 2023, the question and solution for this question have been revised.

WITH ranked_measurements AS (
  SELECT 
    CAST(measurement_time AS DATE) AS measurement_day, 
    measurement_value, 
    ROW_NUMBER() OVER (
      PARTITION BY CAST(measurement_time AS DATE) 
      ORDER BY measurement_time) AS measurement_num 
  FROM measurements
) 

SELECT measurement_day, 
  SUM(measurement_value) FILTER (WHERE measurement_num % 2 != 0) AS odd_sum, 
  SUM(measurement_value) FILTER (WHERE measurement_num % 2 = 0) AS even_sum 
FROM ranked_measurements
GROUP BY measurement_day;

# Lesson 305 SQL LEAD LAG

*Y-on-Y Growth Rate
This is the same question as problem #32 in the SQL Chapter of Ace the Data Science Interview!

Assume you're given a table containing information about Wayfair user transactions for different products. Write a query to calculate the year-on-year growth rate for the total spend of each product, grouping the results by product ID.

The output should include the year in ascending order, product ID, current year's spend, previous year's spend and year-on-year growth percentage, rounded to 2 decimal places.

WITH yearly_spend_cte AS (
  SELECT EXTRACT(YEAR FROM transaction_date) AS year, product_id,
    spend AS curr_year_spend,
    LAG(spend) OVER (
      PARTITION BY product_id 
      ORDER BY product_id, 
        EXTRACT(YEAR FROM transaction_date)) AS prev_year_spend 
  FROM user_transactions
)

SELECT year, product_id, curr_year_spend, prev_year_spend, 
  ROUND(100 * (curr_year_spend - prev_year_spend)/ prev_year_spend
  , 2) AS yoy_rate FROM yearly_spend_cte;

# Lesson 306 SQL SELF-JOINS with Examples

Finding Similar Books Within the Same Genre
Here's the query that generates meaningful book recommendations:

SELECT
  b1.genre,
  b1.book_title AS current_book,
  b2.book_title AS suggested_book
FROM goodreads AS b1
INNER JOIN goodreads AS b2
  ON b1.genre = b2.genre
WHERE b1.book_id != b2.book_id
ORDER BY b1.book_title;

# Lesson 307 SQL UNION, INTERCEPT, EXCEPT with

1. *Maximize Prime Item Inventory

Effective April 3rd 2024, we have updated the problem statement to provide additional clarity.

Amazon wants to maximize the storage capacity of its 500,000 square-foot warehouse by prioritizing a specific batch of prime items. The specific prime product batch detailed in the inventory table must be maintained.

So, if the prime product batch specified in the item_category column included 1 laptop and 1 side table, that would be the base batch. We could not add another laptop without also adding a side table; they come all together as a batch set.

After prioritizing the maximum number of prime batches, any remaining square footage will be utilized to stock non-prime batches, which also come in batch sets and cannot be separated into individual items.

WITH summary AS (
  SELECT 
    SUM(square_footage) FILTER (WHERE item_type = 'prime_eligible') AS prime_sq_ft,
    COUNT(item_id) FILTER (WHERE item_type = 'prime_eligible') AS prime_item_count,
    SUM(square_footage) FILTER (WHERE item_type = 'not_prime') AS not_prime_sq_ft,
    COUNT(item_id) FILTER (WHERE item_type = 'not_prime') AS not_prime_item_count
  FROM inventory
),
prime_occupied_area AS (
  SELECT FLOOR(500000/prime_sq_ft)*prime_sq_ft AS max_prime_area
  FROM summary
)
SELECT 'prime_eligible' AS item_type,
  FLOOR(500000/prime_sq_ft)*prime_item_count AS item_count
FROM summary
UNION ALL
SELECT 'not_prime' AS item_type,
  FLOOR((500000-(SELECT max_prime_area FROM prime_occupied_area)) 
    / not_prime_sq_ft) * not_prime_item_count AS item_count
FROM summary;

2. *Page With No Likes

Assume you're given two tables containing data about Facebook Pages and their respective likes (as in "Like a Facebook Page").

Write a query to return the IDs of the Facebook pages that have zero likes. The output should be sorted in ascending order based on the page IDs.

SELECT page_id FROM pages EXCEPT SELECT page_id FROM page_likes;

# Lesson 308 WRITE CLEAN SQL examples

Consistent Formatting and Indentation
Want your queries to be easier on the eyes? Keep your formatting consistent. Use spaces or tabs throughout, and things will look neater.
For example, avoid this:

WITH product_sales AS (
SELECT
product_id,
  SUM(sales_amount) AS total_sales
FROM sales
GROUP BY product_id
  )
SELECT
products.product_name,
sales.total_sales
FROM products
  INNER JOIN product_sales sales ON products.product_id = sales.product_id
Instead, write like this:
WITH product_sales AS (
  SELECT
    product_id,
    SUM(sales_amount) AS total_sales
  FROM sales
  GROUP BY product_id)
SELECT
  products.product_name,
  sales.total_sales
FROM products
INNER JOIN product_sales AS sales
  ON products.product_id = sales.product_id;
💡 A little tip: You can also use a code formatter tool to automatically apply a style to your code.

# Lesson 309 EXECUTION ORDER

Example Illustrating SQL Order of Execution
Let's consider an example query:

SELECT product_category, AVG(price) AS avg_price
FROM products
WHERE stock_quantity > 0
GROUP BY product_category
HAVING AVG(price) > 50
ORDER BY avg_price DESC
LIMIT 5;

# Lesson 310 SQL PIVOTING

Unpivoting SQL Example: Converting Columnnar Engagement Metrics to Individual Platforms
We've learned to pivot from rows to columns, but how about unpivoting from columns to rows?
In this case, we use the CASE statement with multiple conditions to selectively assign the engagement rate corresponding to the respective social media platforms.

SELECT superhero_alias, platform,
  CASE platform
    WHEN 'Instagram' THEN engagement_rate
    WHEN 'Twitter' THEN engagement_rate
    WHEN 'YouTube' THEN engagement_rate
    WHEN 'TikTok' THEN engagement_rate
  END AS engagement_rate FROM marvel_avengers
WHERE superhero_alias IN ('Iron Man', 'Captain America', 'Black Widow', 'Thor')
ORDER BY superhero_alias;

# Lesson 311 STRING FUNCTIONS

1. *SQL LOWER Practice Exercise

Assume you're given the customer table containing all customer details.
The branch manager is looking for a male customer whose name ends with "son" and he's 20 years old.
Write a SQL query which uses LOWER and LIKE to find this customer's details.

SELECT * FROM customers
WHERE LOWER(customer_name) LIKE '%son'
  AND gender = 'Male'
  AND age = 20;

2. *Pharmacy Analytics (Part 3)

CVS Health wants to gain a clearer understanding of its pharmacy sales and the performance of various products.

Write a query to calculate the total drug sales for each manufacturer. Round the answer to the nearest million and report your results in descending order of total sales. In case of any duplicates, sort them alphabetically by the manufacturer name.

Since this data will be displayed on a dashboard viewed by business stakeholders, please format your results as follows: "$36 million".

WITH drug_sales AS (
  SELECT manufacturer, SUM(total_sales) as sales 
  FROM pharmacy_sales GROUP BY manufacturer
) 
SELECT manufacturer, 
  ('$' || ROUND(sales / 1000000) || ' million') AS sales_mil 
FROM drug_sales ORDER BY sales DESC, manufacturer;

# Lesson 312 INSTACART SQL CASE



