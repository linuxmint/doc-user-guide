##########
Snap Store
##########

.. _snapstore:

The `Snap Store <https://snapcraft.io/>`_, also known as the `Ubuntu Store`, is a commercial centralized software store operated by `Canonical <https://canonical.com/>`_.

Similar to AppImage or Flatpak the Snap Store is able to provide up to date software no matter what version of Linux you are running and how old your libraries are.

Criticism
=========

Centralized control
-------------------

Anyone can create APT repositories and distribute software freely. Users can point to multiple repositories and define priorities. Thanks to the way APT works, if a bug isn't fixed upstream, Debian can fix it with a patch. If Debian doesn't, Ubuntu can. If Ubuntu doesn't Linux Mint can. If Linux Mint doesn't, anyone can, and not only can they fix it, they can distribute it with a PPA.

Flatpak isn't as flexible. Still, anyone can distribute their own Flatpaks. If Flathub decides they don't want to do this or that, anyone else can create another Flatpak repository. Flatpak itself can point to multiple sources and doesn't depend on Flathub.

Although it is open-source, Snap on the other hand, only works with the Ubuntu Store. Nobody knows how to make a Snap Store and nobody can. The Snap client is designed to work with only one source, following a protocol which isn't open, and using only one authentication system. Snapd is nothing on its own, it can only work with the Ubuntu Store.

This is a store we can't audit, which contains software nobody can patch. If we can't fix or modify software, open-source or not, it provides the same limitations as proprietary software.

Backdoor via APT
----------------

When Snap was introduced Canonical promised it would never replace APT. This promise was broken. Some APT packages in the Ubuntu repositories not only install snap as a dependency but also run snap commands as root without your knowledge or consent and connect your computer to the remote proprietary store operated by Canonical.


Disabled Snap Store in Linux Mint 20
====================================

Following the decision made by Canonical to replace parts of APT with Snap and have the Ubuntu Store install itself without users knowledge or consent, the Snap Store is forbidden to be installed by APT in Linux Mint 20.

.. note::

	For more information read the announcements made in `May 2020 <https://blog.linuxmint.com/?p=3906>`_ and `June 2019 <https://blog.linuxmint.com/?p=3766>`_.

How to install the Snap Store in Linux Mint 20
==============================================

Recommended or not, if you want to use the Snap Store, re-enabling and installing it is very easy.

.. code-block:: bash

	sudo rm /etc/apt/preferences.d/nosnap.pref
	apt update
	apt install snapd

