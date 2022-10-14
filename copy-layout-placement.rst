Copying layout and placement
=============================


Motivation
----------

Often times, your design includes similar-but-not-identical sections
such as voltage regulators. Wouldn’t it be nice if you’d only had to do
layout and placement once and then copy it to the other instances? Ever
wanted to reuse layout and placement from another project?
Horzion EDA lets you do just that in a simple two-step process.

TL;DR, I just want to copy a circuit form another project
---------------------------------------------------------

In the source schematic
~~~~~~~~~~~~~~~~~~~~~~~

 - Assign a group to the circuit you want to copy with the "Set new group tool"
 - Assign unique tags to all to-be-copied components with the "Set tags from Ref. Desig." tool
 - Copy the circuit the clipboard

In the destination schematic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 - Paste the copied circuit

In the source board
~~~~~~~~~~~~~~~~~~~

 - Copy all items of the circuit, i.e. packages, tracks, vias, planes, etc. to the clipboard

In the destination board
~~~~~~~~~~~~~~~~~~~~~~~~

 - Place the package that's the reference for the pasted layout
 - Place all other packages of the circuit, their placement doesn't matter
 - Select all packages of the pasted circuit
 - Invoke the "Paste placement" tool and click on the reference package
 - All other packages of the pasted circuit should now be placed as they were on the source board
 - Select any package in the pasted circuit and invoke the "Paste relative tool"
 - All items copied from the source board should now be in the right place relative to the reference package

Groups & Tags
-------------

For this feature to work, you’ll first need to tell Horizon EDA how the
components fit together. This is accomplished by assigning groups and
tags to components. Each section, i.e. all components associated with
one voltage regulator, get assigned one group. To do so, select all
symbols of one section and use the tool “Set new group” to assign all of
them to a new group. For making groups and tags visible on the
schematic, use the “Toggle group & tag visibility”. A components group
and tag will then show up below the reference designator.

To tell Horizon EDA the matching components in each group, these get
assigned identical tags. Since a newly-placed component will already be
assigned a unique tag and groups and tags get preserved on copy/paste
other instances of the same circuit will likely have the appropriate
tags already set. To change the tag on a component, use the “Set tag”
tool. To automatically assign a unique tag to every component, use the
"Set tags from Ref. Desig." tool.

When you’re done, the schematic should roughly look like this (with the
boxes added for clarification). All components inside a yellow box
belong to the same group, all inside a red box belong to the same tag.

.. image:: images/groups-tags.png

You may use the “Highlight group/tag” action to make sure that you got
the assignments right.


Board
-----

Place and route any group as usual.

Paste placement
~~~~~~~~~~~~~~~

For each group, place the package you’d like the other packages to be
referenced to at the target position and place all other packages
anywhere. Then, select all packages in the routed group and invoke the "Copy" action.
This can also be in another project as long as the groups and tags match.

Next, select all packages of the group that you’d like to
apply the placement to and start the “Paste placement” tool. Click on the
reference package (any pad or centroid) in the already placed group and
all selected packages will be placed accordingly.

Paste relative
~~~~~~~~~~~~~~

Select everything (packages will be ignored) you want to copy in
the routed group and copy it to the clipboard. Then invoke the "Paste relative"
tool on any package in the destination group. Keep in mind that the
package placement in the destination group should already match the layout
of the source group to get useful results. As with the paste placement tool,
this also works across projects.


