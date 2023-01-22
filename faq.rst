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

Components in the 3D view are all over the place
------------------------------------------------

This seems to be specific to AMD GPUs on Windows. Updating the drivers
seems to fix it: See also `Issue 691 <https://github.com/horizon-eda/horizon/issues/691>`_.


Does it run on Mac OS?
----------------------

In short, `no <https://github.com/horizon-eda/horizon/issues/271>`_.
