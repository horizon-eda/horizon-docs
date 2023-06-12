Building on Linux
=================

Building horizon on Linux is as simple as ``make`` after you’ve cloned
this repo.

Install dependencies
--------------------

Make sure you got these dependencies installed:

*  Gtkmm3 ≥ 3.20
*  cairomm-pdf
*  librsvg
*  util-linux
*  sqlite
*  boost
*  zeromq
*  glm
*  libgit2
*  curl
*  opencascade / opencascade community edition
*  zeromq with C++ bindings: https://github.com/zeromq/cppzmq
*  podofo
*  libarchive
*  libspnav

The C++ compiler needs to support ``std::filesystem``, for GCC this
requires version 8 or newer.

On Ubuntu ≥18.04 run:

::

   sudo apt install libsqlite3-dev util-linux librsvg2-dev \
       libcairomm-1.0-dev libepoxy-dev libgtkmm-3.0-dev uuid-dev libboost-dev \
       libzmq5 libzmq3-dev libglm-dev libgit2-dev libcurl4-gnutls-dev liboce-ocaf-dev \
       libpodofo-dev libarchive-dev libspnav-dev

On Arch Linux:

::

   sudo pacman -S zeromq cppzmq gtkmm3 cairomm librsvg sqlite3 libgit2 curl \
        opencascade boost glm podofo-0.9 libarchive libspnav

On Fedora:

::

   sudo dnf install git make gcc gcc-c++ pkg-config cppzmq-devel opencascade-devel\
      gtkmm30-devel libgit2-devel libuuid-devel sqlite-devel librsvg2-devel\
      cairomm-devel glm-devel boost-devel libcurl-devel podofo-devel libarchive-devel\
      libspnav-devel

On openSUSE Tumbleweed:

::

   sudo zypper in git make gcc gcc-c++ pkg-config cppzmq-devel oce-devel\
      gtkmm3-devel libgit2-devel libuuid-devel sqlite3-devel librsvg-devel\
      cairomm-devel glm-devel boost-devel libcurl-devel libpodofo-devel binutils-gold libarchive-devel\
      libspnav-devel
      
On Solus:

:: 

   sudo eopkg it -c system.devel
   
::

   sudo eopkg it binutils-gold git glibc curl-devel libgtkmm-3-devel librsvg-devel \
      util-linux-devel sqlite3-devel libboost-devel zeromq-devel glm libgit2-devel \
      opencascade-ce-devel podofo-devel libarchive-devel cppzmq-devel

Build it
--------

::

   make -j 4 #adjust this to the number of CPU cores

Add ``WITH_SPNAV=0`` to disable space navigator support and remove the dependency on libspnav

Running
-------

The resulting binaries are self-contained and don’t require any external
data files like icons or so.
``horizon-eda`` is the main program executable. Run it from the build
directory:

::

   build/horizon-eda
