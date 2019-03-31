Building on Linux
===================

Building horizon on Linux is as simple as ``make`` after you’ve cloned
this repo. Make sure you got these dependencies installed:

-  Gtkmm3 ≥ 3.20
-  cairomm-pdf
-  librsvg
-  util-linux
-  yaml-cpp
-  sqlite
-  boost
-  zeromq
-  glm
-  libgit2
-  curl
-  opencascade / opencascade community edition
-  zeromq with C++ bindings: https://github.com/zeromq/cppzmq

On Ubuntu ≥17.04 run:

::

   sudo apt install libyaml-cpp-dev libsqlite3-dev util-linux librsvg2-dev \
       libcairomm-1.0-dev libepoxy-dev libgtkmm-3.0-dev uuid-dev libboost-dev \
       libzmq5 libzmq3-dev libglm-dev libgit2-dev libcurl4-gnutls-dev liboce-ocaf-dev 

On Arch Linux:

::

   sudo pacman -S yaml-cpp zeromq gtkmm3 cairomm librsvg sqlite3 libgit2 curl opencascade boost glm

On Fedora 25/26/27:

::

   sudo dnf install git make gcc gcc-c++ pkg-config cppzmq-devel OCE-devel\
      gtkmm30-devel libgit2-devel libuuid-devel yaml-cpp-devel sqlite-devel librsvg2-devel\
      cairomm-devel glm-devel boost-devel libcurl-devel

The resulting binaries are self-contained and don’t require any external
data files like icons or so.
