# EJercicios-SQL
1. *SQL SELECT Practice Exercise
   Your given a products table, which contains data about different Microsoft Azure cloud products.
   SELECT * FROM products;
3. *SQL WHERE Practice Exercise
  Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause.
  Only display the user_id and stars columns.
   SELECT user_id, stars FROM reviews WHERE stars = 3;
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
Pro Tip: Try coding up, and executing, each filtering condition, one at a time. It's too easy to try to code this all up in one go, and mess something up!
6. *SQL BETWEEN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the BETWEEN SQL command to find data on medicines:
    - which sold between 100,000 units and 105,000 units
    - AND were manufactured by either Biogen, AbbVie, or Eli Lilly
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE units_sold BETWEEN 100000 AND 105000
   AND (manufacturer = 'Eli Lilly' OR manufacturer = 'AbbVie' OR manufacturer = 'Biogen');
7. *SQL IN Practice Exercise
   Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
   Use the IN SQL command to find data on medicines:
    - which were manufactured by either Roche, Bayer, or AstraZeneca
    - and did not sell between 55,000 and 550,000 units
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE manufacturer  
   IN ('Roche', 'Bayer', 'AstraZeneca') AND NOT units_sold BETWEEN 55000 AND 550000;
Output the manufacturer name, drug name, and the # of units sold. for all the medicines which match that criteria.
8. *SQL LIKE Practice Exercise
11. *SQL Practice Exercise
