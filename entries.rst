Numeric Entries
===============

All numeric entries in horizon support basic two-operand math as well as some other goodies.

They look like these:

.. image:: images/entry.png

Both point and comma are recognized as a decimal separator regardless of locale settings. By default all numbers are treated as millimeters. Suffixing a number with an ``i`` will treat it as inches. 

Additionally, two-operand infix math is supported, so you can to this:

Addition: ``1+2``

Subtraction: ``1-2``

Multiplication: ``3*2``

Division: ``3/2``

Average :math:`\frac{ a+b }{2}`: ``3|2``
