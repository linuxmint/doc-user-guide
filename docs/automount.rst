###################################
Auto-Mounting Non-System Drives
###################################

You can automatically mount additional drives that aren't the Root (or /) drive.

Disk application
================

Firstly, open up the *disks* program from your start menu.

You will have a lust of drives that are there for you to choose from. Choose the one that you want to automount.

Nextly, left-click the partition that you want to mount, usually your largest partition. Click the settings button to pull up "Edit Mount Options".

:: note:

	Windows uses a completely different file system to Linux Mint. Although there is compatibility for ExFAT, It is better for newly bought drives to be put to the EXT4 file system.

In the Mount Options dialog that opens, you will see the option "User Session Defaults" is usually turned on. Turn it off to manually configure mount options.

You’ll now see more options like:
Mount at system startup: Make sure this is enabled to auto-mount at boot.
Show in user interface: This will allow the partition to appear in the file manager.

Make sure to enable both for auto-mounting to work properly.

Reboot your system and see on the desktop and file manager if your drive has mounted properly.

Troubleshooting
===============

Have you: 

1. Checked that the drive is under ``/mnt/`` instead of ``/media/`` when mounting? Change said directory if it is under ``/media/``.
2. Checked your drive? You may have to format it again if it fails to mount, but appears on computer.
3. Selected your disk in *disks* and use the menu in the top right corner and select "smart data and tests" to see if your drive is fine? you should see OKs in the "assessment" column.
4. Check your wiring if it doesn't show on the *disks* program?