========
Database
========

Technologies
============

PosgreSQL
---------

This application uses the `PosgreSQL <https://www.postgresql.org/>`_ database in
its implementation. As currently deployed, the project uses the database option
provided by Heroku's platform.

Node-Postgres
-------------

The backend is built using the `Node-Postgres <https://node-postgres.com/>`_
object relational mapping module to interact with the provided database.

Database Structure
==================

The database uses a single table in the following configuration to store all books
or other materials added to users' lists:

**Columns:**

  * isbn: 10 or 13-digit string
  * author: up to 64 character string of author name
  * title: up to 256 character string of item title
  * call_no: up to 48 character string of item call_no
  * username: up to 64 character string of item's associated user

**Primary Key:**

The table's primary key is the combination of the values isbn and username.


SQL Configuration
-----------------

The following SQL command will create the necessary table for the application.

.. code-block: SQL

create table booklist IF NOT EXISTS (
    isbn VARCHAR(16),
    author VARCHAR(64),
    title VARCHAR(256),
    call_no VARCHAR(48),
    username VARCHAR(64),
    PRIMARY KEY (isbn, username)
);
