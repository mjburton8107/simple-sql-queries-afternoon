# simple-sql-queries

For today we will be practicing inserting and querying data using SQL.

Here is a website that will let us write queries to interact with some data.  [http://jxs.me/chinook-web/](http://jxs.me/chinook-web/)

On the left are the Tables with their fields.  The right is where we will be writing our queries.  The bottom is where we will see our results.  

Any new tables or records that we add into the database will be removed after you refresh the page.  So if you're wondering where you data went, that may be why.

Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## PERSON
1. Create a table called Person that records a person's Name, Age, Height, City, FavoriteColor, and Id.  Id should be an auto-incrementing id/primary key.  

CREATE TABLE Person (
  PersonId integer PRIMARY KEY AUTOINCREMENT,
  Name varchar(255),
  Age int,
  Height int,
  City varchar(255),
  FavoriteColor varchar(255)
  );

2. Add 5 different people into the Person database.  Remember to not include the Id because it should auto-increment.

INSERT INTO Person (Name, Age, Height, City, FavoriteColor)
VALUES ('Michael Burton', 32, 72, 'Salt Lake City', 'Gold')
VALUES ('Heidi Hawkins', 31, 67, 'Ogden', 'Gold');
VALUES ('Rebecca Burton', 35, 67, 'Manhattan', 'Purple');
VALUES ('Kirt Burton', 62, 75, 'Sandy', 'Black');
VALUES ('Kris Burton', 66, 65, 'Sandy', 'Red');

3. List the people in the Person table by Height from tallest to shortest (descending)

SELECT * FROM Person
ORDER BY Height DESCs

(For this database to create an auto incrementing field set it's type to INTEGER PRIMARY KEY AUTOINCREMENT)

  * List the people in the Person table by Height from shortest to tallest (ascending)
    SELECT * FROM Person
    ORDER BY Height ASC
  * List all the people in the Person table by oldest first
    SELECT * FROM Person
    ORDER BY Age DESC
  * List all the people in the Person table older than age 20.
    SELECT * FROM Person
    WHERE Age > 20
  * List all the people in the Person table that are exactly 18.
    SELECT * FROM Person
    WHERE Age = 18
  * List all Person that are less than 20 and older than 30.
    SELECT * FROM Person
    WHERE Age < 20 OR Age > 30
  * List all Person that are not 27 (Use not equals)
    SELECT * FROM Person
    WHERE Age != 27
  * List all Person where their favorite color is not red
    SELECT * FROM Person
    WHERE FavoriteColor != "Red"
  * List all Person where their favorite color is not red or blue
    SELECT * FROM Person
    WHERE FavoriteColor != "Red" AND FavoriteColor != "Blue"
  * List all Person where their favorite color is orange or green
    SELECT * FROM Person
    WHERE FavoriteColor = "Orange" OR FavoriteColor = "Green"
  * List all Person where their favorite color is orange, green or blue (use IN)
    SELECT * FROM Person
    WHERE FavoriteColor IN ('Orange', 'Green', 'Blue')
  * List all Person where their favorite color is yellow or purple
    SELECT * FROM Person
    WHERE FavoriteColor IN ('Yellow', 'Purple')

## ORDER
4. Create a table called Orders that records the productName, productPrice, Quantity, and personId  
      CREATE TABLE Orders (
      productName varchar(255),
      productPrice decimal,
      Quantity int,
      personId integer PRIMARY KEY AUTOINCREMENT
      );
5. Add 5 Orders to Order table
    INSERT INTO Orders (productName, productPrice, Quantity, personId)
    VALUES ('MacBook', '1000.00', 1, 001)
    VALUES ('iPod', '500.00', 1, 002)
    VALUES ('earbuds', '29.99', 2, 003)
    VALUES ('iPad', '225.00', 1, 004)
    VALUES ('iPhone', '700.00', 1, 005)
6. Select all the records from the Order table
    SELECT * FROM Orders

  * Calculate the total number of products Ordered
  SELECT sum(Quantity) FROM Orders

  * Calculate the total Order Price
  SELECT sum(productPrice) FROM Orders

  * Calculate the total Order Price By personId (If you only made orders for 1 person, go add more for the other people)


## Artists
7. Add 3 new Artists to the Artist table
INSERT INTO Artist (ArtistId, Name)
VALUES (777, "Insane Clown Posse"), (686, "Porter Robinson"), (562, "Madeon")

 * Select the top 10 artists in reverse alphabetical order
 SELECT * FROM Artist
ORDER BY Name Desc
LIMIT 10

 * Select the top 5 artists in alphabetical order
 SELECT * FROM Artist
 ORDER BY Name Asc
 LIMIT 5

 * Select all artists that start with the word Black
 SELECT * FROM Artist
WHERE Name LIKE "Black%"

 * Select all artists that contain the word Black
 SELECT * FROM Artist
WHERE Name LIKE "%Black%"

## Employee
8. Add 2 new Employees to the Employee table

INSERT INTO Employee (EmployeeId, LastName, FirstName, Title, ReportsTo, BirthDate, HireDate, Address, City, State, Country, PostalCode, Phone, Fax, Email)
VALUES (8107, 'Burton', 'Mike', 'Mr', 1, '1984-09-06', '2016-01-01', '1235 Nowhere', 'Salt Lake City', 'UT', 'USA', '84212', '8012315555', '8012315555', 'mike@gmail'),
(7777, 'Hawkins', 'Heidi', 'Ms', 1, '1985-09-06', '2011-01-01', '1235 Nowhere', 'Ogden', 'UT', 'USA', '84099', '8012315555', '8012315555', 'heidi@gmail')

* List all Employee first and last names only that live in Calgary
SELECT FirstName, LastName FROM Employee
WHERE City = "Calgary"

* Find the first and last name for the youngest employee
SELECT FirstName, LastName FROM Employee
ORDER BY BirthDate DESC LIMIT 1

* Find the first and last name for the oldest employee
SELECT FirstName, LastName FROM Employee
ORDER BY BirthDate ASC LIMIT 1
Margaret Park

* Find everyone that reports to Nancy Edwards (Use the ReportsTo column)
SELECT * FROM Employee
WHERE ReportsTo = 2

* Count how many people live in Lethbridge

SELECT count(*) FROM Employee
WHERE City LIKE "%Lethbridge%"


## Invoice
9. Use the Invoice table for the following

* Count how many orders were made from the USA

SELECT count(*) FROM Invoice
WHERE BillingCountry = 'USA'
91

* Find the largest order total amount
SELECT * FROM Invoice
ORDER BY Total DESC LIMIT 1

* Find the smallest order total amount
SELECT * FROM Invoice
ORDER BY Total ASC LIMIT 1

* Find all orders bigger than $5
SELECT * FROM Invoice
WHERE Total > 5

* Count how many orders were smaller than $5
SELECT count(*) FROM Invoice
WHERE Total < 5
233

* Count how many orders were in CA, TX, or AZ (use IN)
SELECT count(*) FROM Invoice
WHERE BillingState IN ('CA', 'TX', 'AZ')
35

* Get the average total of the orders
SELECT avg(Total) FROM Invoice
5.651941747572825

* Get the total sum of the orders
SELECT sum(Total) FROM Invoice
2328.600000000004


## Copyright

© DevMountain LLC, 2016. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
