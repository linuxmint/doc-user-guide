##############
Grub Boot Menu
##############

Grub is the boot menu.

If you have more than one operating system installed, it allows you to select which one to boot.

Grub is also useful for troubleshooting. You can use it to modify the boot arguments or to boot from an older kernel.

How to make the Grub menu always visible
========================================

If you only run Linux Mint and there are no other operating systems on the computer, the menu is hidden by default.

To make it visible, as root, add these lines to `/etc/default/grub.d/90_custom.cfg`:

.. code-block:: bash

    GRUB_TIMEOUT="5"
    GRUB_TIMEOUT_STYLE="menu"

Then type the following commands in a terminal:

.. code-block:: bash

    sudo update-grub

How to theme the Grub menu
==========================

For compatibility reasons, some releases sometimes ship without a Grub theme:

.. image:: images/grub.png

You can make it look like this:

.. image:: images/grub2-theme-mint.png

To do so, open a terminal and type:

.. code-block:: bash

    apt reinstall -o Dpkg::Options::="--force-confmiss" grub2-theme-mint

Or if you have a HiDPI screen, type this instead:

.. code-block:: bash

    apt reinstall -o Dpkg::Options::="--force-confmiss" apt install grub2-theme-mint-2k