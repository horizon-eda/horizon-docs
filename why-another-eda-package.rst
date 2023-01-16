Why another EDA package
=======================

So you may be wondering why I started horizon EDA back in 2016, given 
that KiCad was a thing at that time.

Let's get started with a quote from Tom Hausherr: `PCB Design Perfection Starts in the CAD Library
<https://www.innofour.com/3783/news/literature/pcb-design-perfection-starts-in-the-cad-library/pcb-design-perfection-starts-in-the-cad-library-part-1>`_

    [...] PCB design perfection starts in the CAD library.

This also applies to EDA software as in a schematic / PCB design tool 
can only be as good its library structure. Since the definition of 
library items such as symbols packages is the very foundation of any 
EDA software, changing these definitions is next-to-impossible without 
significant changes to almost all other parts of the application. 
Having a certain library structure in place also thus guides any further 
development on that EDA application.

Having used KiCad for small 
and medium-sized projects, my biggest pain points were the library 
lacking a concept of orderable parts without duplicating the symbol for 
each part and the schematic editor not knowing about nets. KiCad's board 
editor, while being quite good as a layout tool was lacking expressive 
design rules. Especially the first and second point didn't seem easy to 
alleviate without major changes that would have involved lots of 
discussion since these would be breaking changes.

That made me start thinking how I'd design an EDA tool that meets my 
wishes and is easy enough to implement from scratch as a one man show 
and provides a clean-slate playground for experimentation.

At the very core of these thoughts was to keep schematic and netlist 
representation of a design separate to allow for non-schematic based 
workflows such as interconnectivity tables. That lead to the decision to 
define pins and their direction in what's called a Unit and not in the symbol as it's common 
among many other EDA packages. This also makes it possible to have 
multiple symbols representing the same thing (such as a resistor) 
without any effect on the netlist. Apart from name and direction, a pin 
as it's defined in a Unit can also have multiple alternate names to 
specify multiple pin functions as they're commonly available on MCUs 
and FPGAs.

To define the netlist representation of an actual part, units are 
referenced by what's called an Entity. This reference is called Gate. 
For simple parts, an entity references just a single Unit that includes 
all pins. For some parts it makes sense to have more gates.

Parts that include multiple instances of the same functionality such as 
quad opamps will then reference the opamp unit 4 times as well as a 
unit for power supply.

On the board side of things, packages are defined as in pretty much 
every EDA package out there - pads and graphical items such as 
silkscreen, reference designator and assembly outline. Pads however are 
defined by a padstack describing copper, soldermask and other layers in 
terms of shapes and polygons. This greatly facilitates odd-shaped pads 
as they can be drawn as-is without resorting to hacks such as using 
multiple pads to make up one actual pad. To avoid having a custom-drawn 
padstack for every pad size, padstacks are usually accompanied by a 
short script written in a custom stack-based language to adjust their 
size as well as other properties such as corner radius or solder mask 
expansion.

The pads of a package are mapped to the pins defined in the units 
referenced by an entity in what's called a Part. In order to mapped to 
something orderable, Parts have fields for the manufacturer name and 
the manufacturer's part number (MPN) among other details such as 
datasheet link or description.

All aforementioned references between items (such as entities 
referencing units) are by UUIDs. In Horizon EDA, all items get assigned 
an immutable UUID at time of their creation. This UUID is then used by 
other items to reference this item. 

To wrap up this introduction: 

   My biggest weakness is that i will eventually turn any arbitrary 
   electronics project into an excuse to write EDA software (and vice 
   versa).

(Based on https://twitter.com/mycoliza/status/824809235632447492)

Next: :doc:`Feature Overview<feature-overview>`
