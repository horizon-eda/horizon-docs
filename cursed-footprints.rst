Cursed Footprints
=================

Complicated footprints, such as this `QFN <https://www.vishay.com/docs/75921/sic437.pdf>`_
can sometimes be challenging to draw, so here are some tips and tricks
to make your life easier.

Import the drawing
-------------------

Even though technical drawings are sometimes not to scale, there's a 
good chance that they are, so it's worth trying to convert the drawing 
to a bitmap image and import it using the "Place picture" tool. In this 
particular case, I had to slightly adjust the aspect ratio for the 
dimensions to be as specified in the drawing. While it's not 
recommended to eyeball coordinates based on a bitmap image, it's a good 
way to verify that one has correctly reproduced the drawing.

Converting polygon to pads
--------------------------

For pads that require custom polygonal padstacks, draw the copper layer 
as a polygon and then use the "Convert to Pad" tool to convert the 
polygon into a pad. 

Snap to pad corners
-------------------

Often times, dimensions are specified between pad corners rather than 
pad centers. To simplify measuring and setting the distance between pad 
corners, enable the "Snap to pad corners" option in the "View & 
Selection" menu.
