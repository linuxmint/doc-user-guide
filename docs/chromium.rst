###############
Google Chromium
###############

Chromium is an open-source web browser developed by Google.

Google also develops a proprietary browser based on Chromium called Chrome. This is the browser Google promotes and provides repositories for. There are no Google repositories for Chromium.

This page lists the different ways to install Google Chromium in Linux Mint.


Default Linux Mint repositories
===============================

In LMDE, Linux Mint 18.x and Linux Mint 19.x you can install Chromium from the repositories:

.. code-block:: bash

    apt install chromium-browser

However, in Linux Mint 20.x, as announced in the `May 2020 Monthly News <https://blog.linuxmint.com/?p=3906>`_ , `chromium-browser` is a dummy package and Chromium is no longer available in the repositories.

Unofficial repositories and PPAs
================================

Unofficial repositories and PPAs provide easy access to packages and updates. As always, with unofficial sources, you need to trust the maintainer when it comes to software stability, security and frequency of updates.

Saikrishna Arcot's Chromium BETA PPA
------------------------------------

This `PPA <https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta>`_ contains the latest Chromium Beta builds, with hardware video decoding enabled (hidden behind a flag), and support for Widevine (needed for viewing many DRM-protected videos) enabled.

.. code-block:: bash

	apt remove --purge chromium-browser
	sudo add-apt-repository ppa:saiarcot895/chromium-beta
	apt update
	apt install chromium-browser

Saikrishna Arcot's Chromium DEV PPA
-----------------------------------

This `PPA <https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev>`_ contains the latest Chromium Dev builds, with hardware video decoding enabled (hidden behind a flag) and support for Widevine (needed for viewing paid videos on Netflix and Youtube) enabled.

.. code-block:: bash

	apt remove --purge chromium-browser
	sudo add-apt-repository ppa:saiarcot895/chromium-dev
	apt update
	apt install chromium-browser

Ungoogled Chromium
------------------

`Ungoogled Chromium <https://github.com/Eloston/ungoogled-chromium>`_ provides a version of Chromium which doesn't use Google Web services.

.. code-block:: bash

	echo 'deb http://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Focal/ /' | sudo tee /etc/apt/sources.list.d/home:ungoogled_chromium.list
	sudo wget -nv https://download.opensuse.org/repositories/home:ungoogled_chromium/Ubuntu_Focal/Release.key -O "/etc/apt/trusted.gpg.d/home:ungoogled_chromium.asc"
	apt update
	apt remove --purge chromium-browser
	apt install ungoogled-chromium

APT Pinning
===========

APT pinning consists in pointing to repositories which are not designed for Linux Mint 20 but with APT preferences which restrict the usage of these repositories to Chromium only and nothing else.

Debian Buster
-------------

As root, add the following to `/etc/apt/sources.list.d/debian-chromium.list`

.. code-block:: text

	deb https://deb.debian.org/debian buster main
	deb https://deb.debian.org/debian buster-updates main
	deb http://security.debian.org/ buster/updates main

And the following to `/etc/apt/preferences.d/debian-chromium.pref`

.. code-block:: text

	# Don't install anything other than chromium from the Debian repos
	Package: *
	Pin: origin "deb.debian.org"
	Pin-Priority: 1

	# Don't install anything other than chromium from the Debian repos
	Package: *
	Pin: origin "security.debian.org"
	Pin-Priority: 1

	# Pattern includes 'chromium'
	Package: chromium*
	Pin: origin "deb.debian.org"
	Pin-Priority: 700

	# Pattern includes 'chromium'
	Package: chromium*
	Pin: origin "security.debian.org"
	Pin-Priority: 700

	# Exclude the game chromium-bsu
	Package: chromium-bsu*
	Pin: origin "deb.debian.org"
	Pin-Priority: 1

	# Exclude the game chromium-bsu
	Package: chromium-bsu*
	Pin: origin "security.debian.org"
	Pin-Priority: 1

Then run the following commands:

.. code-block:: bash

	sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys DCC9EFBF77E11517
	sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys 648ACFD622F3D138
	sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys 112695A0E562B32A
	apt update
	apt remove --purge chromium-browser
	apt install chromium

Alternatives to Chromium
========================

Google Chrome
-------------

Google makes it very easy to install Chrome. Visit the `Google Chrome Website <https://www.google.com/chrome/>`_, download and install the provided package and it will automatically add the Google repositories to your operating system.

Firefox
-------

Firefox is the most popular open-source Web browser and also the default browser in Linux Mint. It's available in the repositories.

.. code-block:: bash

	apt install firefox

Alternatives to APT
===================

The Snap Store
--------------

Chromium is available from the Snap Store.

.. code-block:: bash

	apt install snapd
	sudo snap install chromium

.. note::

	The Snap Store is disabled in Linux Mint 20.x. For more information read :ref:`Snap Store <snapstore>`.