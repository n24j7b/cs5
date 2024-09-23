java c
Database Design  Implementation 
Implementing tables
Here are the tables we are going to   implement:
Customer{CustomerID (PK), FirstName,   Surname, Email}
WineOrder{OrderID (PK), OrderDate, DeliveryDate, CustomerID (FK)}   Basket{OrderID (PK,FK),WineID(PK,FK)}
Wine{WineID (PK), Price, Quality, Country}
For information, the business rules are:
1.A customer can place many orders.
2. Each order is placedby one   customer.
3. An order can appear in the basket many   times.
4. Each entry in the basket is   for   one   order.
5. Each wine can appear   in   many baskets.
6. Each entry in the basket is   for   one wine.
The   SQL command to create a table is the CREATE TABLE statement:
CREATE TABLE table_name (
column1 datatype, 
column2 datatype,
column3 datatype,
… 
);
CREATE TABLE Customer(
CustomerID VARCHAR(255) PRIMARY KEY,
FirstName VARCHAR(255),
Surname VARCHAR(255),
Email VARCHAR(255));
To run this in   Base,   go to Tools,   SQL,   then   type   the   command   and   press   Execute.   I   had   to   close   the   database and reopen it in order to   see the   table   that   had   been   created –   this   is   a   bug   in   Base.
Run this and check that the table has been created. Then   delete your   SQL   (this will   have   no   impact   on the table) and type in the next command to   create the   Order   table:
CREATE TABLE WineOrder(
OrderID VARCHAR(255) PRIMARY KEY,
OrderDate DATE,
DeliveryDate DATE,
CustomerID VARCHAR(255),
FOREIGN KEY (CustomerID)    REFERENCES Customer(CustomerID));
The line above illustrates how to set up a foreign key: you   specify   the   fieldname   and   field   data   type   of   the   foreign   key,   then   in   a   new   line   use   the   keywords   FOREIGN   KEY   and   REFERENCES,   and   specify the fieldname of the foreign key field in brackets,   and the   table代 写Database Design & Implementation
代做程序编程语言   and   in brackets   the   fieldname of the primary key you are using to join the tables. Referential integrity is automatically enforced.
Try   creating   the Wine   table   next. You   can   use   the   INT   datatype   to   store   Quality   and   the   DOUBLE   datatype to store price. 'DOUBLE' is a number that has   decimal   places.
The code for the Basket is as follows. Notice that   it   has   a   composite   primary   key.
CREATE TABLE Basket(   WineID VARCHAR(255),
OrderID VARCHAR(255), PRIMARY KEY (WineID,OrderID),
FOREIGN KEY (WineID) REFERENCES Wine(WineID),
FOREIGN KEY (OrderID) REFERENCES WineOrder(OrderID));
THE REST OF THIS MATERIAL IS HERE FOR REFERENCE 
Composite primary keys 
The following code will create a table   and make Field1   and   Field3   its   composite   key:
CREATE TABLE Testtable(
Field1 VARCHAR(255),
Field2 VARCHAR(255),
Field3 VARCHAR(255),
PRIMARY KEY (Field1,Field3));
You may also need to look at the   SQL   ALTER TABLE statement if you   have   to   set   up   a   table which contains a foreign key, before you set up the table which has   that   foreign   key   as   its   primary   key. 
Composite foreign keys 
It is very uinlikely you will   ever need this:
CREATE TABLE Testtable1(
Field1 VARCHAR(255),
Field2 VARCHAR(255),
Field3 VARCHAR(255),
Primary Key (Field1),
Foreign Key (Field2, Field3) REFERENCES Testtable2(Field2, Field3));
The combination of Field2 and Field3 must   exist in Testtable2 before you   can   enter   it   in Testtable1.
Join tables 
You have already used this syntax to create the   Basket   table.
CREATE Table JoinTable(
Field1 VARCHAR(255),
Field2 VARCHAR(255),
Primary Key (Field1, Field2),
Foreign Key (Field1) References Table1(Field1),
Foreign Key (Field2) References Table1(Field2);







         
加QQ：99515681  WX：codinghelp
