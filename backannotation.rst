Backannotating connections
==========================

Sometimes, you may want to connect component pins based on their 
location on the board, such as connectors or FPGA IO pins. Wouldn't it 
be nice if you could define these connections directly in the board 
editor without going back and forth between board and schematic for 
every connection? With horizon EDA, you can!

How To
------

Use the tool "Draw connection line" to connect pads or junctions as 
desired. Then, use "Backannotate connection lines" to send these 
connections over to the schematic editor. The newly created connections
will appear as net stubs. After saving the schematic and reloading the 
netlist in the board editor, the connection lines will automatically be
replaced by airwires.

Limitations
-----------

Since this feature hasn't been there for very long, some things are 
still unsupported:

- Can't connect two existing nets
- Chaining connection lines (connecting two lines to one pad/junction) will not yield the expected result

