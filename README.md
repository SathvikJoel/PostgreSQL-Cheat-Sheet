# PostgreSQL-Cheat-Sheet
Cheat Sheet for PostgreSQL, notes taken from [freeCodeCamp.org](https://www.youtube.com/watch?v=qw--VYLpxG4&t=4204s)


A database is a collection of data organized in a way that makes it easy to access and manipulate the data.

> POSTGRE is the Database
> 
> SQL is the Structured Query Language ( Programming Lanuage)

### How data is stored

* Stores data in tables

* Columns 

* Rows

### Relational Database 

  * A database that has relationships between tables

### Getting Things Started

  * The postgresql package will by default create a user called postgres
  
  * Switch to the postgres user by `sudo -iu postgres`
> sudo -iu <username> logs you in as <username>, without having to know <username>'s password.

  * [Look at the Initial cofiguration section to create a database cluster](https://wiki.archlinux.org/title/PostgreSQL)
  * exit out of the postgres user by `exit`
  * start the postgresql.service using `systemctl start postgresql`
  * type `psql`
  * type `\q` to exit

* psql — PostgreSQL interactive terminal

* [Look at the Familiarize with PostgreSQL section to understand how to access database shell](https://wiki.archlinux.org/title/PostgreSQL)


### Next Time
| Command | Description |
| ----------- | ----------- |
| `systemctl start postgresql` | Start the Service |
| `sudo -iu postgres` | Change to the postgres user |
| `psql -d databasename` | Start the database shell |
| `\q` | Exit the database shell |


### Commands


| Command | Description |
| ----------- | ----------- |
| `help` | Gives a small help guide |
| `\?` | Gives a big help guide |
| `\l` | Lists all databases |
| `CREATE DATABASE testname;` | Create a database by the name of testname |
| `\c databasename` | change to database | 
| `\d` | (Describe) Show all the tables in Database |
| `\d tablename` | (Describe) Describe the table |
| `\dt` | Show only the table types (not other types) |
| `DROP TABLE tablename` | Drops the table |
| `DROP DATABASE dbname` | Drops the whole Database |
| `\i path_to_sqlfile` | Executes commands from a file |
| `SELECT col1, col2 FROM table` | select col1, col2 from table |
| `SELECT * FROM person ORDER BY col ASC` | Sort by col (ascending, default) |
| `SELECT * FROM person ORDER BY col DESC` | Sort by col (descending) |
| `SELECT * from table WHERE cond1 and cond2` | Filter based on multiple conditions |


### Connec to a Database

`psql --help` gives a list of options

* Method 1 : 
`psql -h hostname -p port -U username` is a sample method to connect to a database, add other options accordingly

* Method 2 : 
go to psql and type `\c databaseaname` to connect to a database, the same command can be used to change the database

### A very Dangerous Command


To delete a database,

```sql
DROP DATABASE test;
```

> MAKE SURE YOU REALLY WANT TO DO IT! 


### Create Table

```sql
CREATE TABLE table_name(
  Column name + data type + constraints if any
);
```

Ex:

```sql
CREATE TABLE person (
  id int ,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  gender VARCHAR(6),
  date_of_birth TIMESTAMP,
);
```

#### All Data Types in SQL

[DOCUMENTAION : List of All the datatypes](https://www.postgresql.org/docs/9.5/datatype.html)

### Create Table with Constraints

Specify extra information that must be followed for every entry that is being addded

```sql
CREATE TABLE person (
  id BIGSERIAL NOT NULL PRIMARY KEY ,
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  gender VARCHAR(6) NOT NULL,
  date_of_birth TIMESTAMP NOT NULL,
);
```
### Insert records into tables

```sql
INSERT INTO tablename(
  col_name
)
VALUES ('value')
```


```sql
INSERT INTO person (
  first_name,
  last_name,
  gender,
  date_of_birth)
VALUES('Anne', 'Smith', 'FEMALE', DATE `1998-01-09');
```

Order in VALUES must match as given before

### Generate 1000 Rows with Mockaroo

[mockaroo website to create fake data](https://www.mockaroo.com/)

> person.sql is the file generate using mockaroo.com

You can directly add the table from the sql file using the following command

`\i path_to_loc\person.sql`

### Select From

`SELECT * FROM table` -- select all the columns from table

`SELECT col_name FROM table` -- select col_name from table

`SELECT col1, col2 FROM table` -- select col1, col2 from table

### Order By

`SELECT * FROM person ORDER BY col ASC` -- Sort by col (ascending, default)

`SELECT * FROM person ORDER BY col DESC` -- Sort by col (descending)

#### Multiple Columns

`SELECT * FROM person ORDER BY col1, col2 ASC` -- Sort by col1 then by col2 (ascending, default)

### Distinct

`SELECT DISTINCT col FROM table` 

### Where Clause and AND

Filter based on condition

`SELECT * from table WHERE cond1 and cond2`

Eg:

`SELECT * FROM table WHERE gender = 'FEMALE';`

`SELECT * FROM table WHERE gender = 'FEMALE' and country_of_birth = 'Poland'`

### Comparision Operators

* `<>` is `not equals` symbol

### Limit, Offset & Fetch

