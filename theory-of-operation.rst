Theory of Operation
===================

Interactive manipulator
-----------------------

Horizon's primary interface is the so-called "Interactive manipulator"
(imp). It's the unified editor for symbols, schematics, padstacks,
packages and boards.

Canvas
~~~~~~

The canvas renders objects such as symbols, packages or tracks. The
output of the rendering are line segments and triangles that get
uploaded to the GPU for drawing. For rendering to to non-OpenGL targets,
the canvas provides hooks to get more information on what's being
rendered. So far, this is used by the gerber exporter, 3D preview and
DRC.

Core
~~~~

Since some documents such as symbols and schematics contain the same
type of object (e.g. texts) and schematic and netlist need to be
modified in-sync, some encapsulation has to take place. The core can be
considered the glue between the document, the canvas and the tools.

Tools
~~~~~

For each action the user can do, there's a tool. Once started, a tool
receives keyboard and mouse input and modifies the document accordingly
by means of the core. When needed, a tool may bring up additional
dialogs for requesting information from the user.

Property editor
~~~~~~~~~~~~~~~

Low-complexity adjustments such as line width don't warrant their own
tool, that's why the the core provides a property interface. The
property editor's widgets are automatically generated from the object's
description.
