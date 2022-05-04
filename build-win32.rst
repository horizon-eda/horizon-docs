Building on Windows
===================

Install MSYS2
-------------

Download and run the msys2 installer from http://msys2.github.io/ I’ve
only tested with the 64bit version, 32bit should work as well (but come
on, it’s 2017…) Make sure that the path you select for installation
doesn’t contain any spaces. (Don’t blame me for that one)

Start MSYS console
------------------

Launch the Start Menu item “MSYS2 mingw 64 bit” you should be greeted
with a console window. All steps below refer to what you should type
into that window.

Install updates
---------------

Type

::

   pacman -Syu

if it tells you to close restart msys, close the console window and
start it again. Then run ``pacman -Syu`` again.

Install dependencies
--------------------

Type/paste

::

   pacman -S mingw-w64-x86_64-gtkmm3 git base-devel \
   mingw-w64-x86_64-boost mingw-w64-x86_64-curl \
   mingw-w64-x86_64-sqlite3  mingw-w64-x86_64-toolchain  \
   mingw-w64-x86_64-zeromq mingw-w64-x86_64-glm zip \
   mingw-w64-x86_64-libgit2 mingw-w64-x86_64-oce \
   mingw-w64-x86_64-podofo mingw-w64-x86_64-libarchive --needed

When prompted, just hit return. Sit back and wait for it to install
what’s almost a complete linux environment.

Before continuing you may change to another directory. It easiest to
type ``cd`` followed by a space and drop the folder you want to change
to on the window.

Clone horizon
-------------

::

   git clone http://github.com/horizon-eda/horizon
   cd horizon

Build it
--------

::

   make -j 4

You may adjust the number to the number of CPUs in your system to speed
up compilation. Expect 100% CPU load for several minutes. Due to debug
symbols the resulting executables are of considerable size.

Running
-------

You won’t be able to double-click the resulting executables since all
the required DLLs are in a directory unknown to windows. You’ll have to
launch them from the mingw shell using ``./horizon-eda`` for example.
For the pool download to work, you’ll have to copy the file
``/mingw64/ssl/certs/ca-bundle.crt`` to the directory the directory
``horizon-eda.exe`` resides in.

Packaging
---------

To create the zip archive as it’s available from the CI, run
``./make_bindist.sh``.
