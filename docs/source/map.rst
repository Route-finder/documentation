=====
Mapping
=====

Application Purpose
-------------------

The purpose of the mapping program
is to provide information for reshelving books.
It does this by providing a map of the library, in addition
to highlighted shelves that have books in need of
being reshelved.

Developers can extend the given map for their own purposes
if needed by modifying `map.json` with new data as described
below.

Creating a new map
---------------------------

Map.tsx, in the src/components/ui directory reads from a file in the
same directory called `map.json` for the creation of the map.
The layout of the json in `map.json` is

.. code-block:: JavaScript

    Array<
       {
       "left": Array<{"min: string, "max": string}>
       "right": Array<{"min": string, "max": string}>
    }>

The outer Array is the entire list of rows in the library. The
`"left"` and `"right"` object are for the left and right
sides respectively of the row. The next-inner-most array
is the list of shelves contained in a row, which each
have minimum and maximum library codes.

The strings should be library codes should be in a form such as `QA1`, in a way
that is readable for our 
`ordering scheme <https://www.npmjs.com/package/lc_call_number_compare>`_.

To use this new map, overwrite the contents of `map.json` with the above JSON.

Modifying minor aspects
---------------------------

To change the colors of the books, modify
the constants `NO_BOOKS_COLOR` and `HAS_BOOKS_COLOR`. You can
also modify the width between the shelves, and certain other aspects
of the map using the global constants at the top of the file.

Modifying the code
---------------------------

If the map produced looks incorrect in some way, such as being too long for
the screen, you may need to use or write your own functions. The idea
of the code at the time of writing is to be extremely modular and mutation-free
so that the code will be not as complicated as it could be to understand.

The most important thing to understand about the code is the type structure.
All of the interfaces are at the top of the file, and explain in detail
what everything looks like.


React components
------------------------------

- `Shelf`: Shelves are building block of rows, and need
  information, such as the color of each of their sides,
  their x,y coordinates, and the range of books they contain.

- `Row`: Rows contain lists of shelves that will be rendered
  with the first element shelf at the top.

