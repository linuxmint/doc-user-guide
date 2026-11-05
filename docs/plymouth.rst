###############################
Boot Screen (Plymouth)
###############################

When you boot up your system and get past the UEFI/BIOS "Manufacturer" Screen, You should generally be greeted by a spinning logo of Linux Mint. 

By pressing `Esc`, You are able to see Systemd, the program that handles everything regarding startup and background services, work its magic.

Changing the Boot Screen
=========================

Firstly, Are you changing the theme to a custom one, or do you just wish to change it to another one already set up?

Custom Boot Screen
----------------------

Firstly, You first open the `Files` app, and go to `/usr/share/plymouth/themes`

Secondly, Right click and select "Open as Root".

Then, Drag in your chosen folder with your boot screen image files and accompanying `.plymouth` file

.. note::

    If it is an animated boot screen, Make sure there that the two-step module is enabled with `ModuleName=two-step` in the .plymouth file, Additionally adding the proper [two-step] section as shown `here <https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/desktop_migration_and_administration_guide/plymouth>`_ . You may have to fiddle with settings in the [two-step] category to get it to render properly.

Next, you want to make sure that Plymouth knows that your boot screen is an option with the following command inside of the `Terminal` application:

`sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth \ /usr/share/plymouth/themes/(NAME HERE)/(NAME HERE).plymouth 100`

Second to last, Run `sudo update-alternatives --config default.plymouth` and a list of multiple selections will appear, input the number corresponding to the theme you created.

.. image:: images/plymouth_select.png

Lastly, run `sudo update-initramfs -u` in order to load the new settings onto memory.

Whenever you reboot, It will enact your changes.


Standard Boot Screen
----------------------------------

First, Open the `Terminal` application and run the following:

`sudo update-alternatives --config default.plymouth`

.. image:: images/plymouth_select.png

You select one out from the number that a theme represents

Lastly, run `sudo update-initramfs -u` in order to load the new settings onto memory.

Whenever you reboot, It will enact your changes.




