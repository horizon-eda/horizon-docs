Project pool
============

Since version 2.0, each project is accompanied by a project pool. When using a part or any other pool item for the first time, it gets copied into the project pool along with its dependencies and is kept there until explicitly updated.
Same as regular pools, project pools can include other pools. In fact, that is the way to use parts from pools in the first place.

To get an overview of items that have been copied into the project pool, go to the "Cache" tab in the project pool manager. If an item has been modified in an upstream pool, select it in the list and click on "Update from pool". After that, reload the pool in the board/schematic editor or reopen them to get the updated items.

Over time, project pools may accumulate items that are no longer needed in the project. To get rid of them, click on "Remove unused" in the "Cache" tab in the project pool manager.
