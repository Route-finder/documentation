===
API
===

Routes
======

The API consists of 3 main routes defined in the backend's ``app.ts`` file:

Books
-----

Located at ``/api/books``, this route accepts ``GET`` requests with the query
parameter of "``?name=<username>``" where ``<username>`` is any username present
in the application database.

This route returns the list of books associated with a given username as JSON
in the following format:

.. code-block:: JavaScript

  {
    "results": [
      {
        "isbn": "9781611321456",
        "author": "Author of the Work",
        "title": "Title of the Work",
        "call_no": "AM101.L196",
        "username": "username"
      },
      {
        "isbn": "9781611321456",
        "author": "Author of the Work",
        "title": "Title of the Work",
        "call_no": "AM101.L196",
        "username": "username"
      }
  }
       

Search
------

Located at ``/api/search``, this route accepts ``POST`` requests with the following
header parameters:

  * isbn: a valid ISBN-10 or ISBN-13 code
  * name: a username present in the application database

Passing a request to this endpoint will result in the requested item being added to
the application database. The following JSON will be returned in the case of either:

**Success**

``{"status": "success", "book": item}`` where ``item`` is the book information.

**Failure -- Database Issue**

``{"status": "failure", "error": data}`` where data is the response returned from the
OCLC access module.

**Failure -- Bad Input**

``{"status": "failure", "error": "Invalid ISBN"}``


Remove
------

Located at ``/api/remove``, this route accepts ``POST`` requests with the following
header parameter:

  * name: a username present in the application database
  
Passing a request to this endpoint will result in all items associated with that
username being removed from the database, with the end-user result of clearing the
subject user's list of books. It will return ``{"Status": "Success"}`` if the removal
was successful, or ``{"Status": "Failure", "Error": err}`` in the case of an
internal error, where ``err`` is any error reported by the database.

Database Interaction
====================

Use of the API requires that the PostgreSQL database connection be active. The Backend
will fail to launch if the database connection is configured incorrectly. Refer to
:doc:`database` for more information.
