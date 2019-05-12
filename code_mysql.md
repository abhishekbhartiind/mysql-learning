## Installation

`sudo apt-get install mysql-server`
`sudo mysql -u root -p` 
Enter: Your_password

###### In CLI

`SHOW DATABASES;` check what databases are available
`CREATE DATABASE database_name;` Creating a database

eg: `CREATE DATABSE universe` 

`USE database_name;` //select a database
`SHOW tables;` 

//create table name galaxy with row 
```
CREATE TABLE galaxy(
	id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, 
	name VARCHAR(20),
	description VARCHAR(50), 
	lifePresent CHAR(1), 
	created_at DATE
);
```
###### DESCRIBE TABLE	
`DESCRIBE galaxy;`

//insert data
```
INSERT INTO `galaxy` (`id`,`name`,`description`,`lifePresent`,`created_at`) 
VALUES (NULL, "Andromeda", "2.5 million light-years, spiral galaxy","Y", '2019-05-12');
```

//view table content syntax
`SELECT * from table_name`
eg 
`SELECT * from galaxy;`

| id | name             | description                                        | lifePresent | created_at |
|----|------------------|----------------------------------------------------|-------------|------------|
|  1 | Andromeda        | 2.5 million light-years, spiral galaxy             | Y           | 2019-05-12 |
|  2 | Black Eye Galaxy | a spectacular dark band of absorbing dust          | N           | 2019-05-11 |
|  3 | Milky Way        | a band because its disk-shaped structure is viewed | Y           | 2019-05-12 |
|  4 | Pinwheel Galaxy  | a face-on spiral galaxy,21 million light-years     | Y           | 2019-05-12 |



//update Information in the Table
```
UPDATE galaxy 
SET description = 'a face-on spiral galaxy,21 million light-years' 
WHERE galaxy.id = 4;

UPDATE galaxy SET constellation = 'Sagittarius' WHERE galaxy.id = 3;
```

// Add Column field with ALTER command
`ALTER TABLE galaxy ADD constellation VARCHAR(40);`

`ALTER TABLE galaxy ADD constellation VARCHAR(40) AFTER name;`
//Now the new “constellation” column goes after the column “name”.

//Delete Column
`ALTER TABLE galaxy DROP lifePresent;`


`SELECT * from galaxy;`

| id | name             | description                                        | created_at | constellation  |
|----|------------------|----------------------------------------------------|------------|----------------|
|  1 | Andromeda        | 2.5 million light-years, spiral galaxy             | 2019-05-12 | Andromeda      |
|  2 | Black Eye Galaxy | a spectacular dark band of absorbing dust          | 2019-05-11 | Coma Berenices |
|  3 | Milky Way        | a band because its disk-shaped structure is viewed | 2019-05-12 | Sagittarius    |
|  4 | Pinwheel Galaxy  | a face-on spiral galaxy,21 million light-years     | 2019-05-12 | Ursa Major     |
|  5 | Cigar Galaxy     | a starburst galaxy,12 million light-years away     | 2019-05-12 | Ursa Major	   |

// Delete a row
`` DELETE from [table name] where [column name]=[field text]; ``
eg: `DELETE from galaxy where id=5;`


