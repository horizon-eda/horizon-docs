Vias
====

As of version 2.5, Horizon EDA supports blind and buried vias. A via 
consists of a Padstack that has the type Via, a parameter set that 
sets the Padstack's parameters such as via and hole diameter and a span 
that defines whether the via goes all the way through the board or is a 
blind/buried via. There are three ways to define these elements of via 
that can be selected by the source property.

Local
-----

In this mode, all elements (padstack, parameter set and span) of the 
via are set on the via itself. The via isn't affected by any rules.

Rules
-----

In this mode, the "Vias" rules are evaluated based on the via's net to 
set its Padstack and parameter set. The span is set on the via 
itself. This mode is recommended for through vias.

Definition
----------

In this mode, all elements of the via are set as per the selected via 
definition. Via definitions are managed by the "Via definitions" rule.

This mode is recommended for boards that use a stackup that allows for 
blind or buried vias.

Misc. notes
-----------

The STEP export omits non-through vias. For the gerber export, you'll 
need to manually assign filename suffixes for each drill span used on 
the board. 
