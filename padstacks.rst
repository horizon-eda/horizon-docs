Padstacks
==========

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
