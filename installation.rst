Installation
============

So you wanna give horizon a test drive? Great! Here's how.

Stable release
--------------

A known-good snapshot from ongoing development.

Windows
^^^^^^^

Download and run the MSI installer from `GitHub releases <https://github.com/horizon-eda/horizon/releases>`_.

Linux
^^^^^

Keep in mind that binary packages provided by your distribution might be out of date.

Flatpak
"""""""

Get the latest stable release from `Flathub <https://flathub.org/apps/details/org.horizon_eda.HorizonEDA>`_.


Debian, Ubuntu
""""""""""""""

Debian builds are hosted by `packagecloud <https://packagecloud.io/>`_.

First, follow the `instructions <https://packagecloud.io/horizon-eda/horizon-eda/install>`_ to add the repository.
When done, you can install it using apt:

::

    sudo apt-get install horizon-eda-upstream


Arch Linux
""""""""""

For Arch Linux, there's an `AUR package <https://aur.archlinux.org/packages/horizon-eda>`_.

NixOS
"""""

Horizon EDA is `packaged for NixOS <https://github.com/NixOS/nixpkgs/blob/master/pkgs/applications/science/electronics/horizon-eda/default.nix>`_.

::

  nix-env -iA horizon-eda


Solus
"""""

.. note::

    A package request to the official solus repository is filed. 


.. warning::

   The unofficial binary package is build with unstable-x86_64 profile. For a
   build against stable main_x86_64 profile of Solus Shannon await successful
   package acceptance to solus repository.

For `Solus <https://getsol.us/home/>`_ you can download the binary from https://github.com/maikwoehl/horizon-eopkg/releases and install it with:

::

  sudo eopkg install horizon-eda-*-.eopkg
    
Or as an alternative you can directly build the package yourself and install it:

::

  sudo eopkg bi --ignore-safety https://raw.githubusercontent.com/maikwoehl/horizon-eopkg/v2.1.0/pspec_x86_64.xml
  sudo eopkg it horizon-eda-*.eopkg; sudo rm horizon-eda-*.eopkg

FreeBSD
^^^^^^^

Horizon EDA is available in the FreeBSD `ports <https://www.freshports.org/cad/horizon-eda/>`_.

::

  sudo pkg install horizon-eda


Build from source
"""""""""""""""""


If you want to compile it yourself, download the source tarball from
`GitHub releases <https://github.com/horizon-eda/horizon/releases>`_ and follow the instructions in :doc:`build-linux`.


Development version
-------------------

Usually works, but might break occasionally, so use at your own risk.
Recommended if you want to get the latest in features and bug fixes.

Windows
^^^^^^^

Grab the latest build from `AppVeyor CI <https://ci.appveyor.com/project/carrotIndustries/horizon/build/artifacts>`_ 
and unzip it somewhere. Note that these are 64bit binaries. In case a
build is still running or someone broke the build, you can download past
builds from
`the build history <https://ci.appveyor.com/project/carrotIndustries/horizon/history>`_
(click on artifacts to get the zip)

Linux
^^^^^

Clone the repository and see :doc:`build-linux` for
instructions on how to build horizon on Linux.

FreeBSD
^^^^^^^

Clone the repository and see :doc:`build-freebsd` for
instructions on how to build horizon on FreeBSD.


Next: :doc:`Setup a pool <pool-setup>`
