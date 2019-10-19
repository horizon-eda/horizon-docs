Layers
======

Board, package and padstack editor use the widget shown below to specify how layers are displayed.

.. image:: images/layers.png

The selected layer is called the "work layer" and is always visible and drawn on top of all other layers. Use :kbd:`Page up/down` to move the work layer to the next or previous layer.
Pressing :kbd:`1` selects the "Top Copper" layer, :kbd:`2` selects the "Bottom Copper" layer, :kbd:`3 … 0` select inner layers if present.

Clicking on the eye toggles a layer's visibility. Keep in mind that the work layer is always visible even if it's set to be invisible.

Clicking on the colored box cycles through a layer's display modes:

- Solid color: Layer is drawn with outlines and fill, overlapping filled objects on the same layer will appear brighter.
- Solid color with black border: Layer is drawn just filled, overlapping objects look the same as non-overlapping ones.
- Black with colored border: Layer is drawn just with outlines.
- Striped: Same as first, but areas are striped rather than filled.
