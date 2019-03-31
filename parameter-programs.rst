Parameter Programs
==================

As explained on other pages, horizon supports parametrizable padstacks
and (to a limited extent) packages. To apply the given parameters to the
existing geometry, each padstack and the like is accompanied by a small
program.

These programs are written in a custom stack-based language. Users of HP
calculators should feel familiar. Since there aren’t any loops, these
programs will terminate in finite time. The stack holds signed 64bit
integers. Conceptually, it grows from top to bottom.

Syntax
------

On the top level, a program is made up of tokens. Tokens are separated
by any amount of whitespace.

Token types:

-  Integers: a number, optionally prefixed by a sign
-  Dimension: a number with optional fractional part, suffixed by “mm”.
   The float before mm will get multiplied by 1e6, since horzion’s
   internal unit of measurement is 1nm
-  Mathematical operators such as: ``+ - * /``
-  Strings
-  Argument start ``[`` and end ``]`` any token between these two will
   get appended to the last command’s arguments

Generic Commands
----------------

Zero-operand
~~~~~~~~~~~~

``get-parameter [ <parameter> ]`` gets paramter and pushes it onto the
stack

One-operand
~~~~~~~~~~~

::

   Before the operation, the stack looks like this:

   .   .
   .   .
   +---+
   | a |
   +---+

   Operators:
       | pushes
   dup | a a
   chs | -a

Two-operand
~~~~~~~~~~~

::

   Before the operation, the stack looks like this:

   .   .
   .   .
   +---+
   | a |
   +---+
   | b |
   +---+

   Operators:
        | pushes
   +    | a+b
   -    | a-b
   *    | a*b
   /    | a/b
   dupc | a b a b (Duplicate coordinate)

Three-operand
~~~~~~~~~~~~~

::

   Before the operation, the stack looks like this:

   .   .
   .   .
   +---+
   | a |
   +---+
   | b |
   +---+
   | c |
   +---+

   Operators:
       | pushes
   +xy | a+c b+c
   -xy | a-c b-c

Padstack commands
-----------------

In order for an object (shape, etc.) to be manipulated by the program,
it needs to be assigned a parameter class. ## set-shape
``set-shape [ <parameter class> <form> ]`` Sets a shape to the specified
form or moves it to the specified position Valid forms:

-  ``rectangle``, pops height, width
-  ``circle``, pops diamater
-  ``obround``, pops height, width
-  ``position``, pops y, x

set-hole
~~~~~~~~

``set-hole [ <parameter class> <shape> ]`` Sets a hole to the specified
shape Valid shapes:

-  ``round``, pops diameter
-  ``slot``, pops length, diameter

Polygon commands (padstack and package)
---------------------------------------

set-polygon
~~~~~~~~~~~

``set-polygon [ <parameter class> <shape> <x0> <y0> ]`` Sets a polygon
to the specified shape with center at (x0,y0) Valid shapes:

-  ``rectangle``, pops height, width
-  ``circle``, pops diameter

set-polygon-vertices
~~~~~~~~~~~~~~~~~~~~

``set-polygon-vertices [ <parameter class> <n_vertices> ]`` Pops 
``n_vertices`` coordinates from the stack and replaces the polygon's 
vertices with them.

expand-polygon
~~~~~~~~~~~~~~

``expand-polygon [ <parameter class> <x0> <y0> <x1> <y1> ... <xn> <yn> ]``
Pops expansion. Expands the polyon specified by the coordinates in the
argument by the dimension popped from the stack.

Example program (from SMD rectangular padstack)
-----------------------------------------------

::

   get-parameter [ pad_width ]
   get-parameter [ pad_height ]
   dupc dupc
   set-shape [ pad rectangle ]
   get-parameter [ solder_mask_expansion ]
   2 *
   +xy
   set-shape [ mask rectangle ]

   get-parameter [ paste_mask_contraction ]
   2 *
   -xy
   set-shape [ paste rectangle ] 
