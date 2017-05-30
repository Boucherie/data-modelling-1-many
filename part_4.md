The data in this part of the assignment uses the authors, articles, countries, provinces, cities, residences, and persons tables from earlier in the assignment.

<!-- 1. Find the author with the name 'Kara Melton' and then select all the articles she has written. -->
SELECT id FROM authors WHERE name='Kara Melton';
 id
----
  8

SELECT title FROM articles WHERE author_id=8;

 How Tech Business Models Come From Marginalized Communities, But Startups Are Still Mostly White
 Confronting the Assumption of Whiteness in Virtual Spaces


<!-- 2. Find Ontario in the provinces table and then find all the cities in that province. -->

one_to_many_assignment=# SELECT id FROM provinces WHERE name='Ontario';
 id
----
 14

one_to_many_assignment=# SELECT name FROM cities WHERE province_id=14;
  name   
---------
 Toronto
 Ottawa

<!-- 3. Who wrote the article called 'Coding Bootcamps and Emotional Labor'? -->

one_to_many_assignment=# SELECT author_id FROM articles WHERE title='Coding Bootcamps and Emotional Labor';
 author_id
-----------
         4

one_to_many_assignment=# SELECT name FROM authors WHERE id=4;
       name        
-------------------
 Tilde Ann Thurium

<!-- 4. Write a series of SQL queries to find out how many provinces are in Canada. -->

one_to_many_assignment=# SELECT Count(name) FROM provinces;
 count
-------
    14

5. How many people live at 4740 McDermott Street?

one_to_many_assignment=# SELECT id FROM residences WHERE address='4740 McDermott Street';
 id
----
  9

one_to_many_assignment=# SELECT COUNT(name) FROM persons WHERE residence_id=9;
 count
-------
     2
OR
one_to_many_assignment=# SELECT name FROM persons WHERE residence_id=9;
     name     
--------------
 Malvina King
 Theo Wolff

<!-- 6. What city is 4740 McDermott Street in? -->

one_to_many_assignment=# SELECT city_id FROM residences WHERE id=9;
 city_id
---------
      11

one_to_many_assignment=# SELECT name FROM cities WHERE id=11;
  name  
--------
 Ottawa

<!-- 7. What province is 4740 McDermott Street in? -->

one_to_many_assignment=# SELECT province_id FROM cities WHERE id=11;
 province_id
-------------
          14

one_to_many_assignment=# SELECT name FROM provinces WHERE id=14;
  name   
---------
 Ontario


<!-- 8. What country is 4740 McDermott Street in? -->

one_to_many_assignment=# one_to_many_assignment=# SELECT country_id FROM provinces WHERE id=14;
 country_id
------------
          1
one_to_many_assignment=# SELECT name FROM countries WHERE id=1;
name  
--------
Canada

<!-- 9. Find the person named 'Destini Davis' and then use a series of SQL queries to find what country they live in. -->

one_to_many_assignment=# SELECT residence_id FROM persons WHERE name='Destini Davis';
 residence_id
--------------
            2

one_to_many_assignment=# SELECT city_id FROM residences WHERE id=2;
 city_id
---------
       8

one_to_many_assignment=# SELECT province_id FROM cities WHERE id=8;
 province_id
-------------
          14

one_to_many_assignment=# SELECT country_id FROM provinces WHERE id=14;
 country_id
------------
          1

one_to_many_assignment=# SELECT name FROM countries WHERE id=1;
  name  
--------
 Canada

<!-- 10. How many articles has Aditya Mukerjee written? -->

one_to_many_assignment=# SELECT id FROM authors WHERE name='Aditya Mukerjee';
 id
----
  2
(1 row)

one_to_many_assignment=# SELECT COUNT(id) FROM articles WHERE author_id=2;
 count
-------
     1
(1 row)
