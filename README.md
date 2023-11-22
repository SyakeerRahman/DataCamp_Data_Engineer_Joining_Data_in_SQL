# DataCamp_Data_Engineer_Joining_Data_in_SQL

Joining data is an essential skill which enables us to draw information from separate tables together into a single, meaningful set of results. Learn to supercharge queries using table joins and relational set theory in this course on joining data.
In this course, i learn how to:
✓ Work with more than one table in SQL
✓ Use inner joins, outer joins and cross joins
✓ Leverage set theory, including unions, intersect, and except clauses
✓ Create nested queries
Every step is accompanied by exercises and opportunities to apply the theory and grow my confidence in SQL.

1. Introducing Inner Joins

- [x] The ins and outs of INNER JOIN

https://youtu.be/44gX0rIYdv8
    
- [x] Your first join

```ruby
SELECT cities.name AS city, countries.name AS country, region
FROM cities
INNER JOIN countries
ON cities.country_code = countries.code;
```     

- [x] Joining with aliased tables

```ruby
select c.code as country_code, name, year, inflation_rate
FROM countries AS c
-- Join to economies (alias e)
Inner join economies e ON 
-- Match on code field using table aliases
e.code = c.code
```
- [x] USING in action

```ruby
SELECT c.name AS country, l.name AS language, official
FROM countries AS c
INNER JOIN languages AS l
-- Match using the code column
USING(code);
```

- [x] Defining relationships

https://youtu.be/znQPUy9DqpU

- [x] Relationships in our database
- [x] Inspecting a relationship

```ruby
-- Rearrange SELECT statement, keeping aliases
SELECT l.name AS language, c.name AS country
FROM countries AS c
INNER JOIN languages AS l
USING(code)
-- Order the results by language
ORDER BY language;
```

- [x] Multiple joins

https://youtu.be/4eCZmHKUR-k

- [x] Joining multiple tables
Your task in this exercise is to join tables to return the country name, year, fertility rate, and unemployment rate in a single result from the countries, populations and economies tables.

```ruby
-- Select fields
SELECT c.name, e.year, p.fertility_rate, e.unemployment_rate
FROM countries AS c
INNER JOIN populations AS p
ON c.code = p.country_code
-- Join to economies (as e)
INNER JOIN economies e
-- Match on country code
ON p.country_code = e.code;
```

- [x] Checking multi-table joins

Have a look at the results for Albania from the previous query below. You can see that the 2015 fertility_rate has been paired with 2010 unemployment_rate, and vice versa.

| name | year | fertility_rate | unemployment_rate |
|------------------|------------------|------------------|------------------|
| Albania    | 2015     | 1.663    | 17.1     |
| Albania    | 2010     | 1.663    | 14       |
| Albania    | 2015     | 1.793    | 17.1     |
| Albania    | 2010     | 1.793    | 14       |

Instead of four records, the query should return two: one for each year. The last join was performed on c.code = e.code, without also joining on year. Your task in this exercise is to fix your query by explicitly stating that both the country code and year should match!

```ruby
SELECT name, e.year, fertility_rate, unemployment_rate
FROM countries AS c
INNER JOIN populations AS p
ON c.code = p.country_code
INNER JOIN economies AS e
ON c.code = e.code
-- Add an additional joining condition such that you are also joining on year
AND e.year = p.year;
```

2. Outer Joins, Cross Joins and Self Joins

- [x] LEFT and RIGHT JOINs

https://youtu.be/LC4My9XgMkg

- [x] Remembering what is LEFT
      
- [x] This is a LEFT JOIN, right?

As before, you will be using the cities and countries tables.

You'll begin with an INNER JOIN with the cities table (left) and countries table (right). This helps if you are interested only in records where a country is present in both tables.

You'll then change to a LEFT JOIN. This helps if you're interested in returning all countries in the cities table, whether or not they have a match in the countries table.

```ruby
SELECT 
	c1.name AS city, 
    code, 
    c2.name AS country,
    region, 
    city_proper_pop
FROM cities AS c1
-- Join right table (with alias)
LEFT JOIN countries c2
ON c1.country_code = c2.code
ORDER BY code DESC;
```

- [x] Building on your LEFT JOIN
    
You'll now revisit the use of the AVG() function introduced in a previous course.

Being able to build more than one SQL function into your query will enable you to write compact, supercharged queries.

You will use AVG() in combination with a LEFT JOIN to determine the average gross domestic product (GDP) per capita by region in 2010.

```ruby
SELECT region, AVG(gdp_percapita) AS avg_gdp
FROM countries AS c
LEFT JOIN economies AS e
USING(code)
WHERE year = 2010
GROUP BY region
-- Order by descending avg_gdp
ORDER BY avg_gdp DESC
-- Return only first 10 records
LIMIT 10
```

- [x] Is this RIGHT?

You learned that right joins are not used as commonly as left joins. A key reason for this is that right joins can always be re-written as left joins, and because joins are typically typed from left to right, joining from the left feels more intuitive when constructing queries.

It can be tricky to wrap one's head around when left and right joins return equivalent results. You'll explore this in this exercise!

```ruby
-- Modify this query to use RIGHT JOIN instead of LEFT JOIN
SELECT countries.name AS country, languages.name AS language, percent
FROM languages
RIGHT JOIN countries
USING(code)
ORDER BY language;
```

- [x] FULL JOINs

https://youtu.be/0wo-RO1RNNA

- [x] Comparing joins

In this exercise, you'll examine how results can differ when performing a full join compared to a left join and inner join by joining the countries and currencies tables. You'll be focusing on the North American region and records where the name of the country is missing.

You'll begin with a full join with countries on the left and currencies on the right. Recall the workings of a full join with the diagram below!

```ruby
SELECT name AS country, code, region, basic_unit
FROM countries
-- Join to currencies
INNER JOIN currencies 
USING (code)
WHERE region = 'North America' 
	OR name IS NULL
ORDER BY region;
```

- [X] Chaining FULL JOINs

As you have seen in the previous chapter on INNER JOIN, it is possible to chain joins in SQL, such as when looking to connect data from more than two tables.

Suppose you are doing some research on Melanesia and Micronesia, and are interested in pulling information about languages and currencies into the data we see for these regions in the countries table. Since languages and currencies exist in separate tables, this will require two consecutive full joins involving the countries, languages and currencies tables.

```ruby
SELECT 
	c1.name AS country, 
    region, 
    l.name AS language,
	basic_unit, 
    frac_unit
FROM countries as c1 
-- Full join with languages (alias as l)
FULL JOIN languages as l 
USING(code)
-- Full join with currencies (alias as c2)
FULL JOIN currencies AS c2
USING(code)
WHERE region LIKE 'M%esia';
```

- [ ] Crossing into CROSS JOIN
- [ ] Histories and languages
- [ ] Choosing your join
- [ ] Self joins
- [ ] Comparing a country to itself
- [ ] All joins on deck

3. Set Theory for SQL Joins

- [ ] Set theory for SQL Joins
- [ ] UNION vs. UNION ALL
- [ ] Comparing global economies
- [ ] Comparing two set operations
- [ ] At the INTERSECT
- [ ] INTERSECT
- [ ] Review UNION and INTERSECT
- [ ] EXCEPT
- [ ] You've got it, EXCEPT...
- [ ] Calling all set operators
  
4. Subqueries

- [ ] Subquerying with semi joins and anti joins
- [ ] Multiple WHERE clauses
- [ ] Semi join
- [ ] Diagnosing problems using anti join
- [ ] Subqueries inside WHERE and SELECT
- [ ] Subquery inside WHERE
- [ ] WHERE do people live?
- [ ] Subquery inside SELECT
- [ ] Subqueries inside FROM
- [ ] Subquery inside FROM
- [ ] Subquery challenge
- [ ] Final challenge
- [ ] The finish line

  
