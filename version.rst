File versions
===================

To protect against loss of fidelity when opening files in an older 
version of Horizon EDA than they were created with, version 1.3.0 
introduces the concept of file versions.

Rather than storing the application version in design files and pool 
items, each file type has its own version number that'll get 
incremented if the file format changes in a way that's incompatible 
with older versions. That way, warnings about upgrading files are only 
show if needed. Forward compatibility, as in being able to open 
files that were crated in an earlier version, is always given.

By Application version
----------------------

.. csv-table::
   :header: "Type", "1.3.0"

   Unit, 0
   Symbol, 0
   Entity, 0
   Padstack, 0
   Package, 0
   Part, 0
   Frame, 0
   Decal, 0
   Schematic, 0
   Board, 0
   Project, 0


Changelog
---------

As of Horizon EDA Version 1.3.0, all object types are at version 0. Any 
changes will be listed here once they happen.
