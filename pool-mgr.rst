Pool Manager
============

The Pool Manager and Part Wizard help with managing things in the Pool
like symbols, entities and parts. You're most likely to use the Pool
Manager for creating new parts. To open the pool manager, launch Horizon EDA and click on the recently opened pool you like to edit. If you never opened a pool before, you can manually select a pool.json you like to open or create a new one. Depending on what kind of part you want to create,
several workflows are available:

Inherting from an existing part
-------------------------------

When the part you're about to create already exisits in a different
variant (different value or different temperature range) but is
otherwise all identical, the new part should inherit from the existing
part. To do so, select the desired base part in the "Parts" tab and
click "Create Part from Part". After having specified the new part's
location, you'll be shown the Part Editor. Uncheck the "inherit" option
for the attributes you'd like to change and save the new part.

Create part from existing Entity
--------------------------------

This workflow is appropriate when the Entity for the new part already
exists. Resistors or LEDs in nonstandard packages are of this kind, for
example. A Part is made up from a Entity and a Package, if the Package for the Part you want to make doesn't exist you will have to create it (see see :doc:`create-package`). 

If you have a fitting Entity and Package you can go ahead and create a Part. In the "Parts" tab, click on "Create Part" for creating the new part. Then after
specifying both Entity and Package and the Part's location, the Part Editor opens and you can edit the part and map the Entity pins to the Package pads.

Create all-new part
-------------------

Many parts such as MCUs, FPGAs, ADCs and other miracles of today's world
require creating new units and entities. Doing so manually would be very
tedious, that's why there's the Part Wizard to assist you. After having
selected the part's package (for creating packages, see :doc:`create-package` ) in the "Packages" tab, click on "Part
Wizard..." to launch it. You'll be greeted with a list of all Pads of
the package.

Fill in the pin names according to the datasheet. Only put the pins
primary name (like PB5) on an MCU in the leftmost entry and put all
other names (like UART0_TX, TA0) space-separated in the "Alt. names"
Entry. If your part is *really* big (such as an FPGA or large MCU) you
may want it to appear as more than one symbol in the schematic. To do
so, select all the pads you'd like to have in the same symbol and type
in the new Gate name. In case many Pads are electrically identical (such
as many GND pads) you may group them by selecting them and clicking the
"Link Pads" button in the bottom toolbar. This way, only one Pin will be
generated for these Pads.

For really large parts with 100+ pins, putting them all in manually can
become too tedious. To get around is, the part wizard can import pin names
from a CSV or json file.

A CSV file for pin import can look like this:

::

    1,PB0,bidirectional,Main,TXD,SDA
    2,PB1,bidirectional,Main,RXD,SCL
    3,TDI,input,Main
    4,TDO,output,Main
    5,GND,power_input,Main

The full CSV format is ``pad,pin,direction,gate,alt1,alt2,..``.

Defining the same pins in json format can be done with:

::

   {
       "1": {"pin": "PB0", "alt": ["TXD", "SDA"], "gate":"Main"},
       "2": {"pin": "PB1", "alt": ["RXD", "SCL"], "gate":"Main"},
       "3": {"pin": "TDI", "direction": "input",  "gate":"Main"},
       "4": {"pin": "TDO", "direction": "output", "gate":"Main"},
       "5": {"pin": "GND", "direction": "power_input", "gate":"Main"}
   }

For both CSV and json, entries with the same ``pin``-``gate`` will get their
pads merged. Additional valid values for ``direction`` are ``open_collector``,
``passive`` and ``not_connected``.

Reasonable sources for pin/pad name data are:

-  IBIS models
-  BSDL files
-  PDF datasheets

Once you're done filling in the pin names, click "Next" in the top left
corner for advancing to the next screen. Fill in the entries according
to your part. In case you're unsure on what to put in, take a look at
existing parts in the pool. If your part is available in multiple
almost-identical variants that only differ in aspects such as
temperature range or packing option (Tape/Reel, Tube, etc.) create the
part you're about to use. For creating the other variants, follow the
instructions in the topmost section. Take care of specifying the correct
location for units/symbols/entity and parts, so that they end in a
subdirectory of their respective directory in the pool.

For each gate, click on "Edit Symbol" for launching an interactive
manipulator to create the symbol for that unit. Use the "Map pin" tool
to place the pins in the symbol and "Draw line rectangle"/"Edit line
rectangle" for drawing the symbols body. Don't forget to give the symbol
a meaningful name and place the "$REFDES" and "$VALUE" texts.

When you've drawn all the symbols an filled in all of the metadata,
click "Finish" to finally insert the part into the pool.

Where to save things
--------------------

When creating new symbols, parts and the like the pool manager/part
wizard will sooner or later ask you for a file name or a directory (in
case of packages) to save the new part. Technically, the path you
specify only needs to meet two requirements:

-  It needs to be in the correct top-level directory, i.e. every symbol
   has to be somewhere in /symbols and so on. Padstacks specific to a
   package must be placed in the package's padstack directory.
-  The file has to end in ``.json``

To get an idea of how all this looks in practice, take a look at `the
pool <https://github.com/horizon-eda/horizon-pool/>`__

The Pool database
-----------------

The Pool keeps the metadata (filenames, UUIDs, names, etc.) in a SQLite
database to facilitate searching. Normally, the pool manager rebuilds
the database from scratch every time something has changed. However, if
you externally manipulate/remove files, you'll have to click "Update
Pool" for the database to include the changes you made.
