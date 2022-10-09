
#####################
Printers and Scanners
#####################

Driverless Printing and Scanning (IPP)
======================================

Since version 21, Linux Mint features driverless printing and scanning:

- Printers and scanners are detected and added automatically.
- Communication with the device is done via a standard protocol called `IPP`.
- No drivers are needed.
- Installed drivers are not used.

This standard protocol works with many devices, so for most printers and scanners, there is nothing to do. Everything just works out of the box.

To print a document open `File` -> `Print...` in your application.

To scan a document open `Document Scanner` from the application menu.

Manufacturer Drivers
====================

If your device doesn't work well with `IPP` you can use drivers from your manufacturer instead.

In this case you need to:

- Disable `IPP`
- Install your manufacturer's drivers

Disabling IPP
-------------

IPP takes priority so as long as it's installed, drivers won't be used.

To remove IPP support from your computer open a terminal and type:

.. code-block:: bash

	apt remove ipp-usb sane-airscan

Hewlett-Packard (HP)
--------------------

The HP drivers are called `HPLIP`.

They are open-source and they already are installed by default in Linux Mint.

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

Installing the proprietary plug-in
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some HP printers require proprietary software technologies to allow full access to printer features and performance. Unfortunately, these technologies cannot be open sourced, but to resolve this HP uses a binary plug-in for these printers.

To see if your printer requires the HP plugin-in, check the list of devices at the `HP Developer Website <https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html>`_.

To install the plugin-in, open a terminal and type:

.. code-block:: bash

	apt install python3-pyqt5
	sudo hp-setup

Then follow the instructions written on that website.

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

Troubleshooting
===============

Adding IPP support
------------------

In Linux Mint 20.x `IPP` isn't installed by default.

If you want to give it a try, remove your printer using the `Printers` configuration tool.

Then install `ipp-usb` and `sane-airscan` from the repositories:

.. code-block:: bash

	apt install ipp-usb sane-airscan

Finally reboot the computer.

Disabling network printers detection
------------------------------------

Network printers are automatically added and reappear even if you remove them.

If you do not like this behaviour, remove the `cups-browsed` package.

Removing ippusbxd
-----------------

`ippusbxd` was an early implementation of `IPP` over USB. It didn't work well and caused many issues. It was installed by default in Linux Mint 20. If this package is installed on your computer, make sure to remove it.

.. code-block:: bash

	apt remove ippusbxd

Then reboot your computer.

Additional info
---------------

More information is available online on:

- `ipp-usb <https://github.com/OpenPrinting/ipp-usb>`_
- `sane-airscan <https://github.com/alexpevzner/sane-airscan>`_
