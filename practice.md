```
show databases;
create database bedrock;
use bedrock;
create table retired_employee (
    Name char(20) DEFAULT '' NOT NULL,
    Dept char(10) DEFAULT '' NOT NULL,
    JobTitle char(20),
    UNIQUE name_dept (Name,Dept)
);

describe retired_employee;
desc employee;

create table employee (Name char(20),Dept char(20),jobTitle char(20));
show tables;
INSERT INTO employee VALUES ('Fred Flinstone','Quarry Worker','Rock Digger');
INSERT INTO employee VALUES ('Wilma Flinstone','Finance','Analyst');
INSERT into employee values ('Barney Rubble','Sales','Neighbor');
INSERT INTO employee VALUES ('Betty Rubble','IT','Neighbor');

SELECT * from employee;

select name from employee where dept='Sales';
	
```

---------------
Note: Data type used was CHAR. Other data types include:
---------------
CHAR(M)    :Fixed length string. Always stores M characters whether it is holding 2 or 20 characters. Where M can range 1 to 255 			    characters.
VARCHAR(M) :Variable length. Stores only the string. If M is defined to be 200 but the string is 20 characters long, only 20 characters 		   are stored. Slower than CHAR.
INT : Ranging from -2147483648 to 2147483647 or unsigned 0 to 4294967295
FLOAT(M,N) : FLOAT(4,2) - Four digits total of which 2 are after the decimal. i.e. 12.34 Values are rounded to fit format if they are too 			   large.
DATE, TEXT, BLOB, SET, ENUM


-----------------
```
CREATE UNIQUE index name_dept on employee (name,dept);
INSERT INTO employee VALUES ("Jane Smith","Sales","Customer Rep");
INSERT INTO employee VALUES ("Jane Smith","Sales","Customer Rep"); --Duplicate entry 'Jane Smith-Sales' for key 'name_dept'
INSERT INTO employee VALUES ('Jane Smith','Engineering','Manager'); --works


ALTER TABLE employee ADD EmpId INT NOT NULL AUTO_INCREMENT PRIMARY KEY; 
ALTER TABLE employee DROP INDEX name_dept;  -- get rid of index

```

###### System Information

```
select version(); --5.7.26-0ubuntu0.18.04.1
select now(); --2019-05-12 18:47:31
select user();	--root@localhost
```
###### Sample Queries
```
SELECT COUNT(*) FROM employee;
SELECT * FROM employee WHERE name LIKE "%Sm%";
SELECT * FROM employee WHERE name REGEXP "^Ja";


SELECT * FROM  employee WHERE Name  LIKE "B%y";  -- "%" match any char: Gives Betty and Barney
SELECT * FROM  employee WHERE Name LIKE "B___y";  -- "_" match space: Gives Betty but not Barney
SELECT * FROM  employee WHERE Name RLIKE "^Betty$";  -- "^" match beginning. "$" to denote end of string
SELECT Name, COUNT(*) FROM employee WHERE Name LIKE "B%y";  -- Return Names and number of records returned

SELECT * FROM pet WHERE species = "snake" OR species = "bird";
SELECT * FROM pet WHERE species = "dog" AND sex = "f";
SELECT * FROM pet WHERE birth >= "1998-1-1";
SELECT name, birth FROM pet ORDER BY birth DESC;

```

 
