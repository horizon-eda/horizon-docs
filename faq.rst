Frequently asked questions
==========================

How do I connect two net segments and why am I getting duplicate net name warnings?
------------------------------------------------------------------------------------

Unlike the schematic editor of other tools, the one in Horizon EDA actually
knows about nets and makes operations that change connectivity explicit to
prevent unintended connectivity. Selecting anything from a net such as a net line
or a net label opens the net in the property editor on the right side of
the window. It's important to stress that what's in the property editor is
the entire net and not just the net segment. That's why changing the name there
changes the name of the entire net and never modifies connectivity.

For reconnecting net segments, use the "Move net segment to other net" and
"Move net segment to new net" tools.

See also `This issue <https://github.com/horizon-eda/horizon/issues/702>`_.

How do I do QR codes?
---------------------

Using the QR code generator in Inkscape and the DXF import tool. Generating
the QR codes requires some precautions however since the pixels in the QR
code must not share edges for the "Line loop to polygon" tool to work
properly.

To do so, first draw a rectangle 100×100 in size, units don't matter and
convert it to a path using the "Object to path" tool. Keep it selected. Then, invoke the
QR code generator from Extensions → Render → Barcode → QR code, select
"Clones" and generate the QR code. Once that's done, select the initial
rectangle and shrink it to 99×99. The QR code should now contain gaps.
If everything's right, export the document as a DXF.

Import this DXF in Horizon EDA and remove the surrounding rectangle.
Finally, select the lines making up the QR code pixels and invoke the
"Line loop to polygon" tool to turn the lines into filled polygons.

See also `this question <https://horizon-eda.discourse.group/t/feature-request-qr-code-import/91/2>`_ on the forum.
Note that the description given there doesn't work on more recent versions
of Inkscape.

How do I add logos to my board?
-------------------------------

First make sure that the logo is in a vector format such as SVG, PDF or EPS.
If that's not the case either try to obtain a vector version of the
logo or trace it using Inkscape's "Trace bitmap" tool.

Open the logo in Inkscape and convert it into a set of closed paths
without holes that consist only of straight lines and no bezier curves.

#. Use the Path → Object to Path tool to convert everything into paths.
#. Remove any holes by either modifying the path or creating cut-ins with the Path → Difference tool.
#. Remove all curved edges with the Extensions → Modify Path → Flatten  beziers tool.
   Adjust the flatness for a good compromise between quality and number of points.

Once that's done, export the document as a DXF file.

Import that DXF into Horizon EDA with the "Import DXF" tool. Keep in
mind that the scale or offset might be way off from what you need, so
try zooming out if you're not seeing anything. Right now, everything's
just a set of connected lines and not filled. Use the "Line loop to
polygon" tool to convert the zero-width lines into filled polygons.
Adjust the size to your need with the "Scale" tool.

If you want to reuse your Logo on multiple boards, consider putting it
into a decal in a pool. Compared to packages, decals have the advantage
that they can be scaled as needed and aren't part of the netlist.

Components in the 3D view are all over the place
------------------------------------------------

This seems to be specific to AMD GPUs on Windows. Updating the drivers
seems to fix it: See also `Issue 691 <https://github.com/horizon-eda/horizon/issues/691>`_.


Does it run on Mac OS?
----------------------

In short, `no <https://github.com/horizon-eda/horizon/issues/271>`_.
