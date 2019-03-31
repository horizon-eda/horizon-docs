The Pool
========

So what's all this Pool stuff anyhow? Many EDA packages organize
packages, symbols and the like in libraries. (My) experience has show
that these are often messy and version-controlling these is difficult
since many independent parts are put in a single file. Especially the
latter makes collaboration difficult.

With horizon, there are no libraries. Instead all the non-project things
(symbols, etc.) are put in one pool. Just like the "central library"
approach common among the more enterprisey EDA packages. Although you
can create your own pool, you are strongly encouraged to use the pool
over at
`https://github.com/carrotIndustries/horizon-pool/ <https://github.com/carrotIndustries/horizon-pool/>`__.
To add new parts to it, simply submit a merge request.

Right now, the pool is organized using tags instead of a hierarchical
system since these often lead to confusion over aspects like whether to
group parts by manufacturer or other attributes.

To keep the pool nice an clean, only add parts you can actually buy with
their corresponding symbols, entities, etc. So don't add some part
called 7805, instead add a MC7805BDTRKG manufactured by ON
Semiconductor.

Each of the items below is stored in a single json file in the
respective directory, i.e. /symbols, /parts, etc. The exact location
within this directory is irrelevant, as long the json file is stored in
the correct directory. It's important for the files to end in ".json" to
be picked up by the pool updater. To make searching for parts more
convenient, the metadata of all json files is aggregated into a sqlite
database. This is what the 'Update pool' button in the Pool Manager is
for.

Structure of the pool
---------------------

See
`here <https://github.com/carrotIndustries/horizon/blob/master/doc/pool.pdf>`__
for a visual overview.

Parts
~~~~~

On top of pool's structure there is the part. To avoid redundancy, a
part can inherit its definition from another part. This is intended to
be used for groups of parts that only differ in some property like
resistance or output voltage for fixed voltage regulators. Each part can
be accompanied with parametric data to make it easier to search for.
Right now, this feature is work in progress, as there's no UI to search
for parts based on parametric data. A Part also contains the mapping of
Entity pins to a Package pads.

Packages
~~~~~~~~

A Package defines the footprint of a part. If the part's manufacturer
provides a reasonable footprint recommendation, use this one. Only use
generic packages if there isn't any. For details on packages see
[[here|Creating-a-Package]].

Entities
~~~~~~~~

An Entity is a Part's netlist representation. Parts that are logically
the same like different shapes of USB connectors therefore can all share
the same Entity, e.g. "USB connector with shield and ID". Entities
themselves consist of one or more Unit.

Units
~~~~~

A Unit actually defines a part's logical pins. For parts that only
consist of one "gate" like a voltage regulator, their entity simply
references one unit. For parts consisting of multiple "gates" like a
dual operational amplifier or a big MCU, each gate references one unit.
Having units separate from entities allows multiple entities to share
the same units. The entity for a single logic gate thus is supposed to
reference the same unit as a quad one. Apart from a name, a pin has a
direction (for ERC) and optionally alternate pin names to deal with pins
having multiple functions as it's common among MCUs.

Symbols
~~~~~~~

A symbol is used in the schematic to represent a unit. Contrary to other
EDA applications, a symbol just displays the pins from its unit and
doesn't define these.
