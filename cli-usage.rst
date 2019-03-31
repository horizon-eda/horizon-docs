CLI usage
=============================

The project and the pool manager have pretty much eliminated the need to
run the interactive manipulator and other tools directly from a shell,
but it’s still useful for development.

All of the commands below require the environment variable
``HORIZON_POOL`` to point to the pool’s directory (the one with the
pool.json and pool.db in it)

horizon-imp
-----------

| Symbol mode:
| ``horizon-imp -y <symbol file>``

| Schematic mode:
| ``horizon-imp -c <schematic file> <block file>``

| Padstack mode:
| ``horizon-imp -a <padstack file>``

| Package mode:
| ``horizon-imp -k <package file>``

| Board mode:
| ``horizon-imp -b <board file> <block file> <via directory>``

horizon-pool
------------

Most of the -edit and -create commands will spawn $EDITOR with the file
to be edited serialized as YAML.

::

   horizon-pool create-unit <unit file>
   horizon-pool edit-unit <unit file>
   horizon-pool create-symbol <symbol file> <unit file>

   horizon-pool create-entity <entity file> [<unit file> ...]
   horizon-pool edit-entity <entity file>

   horizon-pool create-package <package file>
   horizon-pool create-padstack <padstack file>

   horizon-pool update #Recreates the pool's SQLite database.

Remember to run ``horizon-pool update`` after creating things


horizon-prj
-----------

Use these to create empty blocks, schematics, etc.

::

   horizon-prj create-block <block filename>

   horizon-prj create-schematic <schematic filename> <block filename>

   horizon-prj create-board <schematic filename> <block filename>
