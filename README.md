# Structured-Query-Language-or-Sequel-

https://raw.githubusercontent.com/RodrigoMvs123/Structured-Query-Language-or-Sequel-/main/README.md


 

SQL (MySQL + postgreSQL) Installation & Setup Guide for MacOS & Windows
SQL (MySQL + postgreSQL) Installation & Setup Guide for MacOS & Windows

SQL Crash Course for Beginners 2022 (MySQL & PostgreSQL) - No prior knowledge required!

Mysql
PostgreSQL

Oracle Database
Microsoft SQL Server
Microsoft Access
SQLite

MySQL Documentation
MySQL Workbench
mysql Command Line Tool
14: PostgreSQL 14.4 Documentation
PSQL Command Line Tool

Terminal Structured Query Language or Sequel 
mysql
new file // export PATH=/usr/local/mysql/bin:$PATH
mysql

MAC OS terminal 
mysql - - host=localhost - - user=root - - password=Testers1! - - port=3306 ( MySQL to run locally ) 
mysql - - host=localhost - - user=root -p
Enter password:?

SELECT ‘Hello World’ 
;
quit 

MySQL Workbench Manual

PostgreSQL 13 ( SQL Shell ) // Tool and shows the default settings.
Database[localhost]:
Port[5432]:
Username [postgres]:
Password for user postgres:
postgres=# SELECT ‘Hello World’
postgres=# ;

MySQl and MySQL Shell ( Windows ) 


On Start select 
MySQL Shell
Terminal 
shell.connect()
shell.connect({host: ‘localhost’, user: ‘root’ // port: 3306}) // Identifier that tells ( MySQL) That it is running on the local machine
Please provide the password for ‘root@localhost’: ?
n
MySQl localhost:33060+ ssl JS> SELECT ‘Hello World’;
MySQl localhost:33060+ ssl JS> \sql
MySQl localhost:33060+ ssl SQL> SELECT ‘Hello World’;

On Start select 
MySQL Workbench // On Graphical User Interface 

PostgreSQL // SQL Shell command 
Terminal
Server [localhost]: 
Database [postgres]:
Port [5432]:  
Username [postgres]:
Password for user postgres: ?
postgres=# SELECT ‘Hello World’;
postgres=#

Visual Studio Code
Extension SQL Tools 
Add new connection 
Connections Assistance 
Drivers // to install

Extension SQLTools MySQL/MariaDB
Extension SQLTools PostgreSQL/Redshift Driver 

SQL Crash Course for Beginners 2022 (MySQL & PostgreSQL) - No prior knowledge required!


Table
Columns 
Fields and Rolls

PostgreSQL: Documentation: 14: Chapter 8. Data Types


01-Create-Database.sql
CREATE TABLE events (
--id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
id SERIAl PRIMARY KEY, -- Postgresl 
name VARCHAR(300) NOT NULL CHECK (LENGTH(name) > 5),
date_planned TIMESTAMP NOT NULL,
image VARCHAR(300),
description TEXT NOT NULL,
max_participants INT CHECK (max_participants > 0),
min_age INT CHECK (min_age > 0)
);

02-Create-tables.sql
SELECT 'Hello World';
CREATE DATABASE my_events;
        CREATE TABLE create;
        
03-Manipulate-data.sql
-- INSERT INTO events (
--     name, 
--     date_planned, 
--     description, 
--     -- max_participants, 
--     min_age)
--     VALUES (
--         'A first event', 
--         '2022-10-29 16:30:00', 
--         'This is the description of these first event.',
--         20,
--         18
--         );
--     (
--         'A second event', 
--         '2022-05-20 12:30:00', 
--         'This is the description of these second event.',
--         10,
--         22
--     );

UPDATE events
SET min_age = 16
WHERE id = 1;

DELETE FROM events;
WHERE id = 1;
    
04-Query-Data.sql
SELECT * FROM events; 
--WHERE date_planned >= '2022-06-01' OR min_age = 20;
ORDER BY id DESC;

05-Create-Locations-Tables.sql
CREATE TABLE cities(
    name VARCHAR(200) PRIMARY KEY 
);

name VARCHAR(300) NOT NULL CHECK (LENGTH(name) > 5),


CREATE TABLE locations (
  id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
--id SERIAl PRIMARY KEY, -- Postgresl 
  title VARCHAR(300),
  street VARCHAR(300) NOT NULL,
  house_number VARCHAR(10) NOT NULL,
  postal_code VARCHAR(5) NOT NULL,
  city_name VARCHAR(200) REFERENCES cities ON DELETE RESTRICT ON UPDATE CASCADE 

);

CREATE TABLE events (
id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
--id SERIAl PRIMARY KEY, -- Postgresl 
name VARCHAR(300) NOT NULL CHECK (LENGTH(name) > 5),
date_planned TIMESTAMP NOT NULL,
image VARCHAR(300),
description TEXT NOT NULL,
max_participants INT CHECK (max_participants > 0),
min_age INT CHECK (min_age > 0), 
location_id INT REFERENCES locations ON DELETE CASCADE
);

06-Create-All-Tables.sql
CREATE TABLE cities(
    name VARCHAR(200) PRIMARY KEY 
);

name VARCHAR(300) NOT NULL CHECK (LENGTH(name) > 5),


CREATE TABLE locations (
  --id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
  id SERIAl PRIMARY KEY, -- Postgresl 
  title VARCHAR(300),
  street VARCHAR(300) NOT NULL,
  house_number VARCHAR(10) NOT NULL,
  postal_code VARCHAR(5) NOT NULL,
  city_name VARCHAR(200) REFERENCES cities ON DELETE RESTRICT ON UPDATE CASCADE 

);

CREATE TABLE users (
--id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
id SERIAl PRIMARY KEY, -- Postgresl
first_name VARCHAR(300) NOT NULL,
last_name VARCHAR(300) NOT NULL,
birthdate DATE NOT NULL, 
email VARCHAR(300) NOT NULL 
);

CREATE TABLE organizers (
    password VARCHAR(500)
    user_id INT PRIMARY KEY REFERENCES users ON DELETE CASCADE
);

CREATE TABLE tags (
  name VARCHAR (100) PRIMARY KEY 
);

CREATE TABLE events (
--id INT PRIMARY KEY AUTO_INCREMENT, -- MYSQL 
id SERIAl PRIMARY KEY, -- Postgresl 
name VARCHAR(300) NOT NULL CHECK (LENGTH(name) > 5),
date_planned TIMESTAMP NOT NULL,
image VARCHAR(300),
description TEXT NOT NULL,
max_participants INT CHECK (max_participants > 0),
min_age INT CHECK (min_age > 0), 
location_id INT REFERENCES locations ON DELETE CASCADE
organizer_id INT REFERENCES organizers ON DELETE CASCADE
);

CREATE TABLE events_users (
  event_id INT REFERENCES events ON DELETE CASCADE,
  user_id INT REFERENCES users ON DELETE CASCADE
  PRIMARY KEY (event_id, user_id)
);

CREATE TABLE events_tags (
  event_id INT REFERENCES events ON DELETE CASCADE,
  tag_name VARCHAR(100) REFERENCES tags ON DELETE CASCADE
  PRIMARY KEY (event_id, tag_id)
);


07-Insert_Dummy_Data.sql
INSERT INTO tags (name)
VALUES ('socialize'), ('learn'), ('connect'), ('dinner'), ('breakfast');

INSERT INTO cities (name)
VALUES ('Munich'), ('Berlin'), ('Cologne'), ('Frankfurt'), ('Hamburg');

INSERT INTO locations ( title, street, house_number, postal_code, city_name)
VALUES
('Beerhall', 'Beerstreet', '5A', '80135', 'Munich'),
('NULL', 'Beerstreet', '10', '81035', 'Munich'),
('NULL', 'Gardenstreet', '101', '80031', 'Munich'), 
('The Green One', 'Veggiestreet', '12', '12141', 'Berlin'),
('NULL', 'Park Plaza', '1', '11011', 'Berlin'),
('Partyhouse', 'Carnevalstreet', '3', '12345', 'Cologne'), 
('NULL', 'Some Street', '18', '72657', 'Hamburg');

INSERT INTO users ( first_name, last_name, birthdate, email)
VALUES 
('MAX', 'Schwars', '1989-05-01', 'max@test.com'),
('Manuel', 'Lorenz', '1988-10-19', 'manuel@test.com')
('Julie', 'Barnes', '1986-02-13', 'julie@test.com')
('Michael', 'Smith','1982-11-11', 'michael@test.com')

INSERT INTO organizers (password, user_id)
VALUES
('mypw1', 1)--password would typically be stored encrypted
('somepw2' 2);

INSERT INTO events (name, date_planned, image, description, max_participants, min_age, location_id, organizer_id)
VALUES
(
   'New in Town',
   '2022-02-01 17:30:00',   
   'path/to/image.jpg',
   'You are new in town? Joint us and meet like-minded new people',
   20,
   16,
   1,
   1
);


INSERT INTO events_tags (event_id, tag_name)
VALUES
   (1, 'socialize'),
   (1, 'connect'),
   (1, 'dinner');

INSERT INTO events_users (event_id, user_id)
VALUES
   
   (1,3),
   (1,4),
   




08-Basic-Queries.sql
SELECT * FROM users;

09-Queries-With-Relations.sql
SELECT 
    e.id AS event_id, 
    e.name, 
    e.planned, 
    loc.title, 
    loc.street, 
    loc.house_number, 
    loc.city_name 
FROM events AS e
INNER JOIN locations AS loc ON e.location_id = loc.id; 

SELECT 
    e.id AS event_id, 
    e.name, 
    e.planned, 
    loc.title, 
    loc.street, 
    loc.house_number, 
    loc.city_name, 
    u_first_name,
    u.last_name
FROM events AS e
INNER JOIN locations AS loc ON e.location_id = loc.id; 
INNER JOIN events_users AS eu ON eu.event_id = e.id;
INNER JOIN users AS u ON eu.user_id = u.id;

SELECT * FROM locations AS loc
LEFT JOIN events AS e ON e.location_id = loc.id;

SELECT * FROM cities AS c
LEFT JOIN locations AS loc ON loc.citie_name = c.name
LEFT JOIN events AS e ON e.location_id = loc_id;

10-More-Queries.sql
SELECT * FROM users
WHERE first_name LIKE 'Ma%';

SELECT COUNT(id) FROM locations;  

SELECT c.name, loc_street, COUNT(loc.id) FROM cities AS c
LEFT JOIN locations AS loc ON loc.city_name = c.name; 
GROUP BY c.name, loc_street;

SELECT c.name, COUNT(loc.id) FROM cities AS c
LEFT JOIN locations AS loc ON loc.city_name = c.name; 
--WHERE loc.city_name = 'Munich'
GROUP BY c.name
HAVING COUNT(loc.id) > 1;


Drop.sql
DROP TABLE events;
