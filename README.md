# Sql cheat sheet

A quick reminder of all relevant SQL queries and exemples on how to use them.

# Table of contents
1. [ Finding data queries ](#find)
2. [ Data modification queries ](#modify)
3. [ Reportinng queries ](#report)
4. [ Join queries ](#joins)
5. [ View queries ](#view)
6. [ Altering table queries ](#alter)
7. [ Creating table query ](#create)

<a name="find"></a>
# 1. Finding Data Queries

### **SELECT**
* `SELECT * FROM dbname`

### **DISTINCT**: filters away duplicate values and return rows of specified column
* `SELECT DISTINCT * FROM table_name`

### **WHERE**: USED TO FILTER
* `SELECT column1, column2, column3 FROM table_name WHERE condition;`
* `SELECT * FROM table_name WHERE condition1 AND condition2;`
* `SELECT * FROM table_name WHERE condition1 OR condition2;`
* `SELECT * FROM table_name WHERE NOT condition;`
* `SELECT * FROM table_name WHERE condition1 AND (condition2 OR condition3);`
* `SELECT * FROM table_name WHERE EXISTS (select column_name FROM table_name WHERE condition);`

### **ORDER BY**: sort the result ascending or descending
* `SELECT * FROM table_name ORDER BY column;`
* `SELECT * FROM table_name ORDER BY column DESC;`
* `SELECT * FROM table_name ORDER BY column1 asc, column2 DESC;`

### **SELECT TOP**: used to specify the number of records to return from top of table
* `SELECT TOP number colums_name FROM from table_name WHERE condition;`
* `SELECT TOP percent colums_name FROM from table_name WHERE condition;`
  * Not all database systems support `SELECT TOP`. The Mysql equivalent is the `limit` clause
* `SELECT column_names FROM table_name LIMIT offset, count;`

### **LIKE**: operator used in a WHERE clause to search for a specific pattern in a column
* % (percent sign) is a wildcard character that represents zero, one or multiple 
* _ (underscore) is a wild card charactertahat represents a single character
* `SELECT column_name FROM table_name WHERE column_name LIKE pattern;`
* `LIKE 'a%'` (find any values that start with 'a')
* `LIKE '%a'` (find any values that end with 'a')
* `LIKE '%or%'` (find any values that have 'or' in any position)
* `LIKE '_r'` (find any values that have _r in the second position)
* `LIKE 'a_%_%'` (find any values that start with 'a' and are at least 3 characters in length)
* `LIKE '[a_c]%'` (find any values starting with 'a', 'b' or 'c')

### **IN** operator that allows you to specify multiple values in a WHERE clause 
* essentially the IN operator is shorthand for multiple OR conditions
* `SELECT column_names FROM table_name WHERE column_name IN (value1, value2, ...);`
* `SELECT column_names FROM table_name WHERE column_name IN (SELECT STATEMENT);`

### **BETWEEN**: operator who select values within a given range 
* `SELECT column_name FROM table_name WHERE column_name BETWEEN value1 AND value2;`
* `SELECT * FROM products WHERE (column_name BETWEEN value1 AND value2) AND NOT #01/01/2022# AND #02/06/2022#;`
* `SELECT * FROM products WHERE column_name BETWEEN #01/01/2022# AND #02/06/2022#;`

### **NULL**: values in a field with no value
* `SELECT * FROM table_name WHERE column_name IS NULL;`
* `SELECT * FROM table_name WHERE column_name IS NOT NULL;`

### **AS**: aliases are used to assign a temporary name to a table or column
* `SELECT column_name AS alias_name FROM table_name;`
* `SELECT column_name FROM table AS alias_name;`
* `SELECT column_name AS alias_name1, column_name2_AS alias_name2;`
* `SELECT column_name1, column_name2 + ',' + column_name3 AS alias_name2;`

### **UNION**: set operator used to combine the result-set of two or more SELECT statements
* Each SELECT statement within UNION must have the same number of colums
* The colums must have similar Datatypes
* the  columns in each  SELECT statement must also be in the same order
* `SELECT colums_names FROM table1 UNION SELECT column_name FROM table2;`
* `union` operator only selects distinct values, `UNION ALL` will allow duplicates

### **INTERSECT**: set operator which is used to return the records that two SELECT statements have in common
* Generally used the same way as **UNION** above
* `SELECT columns_name FROM table1 INTERSECT SELECT column_name FROM table2;`

### **EXCEPT**: set operator used to return all the records in the first SELECT statement that are not found in the second SELECT statement
* Generally used the same way as **UNION** above
