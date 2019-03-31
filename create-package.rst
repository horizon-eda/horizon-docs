Creating a Package
===================


A PCB layout can only be as good as the footprints it uses, that’s why
it’s important to create high-quality footprints (called packages).

As far as horizon is concerned a package consists of these things:

-  The pads the part gets soldered onto

   -  Copper layers (top/bottom/inner)
   -  Holes (for TH parts)
   -  Solder mask opening
   -  Paste mask

-  Package outline
-  Assembly outline and reference designator
-  Silkscreen graphics and text
-  Courtyard outline

Pads
----

Each pad is defined by its padstack and parameters applied to the
padstack. For details on padstacks see [[here|Padstacks]]. Since the
pads are probably a package’s most important feature, it’s makes sense
to start with these. You can either place pads manually using the “Place
pad” tool or have them placed automatically according to commonly used
patterns using the “Footprint gen.” dialog available from the top bar.
After having placed the pads, they still have their default size, which
is very likely not what you want. To fix this, select the pads you’d
like to modify and use the “Edit pad” tool to add parameters to a pad.
Depending on the selected padstack, certain parameters are understood.
The most commonly used are obviously pad width and height. Use the
checkmark button next to a parameter to apply it to all selected pads.

Package outline
---------------

The package outline is used for visualizing what the part’s outline
looks like, hence it should follow the part’s nominal dimensions. You
may use the “import DXF” tool for importing a DXF drawing obtained from
a STEP model or otherwise. Since the package outline’s purpose is purely
visual, you can use either lines or polygons. Only include pins if they
significantly contribute to the part’s appearance.

Assembly outline
----------------

The assembly outline ends up on the assembly drawing (not yet
implemented) and is intended to aid assembling and inspecting the PCA.
The assembly outline layer thus contains only these items: A polygon
indicating the part’s outline, optionally pins if they significantly
contribute to the part’s appearance and the part’s reference designator.
Opposed to the package outline, the assembly is just a rough
approximation of the part’s shape. It has to include some sort of visual
indication of the part’s pin 1 location. Use the “Draw polygon
rectangle” tool and its decoration options for drawing such outline. For
the reference designator, place a text containing “$RD” with such size,
that it fits withing the assembly outline even when being prefix + 4
digits long.

Silkscreen
----------

The silkscreen graphics purpose is to clarify a parts location and
orientation during manual assembly and visual inspection, so it should
include some sort of pin 1 marker if the part is orientation-sensitive.
Don’t place a dot at pin 1, instead shorten/elongate the silkscreen
graphics. The recommended line with is 0.15mm. Also place a text “$RD”,
0.15mm in with on the silkscreen layer.

Courtyard
---------

The courtyard denotes the space needed by the part that mustn’t be
occupied by other parts in order to leave enough room for assembly.
Since the size of the courtyard needs to be adjusted depending on the
users manufacturing requirements, it has to be set using a parameter
program. At 0mm courtyard expansion the courtyard outline is the
(rectangular) hull around copper pads and package outline. To create a
rectangular courtyard outline that can be parametrized, do this:

Use the “Generate courtyard” tool to generate the initial courtyard at
0mm expansion. If that doesn’t result in the desired polygon, use the
“Draw polygon rectangle” tool for drawing the initial courtyard and set
its parameter class to “courtyard” using the property editor on the
right side of the window.

Open the “Parameters” Window and click on “Insert courtyard program”. If
all goes well, this should add the courtyard program and as the
parameter “Courtyard expansion” set to 0.25mm.
