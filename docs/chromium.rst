########
Chromium
########

Chromium is an open-source web browser developed by Google.

Google also develops a proprietary browser based on Chromium called Chrome. This is the browser Google promotes and provides repositories for. There are no Google repositories for Chromium.

This page lists the different ways to install Chromium in Linux Mint.

.. _extensions: http://www.sphinx-doc.org/en/master/ext/builtins.html#builtin-sphinx-extensions

Default Linux Mint repositories
===============================

In LMDE, Linux Mint 18.x and Linux Mint 19.x you can install Chromium from the repositories:

.. code-block:: bash

    apt install chromium-browser

However, in Linux Mint 20.x, as announced in the `May 2020 Monthly News <https://blog.linuxmint.com/?p=3906>`_ , `chromium-browser` is a dummy package and Chromium is no longer available in the repositories.

Unofficial repositories and PPAs
================================

Unofficial repositories and PPAs provide easy access to packages and updates. As always, with unofficial sources, you need to trust the maintainer when it comes to software stability, security and frequency of updates.

.. hint::

	Create a Timeshift system snapshot before adding any unofficial software sources or installing software from third parties. This will allow you to revert any potential mistakes or undesired consequences.

.. warning::

	Do not use PPAs or third party sources unless you trust its maintainer.

Saikrishna Arcot's Chromium BETA PPA
------------------------------------

This `BETA PPA <https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta>`_ contains the latest Chromium Beta builds, with hardware video decoding enabled (hidden behind a flag), and support for Widevine (needed for viewing many DRM-protected videos) enabled.

As root, add the following to `/etc/apt/preferences.d/saiarcot895-chromium-beta.pref`

.. code-block:: text

	# Ensure packages from saiarcot895-chromium-beta PPA have priority
	Package: *
	Pin: release o=LP-PPA-saiarcot895-chromium-beta
	Pin-Priority: 800

Then in a terminal window run

.. code-block:: bash

	apt remove --purge chromium-browser
	sudo add-apt-repository ppa:saiarcot895/chromium-beta
	apt update
	apt install chromium-browser

Saikrishna Arcot's Chromium DEV PPA
-----------------------------------

This `Dev PPA <https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev>`_ contains the latest Chromium Dev builds, with hardware video decoding enabled (hidden behind a flag) and support for Widevine (needed for viewing paid videos on Netflix and Youtube) enabled.

As root, add the following to `/etc/apt/preferences.d/saiarcot895-chromium-dev.pref`

.. code-block:: text

	# Ensure packages from saiarcot895-chromium-dev PPA have priority
	Package: *
	Pin: release o=LP-PPA-saiarcot895-chromium-dev
	Pin-Priority: 800

Then in a terminal window run

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
	wget -nv https://download.opensuse.org/repositories/home:ungoogled_chromium/Ubuntu_Focal/Release.key -O - | sudo apt-key add -
	apt update
	apt remove --purge chromium-browser
	apt install ungoogled-chromium

APT Pinning
===========

APT pinning consists in pointing to repositories which are not designed for Linux Mint 20 but with APT preferences which restrict the usage of these repositories to Chromium only and nothing else.

Debian Buster
-------------

As root, add the following to `/etc/apt/sources.list.d/pinned-debian-chromium.list`

.. code-block:: text

	deb https://deb.debian.org/debian buster main
	deb https://deb.debian.org/debian buster-updates main
	deb http://security.debian.org/ buster/updates main

And the following to `/etc/apt/preferences.d/pinned-debian-chromium.pref`

.. code-block:: text

	# Don't install anything other than chromium from the Debian repos
	Package: *
	Pin: origin "deb.debian.org"
	Pin-Priority: -10

	# Don't install anything other than chromium from the Debian repos
	Package: *
	Pin: origin "security.debian.org"
	Pin-Priority: -10

	# Exclude the game chromium-bsu
	Package: chromium-bsu*
	Pin: origin "deb.debian.org"
	Pin-Priority: -10

	# Exclude the game chromium-bsu
	Package: chromium-bsu*
	Pin: origin "security.debian.org"
	Pin-Priority: -10

	# Pattern includes 'chromium'
	Package: chromium*
	Pin: origin "deb.debian.org"
	Pin-Priority: 700

	# Pattern includes 'chromium'
	Package: chromium*
	Pin: origin "security.debian.org"
	Pin-Priority: 700

	# Chromium dependencies only in buster
	Package: /libevent-2.1-6/ /libicu63/ /libjpeg62-turbo/ /libvpx5/
	Pin: origin "deb.debian.org"
	Pin-Priority: 1

	# Chromium dependencies only in buster
	Package: /libevent-2.1-6/ /libicu63/ /libjpeg62-turbo/ /libvpx5/
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

Vivaldi
-------

Vivaldi is a new browser that protects you from trackers, blocks unwanted ads and gives you full control with its native features. Install Vivaldi and surf efficiently. Visit the `Vivaldi Website <https://vivaldi.com/>`_, download and install the provided package and it will automatically add the Vivaldi repositories to your operating system.

Google Chrome
-------------

Google makes it very easy to install Chrome. Visit the `Google Chrome Website <https://www.google.com/chrome/>`_, download and install the provided package and it will automatically add the Google repositories to your operating system.

.. warning::

	Only use this browser if you trust `Google <https://google.com>`_ with your privacy and data. Chrome is proprietary software. It cannot be audited or modified.

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

.. warning::

	Only use this store if you trust both `Canonical <https://canonical.com>`_ and the maintainers of the snaps you install. Similar to proprietary software, software delivered by and code run by the Snap Store cannot be audited or modified. This store is disabled in Linux Mint 20.x. For more information read :ref:`Snap Store <snapstore>`.
