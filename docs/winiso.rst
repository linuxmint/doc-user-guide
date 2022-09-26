
##############################
Windows ISOs and multiboot USB
##############################

Whether you want to make a USB stick which can boot multiple ISOs or simply boot from a Windows ISO image, we recommend using Ventoy.

Ventoy
======

Ventoy is an open source tool which creates a special USB stick.

That stick contains an exFAT partition in which you can copy multiple ISO files and an EFI partition where Ventoy puts its bootable menu.

When you boot on the Ventoy USB stick, the menu lists all the ISOs you placed in the exFat partition and you can boot any of them.

Installation
------------

Go to the `Ventoy release page <https://github.com/ventoy/Ventoy/releases>`_ to find the latest version of Ventoy.

Download the `tar.gz` archive and decompress it.

Right-click the decompressed ventoy folder and choose `Open in terminal`.

Run the following command to start Ventoy:

.. code-block:: bash

	sudo ./VentoyGUI.x86_64

Using Ventoy
------------

Choose the device which corresponds to your USB stick.

Press the `Install` button.

.. image:: images/ventoy.png

Once Ventoy is installed, your USB stick should now be called `ventoy`.

Mount it if's not already mounted.

Copy ISO files to the stick.

Boot on the Ventoy USB stick.

.. image:: images/ventoy_boot.jpg

The ISOs you copied should appear as bootable options.
