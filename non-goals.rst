Non-Goals
===================

To limit the project's focus, some things are explicitly out of scope.

Autorouter
----------

Writing a good autorouter is a lot of work that's more well spent on 
other aspects of the application as experience has show that an 
autorouter is rarely useful for small to medium-sized boards.

Simulation
----------

Schematic design for PCBs and schematic design for SPICE-type 
simulation are very different as in that schematics for simulation will 
often simplify aspects of the real world such as replacing an ADC input 
with it's equivalent circuit. On a personal side I'm perfectly happy 
with LTSpice in terms of user interface and SPICE core and don't see much 
scope for new developments in that space.

Raytracer
---------

Other EDA applications recently gained a custom raytracer for rendering 
pretty 3D visualisations of circuit boards. For horizon that's out of 
scope as the OpenGL-based 3D view is pretty enough for checking for the 
board for issues such as forgotten solder mask and getting an idea of 
what it'll look like assembled. Any more pretty visualisation is best 
taken care of by exporting to 3D modelling software such as blender.


On File formats
---------------

Many people complain that there's no commonly agreed on standard format 
for schematics and boards in the industry. The file formats for these
are application files formats, meaning that they'll need to support 
each and every knob and button the application has. Adopting another 
application's file format for horzion EDA would therefore result in 
horizon EDA being a bad clone of the other application.

JSON has been chosen as a serialization format as it directly maps to 
common data structures such as maps and arrays (opposed to XML) and is 
easily manipulated in almost every environment.


Next: :doc:`Installation<installation>`
