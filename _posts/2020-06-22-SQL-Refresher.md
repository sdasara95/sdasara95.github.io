---
layout: post
title: SQL Refresher
subtitle: Revise a good chunk of SQL quickly
gh-repo: sdasara95/
gh-badge: [follow]
tags: [sql, technical]
comments: true
---

I always feel that the notes you write for yourself are the best notes for reference. This is not because you write well or explain well, it's because you can remind yourself things that were going on in your mind when you were writing the notes as you read. This personal connect is necessary when you want to refresh things quickly. Also, most resources online are either too brief or too verbose. Quick revision requires something succint. 
<br />
<br>
SQL is the most pivotal language for querying data. The depth is limitless however, we always don't need to know everything unless it's absolutely required. Software engineers and data scientists are expected to have atleast intermediate proficiency. I have written this article to help myself when I need to quickly revise SQL in less than two hours before technical interviews. I have primarily used [SQL training by Mode Analytics](https://mode.com/sql-tutorial/) and [SQL tutorial by WagonHQ](http://www.wagonhq.com/sql-tutorial) as references for this article. 
<br />
<br>
SQL has many flavors: Oracle, PostGres, MySQL
There are some difference among the flavors but they matter mostly for database administrating tasks which is beyond the scope of this article.
A good way to think of the data organization is:
>**Database** is like the main folder <br>
>**Schema** is the subfolder inside main folder <br>
>**Table** is inside schema if schema exists otherwise it's directly inside database <br>
>**Data Model** is the primary key, foreign key based relationship between tables in a schema. Data Model is sometimes used interchangably with schema. 

<br>

Now that we got the nomenclature out of the way, let's dive into language itself.<br>
Basic query to retrieve **ALL** data is as follow:
```sql
SELECT *
FROM tutorial.us_housing_units
```
Here tutorial is schema and us_housing_units is the table we are fetching. <br>
### Column Names
We can fetch west and south columns from table and display with new column names using **AS**
```sql
SELECT west AS West_Region,
       south AS South_Region
  FROM tutorial.us_housing_units
```
We can use quotes to denote new names as strings
```sql
SELECT west AS "West Region"
  FROM tutorial.us_housing_units
```
**This will cause ERROR** because single space is not allowed. It'll parse Region as SQL command and throw error.
```sql
SELECT west AS West Region
  FROM tutorial.us_housing_units
```
### LIMIT
This will limit the number of records displayed
```sql
SELECT *
  FROM tutorial.us_housing_units
 LIMIT 100
```
### WHERE
This is used to filter data
```sql
SELECT *
  FROM tutorial.us_housing_units
 WHERE month = 1
```
### COMPARISION OPERATORS
These operators are supported: <, >, <=, >=, =, != <br>
Work on **String** and **Numeric** data
```
SELECT *
  FROM tutorial.us_housing_units
 WHERE month_name != 'January'
```
```
SELECT *
  FROM tutorial.us_housing_units
 WHERE west > 30
```
For Strings it's a bit **tricky**
The below query will return records with month_name January **because Ja>J**
```
SELECT *
  FROM tutorial.us_housing_units
 WHERE month_name > 'J'
```
### ARITHMETIC OPERATORS
Do calculations directly on columns during SELECT and WHERE
```
SELECT year,
       month,
       west,
       south,
       west + south AS south_plus_west
  FROM tutorial.us_housing_units
```
```
SELECT year,
       month,
       west,
       south,
       west + south - 4 * year AS nonsense_column
  FROM tutorial.us_housing_units
```
Can be used on WHERE
```
SELECT year,
       month,
       west/(west + south + midwest + northeast)*100 AS west_pct,
       south/(west + south + midwest + northeast)*100 AS south_pct,
       midwest/(west + south + midwest + northeast)*100 AS midwest_pct,
       northeast/(west + south + midwest + northeast)*100 AS northeast_pct
  FROM tutorial.us_housing_units
 WHERE year >= 2000
```
```
SELECT year,
       month,
       west,
       south,
       midwest,
       northeast
  FROM tutorial.us_housing_units
  WHERE west > (midwest + northeast)
```
### LOGICAL OPERATORS
#### LIKE
This is used for **Case Sensitive** matching. <br>
Matches only those starting with S not s. 
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE "group" LIKE 'Snoop%'
```
Here "group" not GROUP because GROUP is inbuilt function!<br>
**If the field name matches with in-built function, it has to be accessed with double quotes.**<br>
**%** is called **Wildcard** because it matches any set of characters.
#### ILIKE
This is used to **ignore Case** while matching. <br>
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE "group" ILIKE 'snoop%'
```
If you want to **substitute for single character** then you can use _
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE artist ILIKE 'dr_ke'
```
If you want to write a query where you want all records which have Ludacris in the group, you can write as follows:
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE "group" ilike '%ludacris%'
```
#### IN
This is used to check for values in specified set.<br>
Works for both 
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year_rank IN (1, 2, 3)
```
```
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE artist IN ('Taylor Swift', 'Usher', 'Ludacris')
```
