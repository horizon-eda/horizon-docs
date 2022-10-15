Installation
============

So you wanna give horizon a test drive? Great! Here's how.

Stable release
--------------

A known-good snapshot from ongoing development.

Windows
^^^^^^^

Download and run the MSI installer from `GitHub releases <https://github.com/horizon-eda/horizon/releases>`_.
Only versions of Windows in `active support
<https://endoflife.date/windows>`_ are supported by Horizon
EDA. Older versions of Windows may work, but bugs specific to them
won't be fixed.

Linux
^^^^^

Keep in mind that binary packages provided by your distribution might be out of date.

Flatpak
"""""""

Get the latest stable release from `Flathub <https://flathub.org/apps/details/org.horizon_eda.HorizonEDA>`_.


Debian, Ubuntu
""""""""""""""

Debian builds are hosted on the `Selfnet mirror <https://mirror.selfnet.de/horizon-eda/>`__.

To add the repository, first download the `GPG key <https://horizon-eda.org/horizon-eda-debian.gpg>`_ and save it somewhere, for example in ``/usr/local/share/keyrings``.

Then add this line to ``/etc/apt/sources.list`` or a new file in ``/etc/apt/sources.list.d/``, replacing ``<distro>`` with either ``ubuntu`` or ``debian`` and ``<release>`` with the release name you're running.

See the `directory listing <https://mirror.selfnet.de/horizon-eda/>`__ for the list of currently supported distributions/releases.

::

 deb [signed-by=/usr/local/share/keyrings/horizon-eda-debian.gpg] https://mirror.selfnet.de/horizon-eda/<distro>-<release>/ <release> main


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

Grab the latest build from the `Selfnet mirror <https://mirror.selfnet.de/horizon-eda/win64-ci/>`__
and unzip it somewhere. Note that these are 64bit binaries. The
download URL is also shown on GitHub Actions.

Linux
^^^^^

Clone the repository and see :doc:`build-linux` for
instructions on how to build horizon on Linux.

FreeBSD
^^^^^^^

Clone the repository and see :doc:`build-freebsd` for
instructions on how to build horizon on FreeBSD.


Next: :doc:`Setup a pool <pool-setup>`
