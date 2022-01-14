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
  * 
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