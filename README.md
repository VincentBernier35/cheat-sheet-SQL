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
* `SELECT DISTINCT * FROM table-name`

### **WHERE**: USED TO FILTER
* `SELECT column1, column2, column3 FROM table-name WHERE condition;`
* `SELECT * FROM table-name WHERE condition1 AND condition2;`
* `SELECT * FROM table-name WHERE condition1 OR condition2;`
* `SELECT * FROM table-name WHERE NOT condition;`
* `SELECT * FROM table-name WHERE condition1 AND (condition2 OR condition3);`
* `SELECT * FROM table-name WHERE EXISTS (select column_name FROM table-name WHERE condition);`

### **ORDER BY**: sort the result ascending or descending
* `SELECT * FROM table-name ORDER BY column;`
* `SELECT * FROM table-name ORDER BY column DESC;`
* `SELECT * FROM table-name ORDER BY column1 asc, column2 DESC;`

### **SELECT TOP**: used to specify the number of records to return from top of table
* `SELECT TOP number colums_name FROM from table-name WHERE condition;`
* `SELECT TOP percent colums_name FROM from table-name WHERE condition;`
  * Not all database systems support `SELECT TOP`. The Mysql equivalent is the `limit` clause
* `SELECT column-names FROM table-name LIMIT offset, count;`

### **LIKE**: operator used in a WHERE clause to search for a specific pattern in a column
* % (percent sign) is a wildcard character that represents zero, one or multiple 
* _ (underscore) is a wild card charactertahat represents a single character
* `SELECT column_name FROM table_name WHERE column_name LIKE pattern;`
* `LIKE 'a%'` (find any values that start with 'a')
* `LIKE '%a'` (find any values that end with 'a')
* `LIKE '%or%'` (find any values that have 'or' in any position)
* `LIKE '_r'` (find any values that have _r in the second position)
* `LIKE 'a_%_%'` (find any values that start with 'a' and are at least 3 characters in length)
* `LIKE '[a-c]%'` (find any values starting with 'a', 'b' or 'c')

### **IN** operator that allows you to specify multiple values in a WHERE clause 
* essentially the IN operator is shorthand for multiple OR conditions
* `SELECT column_names FROM table_name WHERE column_name IN (value1, value2, ...);`
* `SELECT column_names FROM table_name WHERE column_name IN (SELECT STATEMENT);`

### **BETWEEN**: operator who select values within a given range 
* `SELECT column_name FROM table-name WHERE column_name BETWEEN value1 AND value2;`
* `SELECT * FROM products WHERE (column_name BETWEEN value1 AND value2) AND NOT #01/01/2022# AND #02/06/2022#;`
* `SELECT * FROM products WHERE column_name BETWEEN #01/01/2022# AND #02/06/2022#;`

### **NULL**: values in a field with no value
* `SELECT * FROM table-name WHERE column_name IS NULL;`
* `SELECT * FROM table-name WHERE column_name IS NOT NULL;`

