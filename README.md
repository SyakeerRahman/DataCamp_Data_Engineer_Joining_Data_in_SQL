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

- [ ] Defining relationships
- [ ] Relationships in our database
- [ ] Inspecting a relationship
- [ ] Multiple joins
- [ ] Joining multiple tables
- [ ] Checking multi-table joins

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

  
