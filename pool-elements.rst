Elements of a Part
==================

A final Part is composed of multiple elements, that are stored independently from each other in the Pool.

Parts
~~~~~

On top of pool's structure there is the part. To avoid redundancy and alow faster
changes, a part can inherit its definition (or parts of it) from another part. This is intended to be used for groups of parts that only differ in some property like resistance or output voltage for fixed voltage regulators. Each part can
be accompanied with parametric data to make it easier to search for.
Right now, this feature is only implemented for resistors and capacitors. 

In addition to it's data the part is connected to both a Entity and a Package. 
The Part stores how the pins of each Gate in the Entity map to
the pads in the Package (e.g. in the case of the NAND it would map Input A to the
corresponding Pin on a DIP 14 package).

Packages
~~~~~~~~

A Package defines the footprint of a part. If the part's manufacturer
provides a reasonable footprint recommendation, use this one. Only use
generic packages if there isn't any. For details on packages see
:doc:`create-package`.

Entities
~~~~~~~~

An Entity is a Part's netlist representation and consists of one or more Units.
Parts that are logically the same like different shapes of USB connectors 
therefore can all share the same Entity, e.g. "USB connector with shield and ID".
The Symbol for each Unit in the Entity can be placed independently on the schematic.

Units
~~~~~

A Unit actually defines a part's logical pins. For parts that only
consist of one "gate" like a simple resistor, their entity simply
references one unit. For parts consisting of multiple "gates" like a
dual operational amplifier or a big MCU, each gate references one unit.
Having units separate from entities allows multiple entities to share
the same units. The entity for a dual logic gate thus is supposed to
reference the same unit as a quad one. Apart from a name, a pin has a
direction (for ERC) and optionally alternate pin names to deal with pins
having multiple functions as it's common among MCUs.

Symbols
~~~~~~~

A symbol is used in the schematic to represent a unit. Contrary to other
EDA applications, a symbol just displays the pins from its unit and
doesn't define these.

.. _Padstacks:

Padstacks
~~~~~~~~~

In horizon a pad references a padstack to determine its shape. There are
two kinds of padstacks in horizon: Global padstacks are available for
use to all packages and should cover most uses cases. In case a package
requires a specialized padstack, you can create one using the "Create
padstack for package" button in the "Packages" tab in the pool manager.

A padstack consists of these items:

-  Copper
-  Solder mask opening
-  Paste mask
-  Hole (optional)

The preferred way of defining geometry in padstacks is to use shapes as
these get translated to efficient primitives when exporting the board as
a gerber file. To suit more than one package parameters can be applied
to padstacks that alter their size. Parameters are also used to apply
application-specific global parameters like solder mask expansion and
paste mask contraction. To get an idea on how this works out in reality
take a look at the global padstacks in the pool.

To apply the parameters to the padstack's geometry each padstack is
accompanied by a :doc:`Parameter Program <parameter-programs>`  that takes
care of applying the parameters to the shapes.

