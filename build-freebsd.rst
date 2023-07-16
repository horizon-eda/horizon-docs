Building on FreeBSD
===================

.. note::
   Version 2.5 and earlier are built using ``make``,
   see `the documentation for that version <https://docs.horizon-eda.org/en/v2.5.0/build-freebsd.html>`_
   instead.

Building horizon on FreeBSD is as simple as running meson after you’ve cloned
the repo.

Install dependencies
--------------------

::

   sudo pkg install git pkgconf e2fsprogs-libuuid sqlite3 \
      gtkmm30 cppzmq libgit2 boost-libs glm opencascade podofo09 libarchive \
      meson cmake

Build it
--------

::

   meson setup build --cmake-prefix-path=/usr/local/lib
   meson compile -C build

Running
-------

The resulting binaries are self-contained and don’t require any external
data files like icons or so.
``horizon-eda`` is the main program executable. Run it from the build
directory:

::

   build/horizon-eda
