# Data Manipulation Language (DML) includes operations such as INSERT, UPDATE and DELETE:

## Basics

```sql
-- Create a table HelloWorld
CREATE TABLE HelloWorld (
 Id INT IDENTITY,
 Description VARCHAR(1000)
)
-- DML Operation INSERT, inserting a row into the table
INSERT INTO HelloWorld (Description) VALUES ('Hello World')
-- DML Operation SELECT, displaying the table
SELECT * FROM HelloWorld
-- Select a specific column from table
SELECT Description FROM HelloWorld
-- Display number of records in the table
SELECT Count(*) FROM HelloWorld
-- DML Operation UPDATE, updating a specific row in the table
UPDATE HelloWorld SET Description = 'Hello, World!' WHERE Id = 1
-- Selecting rows from the table (see how the Description has changed after the update?)
SELECT * FROM HelloWorld
-- DML Operation - DELETE, deleting a row from the table
DELETE FROM HelloWorld WHERE Id = 1
-- Selecting the table. See table content after DELETE operation
SELECT * FROM HelloWorld
```

<br>
<hr>
<br>

## Query tables example

```sql
USE Northwind;
GO
SELECT TOP 10 * FROM Customers
ORDER BY CompanyName
-- will select the first 10 records of the Customer table, ordered by the column CompanyName from the database Northwind
```

Note that Use Northwind; changes the default database for all subsequent queries. You can still reference the database by using the fully qualified syntax in the form of [Database].[Schema].[Table]:
```sql
SELECT TOP 10 * FROM Northwind.dbo.Customers
ORDER BY CompanyName
SELECT TOP 10 * FROM Pubs.dbo.Authors
ORDER BY City
```
This is useful if you're querying data from different databases. Note that dbo, specified "in between" is called a
schema and needs to be specified while using the fully qualified syntax. You can think of it as a folder within your
database. dbo is the default schema. The default schema may be omitted. All other user defined schemas need to
be specified.

<br>
<hr>
<br>

### Reserved words

If the database table contains columns which are named like reserved words, e.g. Date, you need to enclose the
column name in brackets, like this:
```sql
-- descending order
SELECT TOP 10 [Date] FROM dbo.MyLogTable
ORDER BY [Date] DESC
```
<br>
The same applies if the column name contains spaces in its name (which is not recommended). An alternative
syntax is to use double quotes instead of square brackets, e.g.:

```sql 
-- descending order
SELECT top 10 "Date" from dbo.MyLogTable
order by "Date" desc
```
is equivalent but not so commonly used. Notice the difference between double quotes and single quotes: <strong>Single quotes are used for strings</strong>

<br>
<hr>
<br>

 Notice that T-SQL has a N prefix for NChar and NVarchar data types

 ```sql
SELECT TOP 10 * FROM Northwind.dbo.Customers
WHERE CompanyName LIKE N'AL%'
ORDER BY CompanyName
 ```

returns all companies having a company name starting with AL (% is a wild card, use it as you would use the asterisk
in a DOS command line, e.g. DIR AL*). For LIKE, there are a couple of wildcards available




