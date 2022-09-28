#############
Lost Password
#############

If you forgot your password there are two ways to reset it:

- Recovery mode
- Chroot from live ISO

Recovery Mode
=============

Boot up the computer, and after the BIOS screen, hold down the left Shift key to force the boot menu to show up:

.. image:: images/grub.png

.. note::

    On some computers you might need to press the Escape key instead.

Select the second entry from the top, the one that starts with `Advanced options`.

Then on the next screen, select the second entry again, the one that ends with `(recovery mode)`.

Linux Mint will then starts in recovery mode and present this menu:

.. image:: images/recovery.png

Select `root` to get a root prompt and press Enter.

Use the passwd command to reset your password. Say your username is `joe`, type:

.. code-block:: bash

    passwd joe

Chroot from Live ISO
====================

Boot up the computer from the live ISO.

Once in the live session launch `Gparted` from the applications menu.

.. image:: images/chroot.png

Identify your Linux Mint partition (usually a large ext4 partition). In the example above the Linux Mint partition is `/dev/sda5`.

Open a terminal and type the following commands:

.. code-block:: bash

    mkdir hdd
    sudo mount /dev/sda5 hdd
    sudo chroot hdd
    passwd joe

Replace `/dev/sda5` with your Mint partition and `joe` with your username.

