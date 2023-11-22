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

- [ ] LEFT and RIGHT JOINs
- [ ] Remembering what is LEFT
- [ ] This is a LEFT JOIN, right?
- [ ] Building on your LEFT JOIN
- [ ] Is this RIGHT?
- [ ] FULL JOINs
- [ ] Comparing joins
- [ ] Chaining FULL JOINs
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

  
