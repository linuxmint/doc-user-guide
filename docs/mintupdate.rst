##############
Update Manager
##############

The Update Manager provides your operating system with software and security updates.

Updates are important because they keep your computer safe, eliminate bugs and can even add new features to your operating system.

Unfortunately they also sometimes introduce new issues called 'regressions', which can break things which worked well before.

To keep your computer safe and in good working condition, it is recommended to apply all available updates and to set up system snapshots, so that you can restore your system in case something goes wrong.

Core concepts
=============

Software regressions
********************

Updates keep your computer safe, eliminate bugs and even sometimes add new features to your operating system.

Unfortunately they also sometimes introduce new issues called 'regressions'.

Regressions are very common in the software industry. They're inherent to software development. Code changes can cause regressions. No matter how skilled developers are, they can't always predict every possible situation or test on every possible hardware specification.

When a regression happens, it breaks something which worked well before.

Sometimes it doesn't really matter, but sometimes it matters a lot.

It depends on what part of the operating system is affected and whether or not you're able to work around it or to fix it.

Say, the PDF reader is no longer able to print. Well, it's annoying... but it's not as problematic as if your network connection stopped working or if you were suddenly unable to boot the computer or to login.

In the latter case, it can be very problematic if you're not experienced with Linux and you don't know how to troubleshoot.

System snapshots
****************

Timeshift, the system snapshot utility, is available in all versions of Linux Mint.

It can be used to create snapshots manually but also to automate system snapshots.

Linux Mint recommends the automation of daily and boot snapshots.

If an update, a mistake, a bug or a malicious program breaks something on your computer, you can restore the operating system from any snapshot, thus cancelling the problem as if it never happened.

.. note::

    System snapshots only cover the operating system itself. They do not include or affect your personal data.

The different types of updates
******************************

There are different types of updates:

- 'Software updates' are updates which fix bugs (or also sometimes which bring new features).
- 'Security updates' are updates which patch vulnerabilities.
- 'Kernel updates' represent the installation of a newer kernel.

Security is very important but also very technical. Vulnerabilities don't always affect your computer and can be quite difficult to understand. Most people don't understand them at all and their personal computers are rarely at risk. That said, a security breach can have dire consequences, so it is always recommended to take them seriously.

Software updates aren't as important. They bring bug fixes or improvements which are not related to security.

.. note::

    In Linux Mint, kernel updates bring both security patches and bug fixes (and sometimes even new features), and they impact critical parts of the operating system. This makes kernel updates important from a security point of view, but also prone to regressions which can be hard to fix for novice users.


Kernel updates
==============

The kernel is the central part of the operating system. Among other things, it is responsible for hardware support.

.. note::

    In Linux Mint, kernel updates bring both security patches and bug fixes (and sometimes even new features), and they impact critical parts of the operating system. This makes kernel updates important from a security point of view, but also prone to regressions which can be hard to fix for novice users.

From a security point of view, it is important to apply kernel updates.

A kernel regression could however affect your ability to connect to the Internet, to start your desktop environment or even to boot the operating system.

For this reason it is important to be cautious when applying kernel updates and to know how to revert them when something goes wrong.

Multiple kernels can be installed
*********************************

When you apply an update, you replace the old version of the software with the new version.

Things are different when it comes to kernels. When you apply a "kernel update", you don't actually update the kernel, you install a new kernel alongside the existing one.

Every time you apply a kernel update, you install a new kernel on the system, without removing the old ones.

At boot time, the computer selects the most recent one.

Identifying the current kernel
******************************

If you want to know which kernel you are currently using, open a terminal and type:

.. code-block:: bash

	uname -a

Installing and removing kernels
*******************************

You can install and remove kernels from the Update Manager.

Select "View" -> "Linux Kernels" in the menu.

.. note::

    You cannot remove the kernel you are currently using. To remove it, you need to reboot and select a different kernel to boot with.

Selecting a kernel
******************

You can have multiple kernels installed, but you can only run one kernel at a time.

When you boot the computer, the very first screen is called the Grub menu. This menu allows you to choose operating systems but you can also use it to select a kernel.

.. note::

    If you only have one operating system installed, your boot sequence might skip the Grub menu. To force the Grub menu to show, boot the computer and keep pressing the left Shift key.

To select a kernel, choose "Advanced options" in the Grub menu. You should see all the kernels currently installed. Select the one you want to use and your computer will boot with that one.

Checking the DKMS status
************************

The kernel includes all open source drivers and these usually work very well. Proprietary drivers (NVIDIA, AMD, Broadcom...etc) are not included and they need to compile themselves against every kernel you install. This is done via a mechanism called DKMS.

If a proprietary driver isn't properly recompiled with DKMS for one of your kernels, it will not function correctly with that kernel.

After installing or removing a kernel, you can check your DKMS status, to make sure all proprietary drivers are properly installed for each of your kernels with the following command:

.. code-block:: bash

	dkms status

.. note::

    New kernel series usually become available before proprietary drivers support them via DKMS. If you are using proprietary drivers, it is recommended to stick to kernel updates and not to install kernels from series which are newer than the series of the recommended kernels.

Reverting a kernel update
*************************

If something doesn't work with the latest kernel you installed (or the latest kernel update), reboot, select the kernel you were previously using, remove the new kernel and reboot again.

Command line tools
==================

The Update Manager provides a command line utility called `mintupdate-cli`.

If you are experienced with Linux, you can use this tool in your scripts or your cron jobs to automate the installation of software updates.

Listing updates
***************

You can use the "list" command to list updates:

.. code-block:: bash

	mintupdate-cli list

You can use -s to only show the security updates.

You can use -k to only show the kernel updates.

For instance, the following command lists all security updates:

.. code-block:: bash

	mintupdate-cli list -s

Applying updates
****************

You can use the "upgrade" command to apply updates, using the same options.

For instance, the following command applies kernel updates:

.. code-block:: bash

	sudo mintupdate-cli upgrade -r -k

Note the -r argument, which was added to refresh the cache.

For more information on mintupdate-cli and a complete list of arguments, type:

.. code-block:: bash

	mintupdate-cli -h

