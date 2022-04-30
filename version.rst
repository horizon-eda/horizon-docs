File versions
===================

To protect against loss of fidelity when opening files in an older 
version of Horizon EDA than they were created with, version 1.3.0 
introduces the concept of file versions.

Rather than storing the application version in design files and pool 
items, each file type has its own version number that'll get 
incremented if the file format changes in a way that's incompatible 
with older versions. That way, warnings about upgrading files are only 
shown if needed. Forward compatibility, as in being able to open 
files that were crated in an earlier version, is always given.

By Application version
----------------------

.. csv-table::
   :header: "Type", "1.3.0", "1.4.0", "2.0.0", "2.1.0", "2.2.0", "2.3.0"

   Unit, 0, 0, 0, 0, 0, **1**
   Symbol, 0, 0, 0, 0, **1**, 1
   Entity, 0, 0, 0, 0, 0, 0
   Padstack, 0, 0, 0, 0, 0, 0
   Package, 0, 0, 0, 0, 0, 0
   Part, 0, 0, **1**, 1, **2**, 2
   Frame, 0, 0, 0, 0, 0, 0
   Decal, 0, 0, 0, 0, 0, 0
   Schematic, 0, 0, **1**, 1, **3**, **6**
   Board, 0, **2**, **4**, 4, **7**, **14**
   Project, 0, 0, **1**, 1, **2**, 2
   Pool, N/A, N/A, N/A, N/A, 0, **1**


Changelog
---------

As of Horizon EDA Version 1.3.0, all object types are at version 0. Any 
changes will be listed here once they happen.

Board:
  - 1: Add holes to PDF export
  - 2: Support pick & place export format customisation
  - 3: Add silkscreen color
  - 4: Add rule net class regex matching
  - 5: Add shorted pads rule
  - 6: Add pads only flag to silkscreen exposed copper rule
  - 7: Actually serialize from rules option for planes
  - 8: Add matching multiple nets in rules
  - 9: Add matching multiple components in rules
  - 10: Add thermal rules
  - 11: Add thermal spoke customisation
  - 12: Add net ties
  - 13: Add ODB++ export
  - 14: Add track connection offset
  
Schematic:
  - 1: Add custom values on symbols
  - 2: Add hierarchy
  - 3: Add name orientation to block symbol ports
  - 4: Add connectivity checks
  - 5: Add support for UUID-based alternate pin names with direction
  - 6: Add net ties

Project:
  - 1: Replace pool cache with project pool
  - 2: Add hierarchy

Part:
  - 1: Add flags
  - 2: Add prefix override

Symbol:
  - 1: Fix orientation-specifix text placement
  
Pool:
  - 1: Add default frame
  
Unit:
  - 1: Use UUIDs for alternate pin names and support directions
