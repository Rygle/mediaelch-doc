=========================================================
Build MediaElch
=========================================================

MediaElch can be build using ``qmake``.
Using `QtCreator`_ is supported and advised.

*Supported platforms:*

.. contents::
   :local:
   :depth: 1


Linux
**********************************************************

Linux build instructions are available for:

 - Ubuntu 16.04 LTS and 18.04 LTS
 - openSUSE Leap 42.3

Ubuntu
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Dependencies
----------------------------------------------------------

.. code-block:: sh

    # [Only for 16.04] Modern GCC:
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get install g++-7 gcc-7
    sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 90
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 90

    # Build tools and other libraries
    sudo apt install build-essential git libcurl4-openssl-dev
    sudo apt install libmediainfo-dev
    # ffmpeg is required at runtime to create random screenshots
    sudo apt install ffmpeg

    # Qt (alternative: download and install Qt from its official website)
    sudo apt install qt5-default qtmultimedia5-dev qtdeclarative5-dev

Following packages are only required for Ubuntu 16.04 but not for 18.04.

.. code-block:: sh

    sudo apt install qtdeclarative5-controls-plugin qtdeclarative5-models-plugin

Build
----------------------------------------------------------

.. code-block:: sh

    git clone https://github.com/Komet/MediaElch.git && cd MediaElch
    mkdir build && cd $_
    qmake ..
    make -j4

Install
----------------------------------------------------------

Run following command after building MediaElch to install it on your system.

.. code-block:: sh

    sudo make install

openSUSE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Dependencies
----------------------------------------------------------
Follow the instructions on https://wiki.qt.io/Install_Qt_5_on_openSUSE |br|
Select the latest stable Qt version (e.g. 5.10.1) with "Desktop gcc 64-bit" enabled.

.. code-block:: sh

    # Install development tools
    sudo zypper install --type pattern devel_basis
    # Install other dependencies
    sudo zypper install libmediainfo0 libmediainfo-devel libpulse-devel
    # Install a newer version of GCC (Leap 42.3 uses GCC 4.8.5)
    sudo zypper install gcc7 gcc7-c++

Note that MediaElch needs ffmpeg to create screenshots.
ffmpeg itself requires multimedia codecs. Please refer to
http://opensuse-guide.org/codecs.php to learn how to install them.
Then install ffmpeg.

.. code-block:: sh

    sudo zypper install ffmpeg

To be able to build MediaElch using the command line, don't forget to
add the ``bin`` directory of the previously installed Qt version to
your ``$PATH``. For example add following to your ``~/.bashrc``:

.. code-block:: sh

    export PATH=$PATH:$HOME/Qt/5.10.1/gcc_64/bin

Build
----------------------------------------------------------
.. code-block:: sh

    git clone https://github.com/Komet/MediaElch.git && cd MediaElch
    mkdir build && cd $_
    qmake ..
    make -j4

Install
----------------------------------------------------------
Run following command after building MediaElch to install it on your system.

.. code-block:: sh

    sudo make install

Mac
**********************************************************

Install XCode (e.g. through the `Mac App Store <https://itunes.apple.com/de/app/xcode/id497799835>`_)
and `Homebrew <https://brew.sh/>`_. Instead of XCode you can also just install the
`XCode Command Line Tools <https://developer.apple.com/library/content/technotes/tn2339/_index.html#//apple_ref/doc/uid/DTS40014588-CH1-WHAT_IS_THE_COMMAND_LINE_TOOLS_PACKAGE_>`_
(open a Terminal and execute ``xcode-select --install``).


Command Line Build
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: sh

    # [Optional] Install git (it should have already been installed by XCode)
    brew install git

    # Install tools and dependencies
    brew install subversion qt media-info ffmpeg

    # Clone MediaElch
    git clone https://github.com/Komet/MediaElch.git && cd MediaElch

    # Download necessary headers
    svn checkout https://github.com/MediaArea/MediaInfoLib/trunk/Source/MediaInfoDLL
    svn checkout https://github.com/MediaArea/ZenLib/trunk/Source/ZenLib

    # Build MediaElch
    mkdir build && cd $_
    qmake ..
    make -j4


QtCreator Build
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Download the [Qt online installer][qt]. Run it and select the latest Qt
version for installation (e.g. ``Qt 5.10.1``).
Check that following components are selected:

 - macOS
 - QtCreator

Download the `MediaElch source code <https://github.com/Komet/MediaElch>`_
by clicking "Download" or using git: |br|
``git clone https://github.com/Komet/MediaElch.git``.

You have to download `ffmpeg for Windows <https://evermeet.cx/ffmpeg/>`_ to be able
to create random screenshots of video files. After building MediaElch, place ``ffmpeg``
inside ``MediaElch.app/Contents/MacOS``.

Other Libraries
----------------------------------------------------------
 1. Install MediaInfo as it is required for MediaElch to get stream details. |br|
    Install it using Homebrew: ``brew install media-info``
 2. Download `MediaInfoLib <https://github.com/MediaArea/MediaInfoLib>`_. |br|
    Copy the folder ``Source/MediaInfoDLL`` to ``path/to/MediaElch/MediaInfoDLL``
 3. Download `ZenLib <https://github.com/MediaArea/ZenLib>`_.
    Copy the folder ``Source/ZenLib`` to ``path/to/MediaElch/ZenLib``

Build
----------------------------------------------------------
Start QtCreator and open ``/path/to/MediaElch/MediaElch.pro``. |br|
Configure it as "Release" and click "Run" (``Strg+R``).

Windows
**********************************************************

Dependencies
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Qt
----------------------------------------------------------
Download the `Qt online installer`_. Run it and select the latest Qt version
for installation (e.g. ``Qt 5.10.1``). Select "MinGW 5.3.0" in section ``Tools``.

Other Libraries
----------------------------------------------------------
 1. Download precompiled `MediaInfo <https://mediaarea.net/de/MediaInfo/Download/Windows>`_ (DLL)
 2. Download `MediaInfoLib <https://github.com/MediaArea/MediaInfoLib>`_. |br|
    Copy the folder ``Source/MediaInfoDLL`` to ``path/to/MediaElch/MediaInfoDLL``
 3. Download `ZenLib <https://github.com/MediaArea/ZenLib>`_. |br|
    Copy the folder ``Source/ZenLib`` to ``path/to/MediaElch/ZenLib``

Build
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Open the MediaElch project using QtCreator, configure it and click "Run" (``Strg+R``).

ffmpeg
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
You have to download `ffmpeg <https://ffmpeg.zeranoe.com/builds/>`_ to be able
to create random screenshots of video files. After building MediaElch place
``ffmpeg`` inside a new folder ``vendor`` which must be placed in the same
directory as ``MediaElch.exe``.

.. _Qt online installer:
.. _QtCreator: https://www.qt.io/download

.. |br| raw:: html

   <br />
