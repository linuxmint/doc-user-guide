#########
Bluetooth
#########

Enabling/disabling Bluetooth
============================

Rfkill
------

Bluetooth can be disabled by using a software kill switch.

On some laptops, a hardware kill switch is also provided either via a special Function key or key combination or a dedicated physical button or mechanism.

Using the `rfkill` command, you can see the state of these switches.

Open a terminal and type:

.. code-block:: bash

    rfkill list

The output lists the state of software and hardware kill switches for all your wireless devices:

.. image:: images/rfkill.png

In the picture above you can see that Bluetooth is neither `Soft blocked` nor `Hard blocked` and is therefore enabled.

You can use rfkill to block (i.e. disable) or unblock (i.e. enable) bluetooth:

.. code-block:: bash

    rfkill block bluetooth
    rfkill unblock bluetooth

Blueman
-------

Blueman is the default Bluetooth Manager in Linux Mint.

It provides the little Bluetooth icon in your system tray.

To disable Bluetooth right-click the tray icon and select `Turn Bluetooth Off`.

To enable Bluetooth right-click the tray icon and select `Turn Bluetooth On`.

The very first time you open Blueman it asks if Bluetooth should be enabled automatically.

To check whether this feature is enabled open a terminal and type:

.. code-block:: bash

    gsettings get org.blueman.plugins.powermanager auto-power-on

It `auto-power-on` is set to `true`, Blueman automatically unblocks Bluetooth at startup.

If you want to persistently disable Bluetooth you need to set `auto-power-on` to `false`:

.. code-block:: bash

    gsettings set org.blueman.plugins.powermanager auto-power-on false

Systemd-rfkill
--------------

Systemd provides a service which saves the state of your kill switches during shutdown and restores them on the next boot.

This service is a core part of systemd and is installed in Linux Mint by default.
