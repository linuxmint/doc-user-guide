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
