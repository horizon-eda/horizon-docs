Building on FreeBSD
===================

Building horizon on FreeBSD is as simple as ``gmake`` after you’ve cloned
this repo.

Install dependencies
--------------------

::

   sudo pkg install git gmake pkgconf e2fsprogs-libuuid sqlite3 \
      gtkmm30 cppzmq libgit2 boost-libs glm opencascade podofo libzip

Build it
--------

::

   gmake -j 4 #adjust this to the number of CPU cores

Running
-------

The resulting binaries are self-contained and don’t require any external
data files like icons or so.
``horizon-eda`` is the main program executable. Run it from the build
directory:

::

   build/horizon-eda
