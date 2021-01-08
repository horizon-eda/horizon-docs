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

Add bintray's key to the apt keyring:
::

   curl https://bintray.com/user/downloadSubjectPublicKey?username=bintray | sudo apt-key add -

Add one of these lines to ``/etc/apt/sources.list``:

::

    # Debian Buster
    deb https://dl.bintray.com/horizon-eda/horizon-eda-buster horizon-eda-buster main

    # Ubuntu Bionic (18.04)
    deb https://dl.bintray.com/horizon-eda/horizon-eda-bionic horizon-eda-bionic main

    # Ubuntu Focal (20.04)
    deb https://dl.bintray.com/horizon-eda/horizon-eda-focal horizon-eda-focal main

    # Ubuntu Groovy (20.10)
    deb https://dl.bintray.com/horizon-eda/horizon-eda-groovy horizon-eda-groovy main

Update the apt cache:

::

    sudo apt-get update

Install it:

::
    
    # Debian Buster
    sudo apt-get install -t horizon-eda-buster horizon-eda

    # Ubuntu Bionic (18.04)
    sudo apt-get install -t horizon-eda-bionic horizon-eda

    # Ubuntu Focal (20.04)
    sudo apt-get install -t horizon-eda-focal horizon-eda

    # Ubuntu Groovy (20.10)
    sudo apt-get install -t horizon-eda-groovy horizon-eda

These packages are built from the `horizon-deb repo <https://github.com/horizon-eda/horizon-deb>`_ and are published on `bintray <https://bintray.com/horizon-eda>`_.



Arch Linux
""""""""""

For Arch Linux, there's an `AUR package <https://aur.archlinux.org/packages/horizon-eda>`_.


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
instructions on how to build horizon on linux.


Next: :doc:`Setup a pool <pool-setup>`
