#####################
Printers and Scanners
#####################

To add a printer open `Printers` from the application menu and click on the `Add` button.

To scan a document open `Document Scanner` from the application menu.

.. warning::

	Linux Mint 20 shipped with a package called `ippusbxd`. This package prevents many printers from working correctly.
	If this package is installed on your computer, remove it and reboot.

.. note::

	Network printers can be automatically added and reappear even if you remove them. If you do not like this behaviour, remove the `cups-browsed` package.

Manufacturers
=============

Hewlett-Packard (HP)
--------------------

The HP drivers are called `HPLIP`. They are open-source and they are installed by default in Linux Mint. As a result, most HP printers and scanners work out of the box and don't require you to install any additional drivers.

Installing hplip-gui
~~~~~~~~~~~~~~~~~~~~

In addition to the already installed `hplip` driver, there is a package available in the Linux Mint repositories called `hplip-gui`.

This package provides the following utilities:

- An HP status tray icon
- HP Device Manager
- HPLIP Toolbox
- HPLIP Fax Utility
- Fax Address book

Although you do not need `hplip-gui` to use your HP device, it can provide extra information (such as ink levels) and help troubleshooting.

Brands which provide .deb packages
----------------------------------

The following brands provide Linux drivers for their printers and scanners in the form of `.deb` packages:

- Epson
- Lexmark
- Samsung
- Xerox

Look for Linux drivers on your manufacturer's website, download the packages and double-click them to install them with `Gdebi`.

.. hint::

	When you have a choice between different package options, choose `.deb`. If you have a choice for the package architecture choose `amd64` (note that this is sometimes called `x86_64` or even just `64-bit`).

Canon
-----

Canon provides Linux drivers for its printers and scanners. They have different websites for Europe, the USA and various countries.

When downloading drivers from Canon, choose the `debian Package archive` option.

If they come as `.tar.gz` archives, decompress them.

Canon driver archives usually contain an `install.sh` script which already has execution permissions. Run it and follow the instructions provided by Canon.

Brother
-------

Brother provides a utility to download and install the right driver for you.

Download the utility, choose `deb` when asked.

Decompress it, give it permission to execute and run it in a terminal:

.. code-block:: bash

	chmod a+rx ./linux-brprinter-installer*
	sudo ./linux-brprinter-installer*

Then follow the instructions provided by Brother.

Driverless Printing and Scanning
================================

A standard protocol called `IPP` was designed to communicate with printers and scanners over the network. Nowadays this protocol is supported by many devices.

Driverless printing and scanning consists in using `IPP` locally, i.e. to be able to print and scan without the need for any drivers at all.

ippusbxd
--------

`ippusbxd` was an early implementation of `IPP` over USB. It didn't work well and caused many issues. It was installed by default in Linux Mint 20. If this package is installed on your computer, make sure to remove it.

.. code-block:: bash

	apt remove ippusbxd

Then reboot your computer.

ipp-usb
-------

`ipp-usb <https://github.com/OpenPrinting/ipp-usb>`_ is a new implementation of `IPP` over USB. It works much better and recognizes many printers and scanners. If you are unable to make your device work using printing/scanning drivers, give `ipp-usb` a try.

First, remove your printer using the `Printers` configuration tool.

Then install `ipp-usb` from the repositories:

.. code-block:: bash

	apt install ipp-usb

Finally reboot the computer.

.. note::

	When ipp-usb is installed local printers are automatically added. They will reappear if you remove them.

.. warning::

	When ipp-usb is installed it takes over communication with all printing/scanning devices, i.e. printing/scanning drivers cannot work, they're inhibited.

sane-airscan
------------

`sane-airscan <https://github.com/alexpevzner/sane-airscan>`_ provides support for eSCL (Apple AirScan, AirPrint) and Microsoft WSD (WS-Scan, Web Services for Devices).

If you can't get your scanner to work give sane-airscan a try.

Install it from the repositories:

.. code-block:: bash

	apt install sane-airscan

And reboot the computer.
