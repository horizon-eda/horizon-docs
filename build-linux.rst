Building on Linux
=================

.. note::
   Version 2.5 and earlier are built using ``make``,
   see `the documentation for that version <https://docs.horizon-eda.org/en/v2.5.0/build-linux.html>`_
   instead.

Building horizon on Linux is as simple as running meson after you’ve cloned
the repo.

Install dependencies
--------------------

Make sure you got these dependencies installed:

*  Gtkmm3 ≥ 3.20
*  librsvg
*  util-linux
*  sqlite
*  zeromq
*  glm
*  libgit2
*  curl
*  opencascade / opencascade community edition
*  zeromq with C++ bindings: https://github.com/zeromq/cppzmq
*  podofo <0.10
*  libarchive
*  libspnav


On Ubuntu ≥20.04 run:

::

   sudo apt install libsqlite3-dev util-linux librsvg2-dev \
       libcairomm-1.0-dev libepoxy-dev libgtkmm-3.0-dev uuid-dev libboost-dev \
       libzmq5 libzmq3-dev libglm-dev libgit2-dev libcurl4-gnutls-dev liboce-ocaf-dev \
       libpodofo-dev libarchive-dev libspnav-dev meson cmake

On Arch Linux:

::

   sudo pacman -S zeromq cppzmq gtkmm3 cairomm librsvg sqlite3 libgit2 curl \
        opencascade boost glm podofo-0.9 libarchive libspnav meson cmake

On Fedora:

::

   sudo dnf install git make gcc gcc-c++ pkg-config cppzmq-devel opencascade-devel\
      gtkmm30-devel libgit2-devel libuuid-devel sqlite-devel librsvg2-devel\
      cairomm-devel glm-devel boost-devel libcurl-devel podofo-devel libarchive-devel\
      libspnav-devel meson cmake

On openSUSE Tumbleweed:

::

   sudo zypper in git make gcc gcc-c++ pkg-config cppzmq-devel oce-devel\
      gtkmm3-devel libgit2-devel libuuid-devel sqlite3-devel librsvg-devel\
      cairomm-devel glm-devel boost-devel libcurl-devel libpodofo-devel binutils-gold libarchive-devel\
      libspnav-devel meson cmake
      
On Solus:

:: 

   sudo eopkg it -c system.devel
   
::

   sudo eopkg it binutils-gold git glibc curl-devel libgtkmm-3-devel librsvg-devel \
      util-linux-devel sqlite3-devel libboost-devel zeromq-devel glm libgit2-devel \
      opencascade-ce-devel podofo-devel libarchive-devel cppzmq-devel meson cmake

Build it
--------

::

   meson setup build
   meson compile -C build

If ``meson compile`` isn't available yet, invoke ninja directly:

::

   ninja -C build

Running
-------

The resulting binaries are self-contained and don’t require any external
data files like icons or so.
``horizon-eda`` is the main program executable. Run it from the build
directory:

::

   build/horizon-eda
