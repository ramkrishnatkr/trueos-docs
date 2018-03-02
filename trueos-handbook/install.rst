.. index:: install
.. _Install:

Install
*******

This chapter describes how to use the graphical installer to install a
graphical desktop directly onto a hard drive or into a virtual machine
using virtualization software such as
`VirtualBox <https://www.virtualbox.org/>`_.

.. index:: Download and Prepare to Install
.. _Download and Prepare to Install:

Download and Prepare to Install
===============================

|trueos| uses a rolling release model rather than versioned releases.
There are two primary options of |trueos| install: STABLE and UNSTABLE:

1. STABLE is synchronized with FreeBSD. This means users see less
   experimental work and generally have a smoother experience. However,
   users on STABLE typically wait longer for bugfixes and patches
   to be available. While some |trueos| development may be backported to
   STABLE early, FreeBSD patches and port synchronization is done on a
   six-month schedule.

2. UNSTABLE is the full leading edge of TrueOS and FreeBSD development.
   Patches are very frequent, but can incorporate experimental work from
   |trueos|, FreeBSD, and other Open Source projects and contributions.
   UNSTABLE is recommended for users who need the absolute latest work
   from FreeBSD or |trueos| and are willing to tolerate breakage or less
   system stability. It is also recommended for users who want to test
   and contribute patches to FreeBSD or |trueos|.

Periodically, the |sysadm| :sysclbk:`Update Manager <update-manager>`
provides patches to update the operating system. By default, users who
install STABLE receive updates from the STABLE track, and UNSTABLE users
follow the UNSTABLE track. It is possible to switch update tracks
post-installation. See the :ref:`Updating TrueOS` section for
instructions on switching update repositories.

Installation files can be downloaded from the
`TrueOS® website <https://www.trueos.org/downloads/>`_.

:numref:`Figure %s <downloadscreen1>` below shows the |trueos| website,
and how to download a STABLE or UNSTABLE version of |trueos|. It also
shows a drop down menu containing the different types of install files
available for download.

.. _downloadscreen1:

.. figure:: images/downloadscreen1.png
   :scale: 100%

   UNSTABLE or STABLE Download Screen

To install a graphical desktop, download the |trueos| Desktop option.
Then, depending on the file chosen, either burn it to a DVD media
or write it to a removable USB device.

If installing a command-line only server is preferred, download and
begin installing the |trueos| Server option.

Install files can end with a variety of extensions:

* **.iso**: If the file has an *.iso* extension, it should be burned to
  a DVD media.
* **.img**: If it has a *img* extension, it should be burned to a USB
  stick.
* **.md5, .sha256, and .sig**: Depending upon the current operating
  system and its tools, use the value in any of these files to
  determine the integrity of the download, as described in
  :ref:`Data Integrity Check`.
* **.torrent**: If a torrent is available, a file with the same name
  and a *.torrent* extension will be visible.

Refer to :ref:`Burning the Installation Media` for instructions on how
to burn the downloaded file to bootable media.

.. index:: data integrity check
.. _Data Integrity Check:

Data Integrity Check
--------------------

After downloading the desired file, it is a good idea to check the file
is exactly the same as the one on the |trueos| download server. While
downloading, a portion of the file may get damaged or lost, making the
installation file unusable. Each |trueos| installation file has an
associated *MD5* and *SHA256* checksum. If a checksum of the downloaded
file matches, the download was successful. If a checksum does not match,
try downloading the file again. In order to verify a checksum, use a
checksum verification utility.

.. note:: Only one of the checksums needs to be verified. The
   `TrueOS website <https://www.trueos.org/downloads/>`_ lists
   *.MD5*, *SHA256*, and *.SIG* files. The
   `TrueOS website <https://www.trueos.org/downloads/>`_ has all
   file types.

If using a Windows system, download and install a utility such as
`Raymond's MD5 & SHA Checksum Utility <http://download.cnet.com/MD5-SHA-Checksum-Utility/3000-2092_4-10911445.html>`_.
This utility can be used to simultaneously check the *MD5*, *SHA-1*,
*SHA-256*, and *SHA-512* checksums of any file. Once installed, launch
the program and use :guilabel:`Browse`, shown in
:numref:`Figure %s <fastsum1>`, to browse to the location of the
downloaded file.

.. _fastsum1:

.. figure:: images/checksum.png
   :scale: 100%

   Checksum Verification

Once the file is selected, click :guilabel:`Open` to calculate the
checksums. It may take a minute or so, depending upon the size of the
downloaded file.

On Linux and BSD systems, use the built-in :command:`md5` or
:command:`md5sum` command line tool to display the MD5 checksum. In this
example, the user types :command:`md5` to view the sum of a :file:`.img`
file located in the :file:`Downloads` directory. Then, using the
built-in :command:`cat` command line tool, the user compares the sum to
the contents of the related :file:`.md5` file:

.. code-block:: none

 ~% md5 Downloads/TrueOS-2017-04-21-x64-USB.img
 MD5 (Downloads/TrueOS-2017-04-21-x64-USB.img) =
 3eb6adef0ad171f6c5825f0f820557f5

 ~& cat Downloads/TrueOS-2017-04-21-x64-USB.img.md5
 3eb6adef0ad171f6c5825f0f820557f5

To use the *OpenPGP* :file:`.sig` file, use your preferred utility to
verify the signature. The `OpenPGP website <https://openpgp.org/>`_ has
numerous recommendations for verification utilities.

.. index:: burn installation media
.. _Burning the Installation Media:

Burning the Installation Media
------------------------------

Once the installation file is downloaded and its checksum verified, burn
it to a media. The media you use depends upon the file downloaded:

* Files ending with :file:`.iso` can be burned to a DVD or used in a
  Virtual Machine (VM).

* Files ending in :file:`img` must be burned to a USB stick.

To burn to a DVD, use either a burning utility packaged with the
operating system on the system with the burner or a separate burning
application. :numref:`Table %s <burn utils>` lists some freely available
burning utilities.

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.65\linewidth-2\tabcolsep}|

.. _burn utils:

.. table:: Free Burning Utilities
   :class: longtable

   +-----------------------+---------------------------------------------------------------------------------------------------+
   | Operating System      | Utility                                                                                           |
   +=======================+===================================================================================================+
   | Windows               | `InfraRecorder utility <http://infrarecorder.org/>`_                                              |
   +-----------------------+---------------------------------------------------------------------------------------------------+
   | Windows               | `Disk Burner <https://support.microsoft.com/en-us/help/15088/windows-create-installation-media>`_ |
   +-----------------------+---------------------------------------------------------------------------------------------------+
   | Linux or \*BSD        | `K3B <https://www.kde.org/applications/multimedia/k3b/>`_                                         |
   +-----------------------+---------------------------------------------------------------------------------------------------+
   | Linux or \*BSD        | `Brasero <https://wiki.gnome.org/Apps/Brasero>`_                                                  |
   +-----------------------+---------------------------------------------------------------------------------------------------+
   | FreeBSD/PC-BSD/TrueOS | `growisofs <https://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/creating-dvds.html>`_      |
   +-----------------------+---------------------------------------------------------------------------------------------------+
   | Mac OS X              | `Disk Utility <https://support.apple.com/kb/PH20577?locale=en_US>`_                               |
   +-----------------------+---------------------------------------------------------------------------------------------------+

.. index:: writing to usb
.. _Writing to a USB Device:

Writing to a USB Device
-----------------------

There are a few requirements to write the :file:`img` file to a USB
device:

* A utility capable of writing the image to a USB media; the available
  utilities depend on the installed operating system.

* A USB thumb drive or hard drive large enough to hold the image.

.. warning:: If there is a card reader on the system or the USB drive is
   connected using a USB dongle, device enumeration may be affected. For
   example, with the USB card reader dongle as the destination, the
   device name could be :file:`/dev/da1` instead of :file:`/dev/da0`.

To write the :file:`.img` file to a flash card or removable USB drive on
a BSD or Linux system, use the :command:`dd` command line utility. On a
FreeBSD system, the superuser can use this command to write the file to
the first plugged in USB device:

.. code-block:: none

 [user@exmpl] dd if=TrueOS-Desktop-2016-08-11-x64.img of=/dev/da0 bs=1m
 1415+1 records in
 1415+1 records out
 1483990016 bytes transferred in 238.552250 secs (6220818 bytes/sec)

When using the :command:`dd` command:

* **if=** designates the *input file* to be written.

* **of=** refers to the *output file* (the device name of the flash card
  or removable USB drive). Increment the number in the name if it is not
  the first USB device.

* **bs=** refers to the *block size*.

.. note:: On Linux, type :command:`mount` with the USB stick inserted to
   see two or more device nodes corresponding to the USB stick. For
   example, :file:`/dev/sdc` and :file:`/dev/sdc1`, where
   :file:`/dev/sdc1` corresponds to the primary partition of the USB
   stick. Before using :command:`dd`, ensure the USB stick is unmounted.
   Then, remember to use :file:`/dev/sdc` (the device node without the
   number) as the option for the output file **of=**. Once :command:`dd`
   completes, the USB stick may not be mountable on Linux as it has very
   limited support for UFS (BSD filesystem created on the USB stick).

To burn the image file on a Windows system, use
`win32-image-writer <https://sourceforge.net/projects/win32diskimager/>`_.
When downloading **win32-image-writer**, download the latest version
ending in :file:`-binary.zip` and use a utility such as Windows Explorer
or 7zip to unzip the executable.

Launch :command:`win32-image-writer.exe` to start the Win32 Disk Imager
utility, shown in :numref:`Figure %s <writer1>`. Use :guilabel:`browse`
to browse to the location of the :file:`.img` file. Insert a USB thumb
drive and select its drive letter (in this example, drive **D**). Click
:guilabel:`Write` and the image will be written to the USB thumb drive.

.. _writer1:

.. figure:: images/writer1.png
   :scale: 100%

   Write an Image using Win32 Disk Imager

To burn the :file:`.img` file on Mac OS X, insert a USB stick and open
*Terminal*. Run :command:`diskutil list` to discover the device name of
the USB disk, unmount the USB disk, then use :command:`dd` to write the
image to the raw disk (:file:`rdisk`). In this example, an 8 GB USB
stick has a device name of :file:`/dev/disk1` and a raw device name of
:file:`/dev/rdisk1`:

.. code-block:: none

 diskutil list
 /dev/disk0
 #: TYPE NAME SIZE IDENTIFIER
 0: GUID_partition_scheme *500.1 GB disk0
 1: EFI 209.7 MB disk0s1
 2: Apple_HFS Macintosh HD 499.2 GB disk0s2
 3: Apple_Boot Recovery HD 650.0 MB disk0s3
 /dev/disk1
 #: TYPE NAME SIZE IDENTIFIER
 0: FDisk_partition_scheme *8.0 GB disk1
 1: DOS_FAT_32 UNTITLED 8.0 GB disk1s1

 diskutil unmountDisk /dev/disk1
 Unmount of all volumes on disk1 was successful

 sudo dd if=/Users/dru/Downloads/TrueOS-Desktop-2016-08-11-x64.img of=/dev/rdisk1 bs=4m
 Password:
 1415+1 records in
 1415+1 records out
 1483990016 bytes transferred in 238.552250 secs (6220818 bytes/sec)

.. index:: TrueOS installation
.. _TrueOS Installation:

|trueos| Installation
=====================

To begin the |trueos| installation, insert the prepared boot media and
boot the system. If the computer boots into an existing operating
system instead of the installer, reboot and check the computer's BIOS
program to ensure the drive containing the installation media is listed
first in the boot order. Save any BIOS changes and reboot.

Once the system boots it displays the menu shown in
:numref:`Figure %s <install1>`. Press :kbd:`Enter` or simply wait a few
moments and this menu automatically prompts the system to continue
booting.

.. _install1:

.. figure:: images/install1b.png
   :scale: 100%

   Initial Boot Menu

.. note:: See :ref:`BSD Boot Loader` for a detailed description of this
   menu.

If a key other than :kbd:`Enter` is pressed, this screen pauses
to provide additional time to review the options. If this screen is not
paused, it automatically boots into the :guilabel:`Boot Multi User`
option, displaying the first graphical installer screen, shown in the
:ref:`Language` install section.

The rest of this chapter describes the screens of the graphical
installer. If any problems arise with booting into the graphical
installer, please refer to the
:ref:`Installation Troubleshooting <Installation Help>` section of
this handbook.

.. index:: installer language selection
.. _Language:

Language
========

The first graphical installer screen, seen in
:numref:`Figure %s <install2>`, indicates the installer successfully
loaded and is ready to present its options.

.. _install2:

.. figure:: images/install2e.png
   :scale: 100%

   Welcome and Language Selection Screen

On the bottom-left side of the screen are several icons and buttons to
help with the installation, explained in :numref:`Table %s <insico>`:

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.65\linewidth-2\tabcolsep}|

.. _insico:

.. table:: Installer icons
   :class: longtable

   +-----------------------+-------------------------------------------+
   | Icon                  | Function                                  |
   +=======================+===========================================+
   | System with wrench    | Access hardware compatibility information |
   |                       | to quickly determine if the system's      |
   |                       | video card, Ethernet card, wireless       |
   |                       | device, and sound card are compatible     |
   |                       | with |trueos|.                            |
   +-----------------------+-------------------------------------------+
   | Light Bulb            | Read a screen's Help text.                |
   +-----------------------+-------------------------------------------+
   | Keyboard              | Use the onscreen keyboard.                |
   +-----------------------+-------------------------------------------+
   | "L" key and U.S. Flag | Switch between the US keyboard layout and |
   |                       | a user selected layout.                   |
   +-----------------------+-------------------------------------------+
   | Blue and White Orb    | Opens the *Network Manager* in order to   |
   |                       | configure system networking during the    |
   |                       | installation process.                     |
   +-----------------------+-------------------------------------------+
   | Command Prompt Window | Access the emergency shell described in   |
   |                       | :ref:`Using the System Utilities Menu`.   |
   +-----------------------+-------------------------------------------+
   | Abort                 | Cancel the installation.                  |
   +-----------------------+-------------------------------------------+
   | Next                  | Navigate to the next or previous screen.  |
   +-----------------------+-------------------------------------------+

Hover over an icon to view its description in the tip bar at the
bottom of the screen.

.. note:: The default keyboard layout can be changed at this point,
   during the post-installation :ref:`Choose a Language` screen, when
   :ref:`Logging In`, or during an active session using the included
   :command:`fcitx` utility.

There is also an option to :guilabel:`Load config from USB`. If the
configuration from a previous installation has been saved, it can be
loaded at this time from a *FAT* formatted USB stick.

By default, |trueos| menus display in English, unless another language
is selected in the drop-down menu in this screen. The menus in |trueos|
are being continuously translated to other languages. To view the
availability of a specific language, navigate to the
`TrueOS® Translation Site <https://weblate.trueos.org>`_. A language may
show less than 100% translation, indicating not all of the menus are
translated. Any untranslated menus are displayed in English. Refer to
:ref:`Become a Translator` to assist in translating the graphical menus.

.. note:: Small screens may not display the entire installer window,
   resulting in buttons at the bottom of the window being hidden and
   inaccessible. In this situation, either press :kbd:`Alt` while
   dragging the window with the mouse or press :kbd:`Alt+N` to select
   the next button of the window.

When finished reviewing this screen, click :guilabel:`Next` to move on
to the next installation screen.

.. index:: installer system select
.. _System Selection:

System Selection
================

The **System Selection** screen installs a graphical desktop or
a console-based server operating system, as seen in
:numref:`Figure %s <install3>`. It also can be used for
:ref:`Restoring the Operating System`. This chapter concentrates on a
desktop installation. Refer to the :ref:`Server Installation`
instructions for installing a command-line only server.

.. _install3:

.. figure:: images/install3e.png
   :scale: 100%

   System Selection Screen

By default, :guilabel:`TrueOS Desktop (graphical interface)` is
selected. The |lumina| Desktop is installed with TrueOS, but
additional software can be installed later using
:sysclbk:`AppCafe <appcafe>`.

To install the desktop, click :guilabel:`Next`.

.. note:: When installing to an existing |pcbsd| or |trueos| system, a
   pop-up window asks to install to the existing pool without
   reformatting it. Press :guilabel:`OK` to keep the existing pool.
   Clicking :guilabel:`Cancel` formats the existing pool and all of
   its data. Refer to the :ref:`Upgrading from PCBSD 10.x to TrueOS`
   section for more information about this option.

.. index:: Optional Installation Packages
.. _Optional Packages:

Optional Packages
=================

By default, |trueos| loads only two graphics drivers during the
installation: VESA (for MBR) and SCFB (for UEFI). |trueos| provides
the option to further choose your graphics driver as part of the
:numref:`Figure %s <install16>` screen.

.. _install16:

.. figure:: images/install16.png
   :scale: 100%

   Optional Installation Packages

When installing |trueos|, it detects the onboard graphics solution and
displays a list of drivers you can use for |trueos|. Additionally,
VirtualBox is automatically detected, populating the list with
*Virtual Environment Drivers*.

Expand the desired list of drivers and choose one which is compatible
with your hardware, then click :guilabel:`Next` to continue.

.. index:: installer disk config screen
.. _Disk Selection:

Disk Selection
==============

The **Disk Selection** screen, seen in :numref:`Figure %s <install5>`,
summarizes the default disk configuration.

.. _install5:

.. figure:: images/install5d.png
   :scale: 100%

   Disk Selection Screen

.. warning:: By default, |trueos| assumes the user wants to install
   on the entire first disk. When installing |trueos| as the only
   operating system on the computer, click :guilabel:`Next` to start the
   installation. However, if this is not intended, review the rest
   of this section to determine how to layout the disk. If |trueos| is
   to be booted with another operating system, please review the section
   on :ref:`Dual Booting`.

To select the disk or partition to install |trueos|, click
:guilabel:`Customize Disk Settings` to start the |trueos| Disk Wizard,
shown in :numref:`Figure %s <install6>`.

.. _install6:

.. figure:: images/install6c.png
   :scale: 100%

   |trueos| Disk Wizard

The wizard provides two modes of operation:

* **Basic:** (default) Select this mode if to specify the installation
  partition or disk.

* **Advanced:** Select this mode to specify the installation partition
  or disk, use MBR partitioning, change the default ZFS pool name, force
  the block size used by ZFS, configure a multi-disk installation, add a
  log or cache device, encrypt the disk, or specify the filesystem
  layout.

.. warning:: Regardless of the selected mode, once the disk wizard
   completes and :guilabel:`Next` is chosen at the **Disk Selection**
   screen, a pop-up window asks to start the installation. Be sure to
   review the **Summary** area before clicking :guilabel:`Yes` and
   starting the installation. The **Disk Selection** screen is the
   **very last chance** to ensure the system is correctly configured.
   After clicking :guilabel:`Yes`, the selected hard drive or
   partition is formatted, losing any existing data.

Once finished configuring the disk, you can save your choices for
later use. Insert a FAT32 or MSDOSFS formatted USB stick and click
:guilabel:`Save Config to USB`.

.. index:: basic disk customization
.. _Basic Mode:

Basic Mode
----------

Select :guilabel:`Basic` and the wizard displays the screen shown
in :numref:`Figure %s <install7>`.

.. _install7:

.. figure:: images/install7c.png
   :scale: 100%

   Disk or Partition Selection

The first hard disk is typically selected. To install on a different
disk, use the :guilabel:`Disk` drop-down menu to select the install
disk.

By default, the entirety of the selected disk is formatted. If the disk
is divided into partitions or there is an area of free space, use the
:guilabel:`Partition` drop-down menu to choose the desired partition.

.. note:: |trueos| only installs into a primary MBR partition, a GPT
   partition, or an area of free space. |trueos| cannot install into
   a secondary or an extended partition. To create an area of free
   space for installation, refer to :ref:`Creating Free Space`.

For EFI/UEFI systems, you can choose to :guilabel:`Install rEFInd`.
The `rEFInd boot manager <http://www.rodsbooks.com/refind/>`_ is
used to provide a menu of boot options to the user when the computer
boots. It is required by |trueos| when :ref:`Dual Booting`.

.. note:: rEFInd is a boot manager which functions separately from the
   FreeBSD bootloader.

Once the disk and partition are selected, click :guilabel:`Next` to
view a **Summary** screen to review your choices. To make additional
changes, press :guilabel:`Back` to return to a previous screen.
Otherwise, click :guilabel:`Finish` to leave the wizard. Click
:guilabel:`Next` then :guilabel:`Yes` to start the installation.

.. index:: advanced disk customization
.. _Advanced Mode:

Advanced Mode
-------------

After selecting advanced mode, the wizard displays the screen shown in
:numref:`Figure %s <install8>`.

.. _install8:

.. figure:: images/install8d.png
   :scale: 100%

   Advanced Mode Options

This screen has several options:

* **Disk:** Choose the install disk.

* **Partition:** Select the desired partition or area of free space.

.. note:: |trueos| onlys install into a primary MBR partition, a GPT
   partition, or an area of free space. |trueos| cannot install into
   a secondary or an extended partition. To create an area of free
   space for installation, refer to :ref:`Creating Free Space`.

* **Partition Scheme:**  The default
  :guilabel:`GPT (Best for new hardware)` is a partition table layout
  supporting larger partition sizes than the traditional
  :guilabel:`MBR (Legacy)` layout. **If the installation disk or
  partition is larger than 2 TB, the GPT option must be selected**.
  Since some older motherboards do not support GPT, if the installation
  fails, try again with :guilabel:`MBR (Legacy)` selected. When in
  doubt, use the default selection.

.. note:: The **Partition Scheme** section does not appear if a
   partition other than :guilabel:`Use entire disk` is chosen in the
   :guilabel:`Partition` drop-down menu.

* **ZFS pool name:** To use a pool name other than *tank* (default),
  check this box and type the name of the pool in the text window.
  *Root* is reserved and can not be used as a pool name.

* **Force ZFS 4k block size:** This option is only used if the disk
  supports 4k, even though the disk may lie and report its size as
  512b. Use with caution as it may cause the installation to fail.

* **Install rEFInd:** For EFI/UEFI systems, you can choose to
  :guilabel:`Install rEFInd`. The
  `rEFInd boot manager <http://www.rodsbooks.com/refind/>`_ is used to
  provide a menu of boot options to the user when the computer boots. It
  is required by |trueos| when :ref:`Dual Booting`.

After making any selections, click :guilabel:`Next` to access the ZFS
configuration screens. The rest of this section provides a ZFS overview
and then demonstrates how to customize the ZFS layout.

.. index:: ZFS layout
.. _ZFS Layout:

ZFS Layout
^^^^^^^^^^

In :guilabel:`Advanced Mode`, the disk setup wizard allows configuring
the ZFS layout. The initial ZFS configuration screen is seen in
:numref:`Figure %s <install9>`.

.. _install9:

.. figure:: images/install9c.png
   :scale: 100%

   ZFS Configuration

If the system contains multiple drives to be used to create a ZFS mirror
or RAIDZ*, check :guilabel:`Add additional disks to storage pool`, which
enables this screen. Any available disks are listed in the box below the
:guilabel:`ZFS Virtual Device Mode` drop-down menu. Select the desired
level of redundancy from the :guilabel:`ZFS Virtual Device Mode`
drop-down menu, then check the box for each disk to add to the
configuration.

.. note:: The |trueos| installer requires entire disks (not partitions)
   when adding more disks to the pool.

While ZFS allows using disks of different sizes, this is discouraged as
it decreases storage capacity and ZFS performance.

The |trueos| installer supports multiple ZFS configurations:

* **mirror:** Requires a minimum of 2 disks.

* **RAIDZ1:** Requires a minimum of 3 disks. For best performance,
  a maximum of 9 disks is recommended.

* **RAIDZ2:** Requires a minimum of 4 disks. For best performance, a
  maximum of 10 disks is recommended.

* **RAIDZ3:** Requires a minimum of 5 disks. For best performance, a
  maximum of 11 disks is recommended.

* **stripe:** Requires a minimum of 2 disks.

.. danger:: A stripe does NOT provide ANY redundancy. If any disk fails
   in a stripe, all data in the pool is lost!

The installer does not allow a configuration choice in which the system
does not meet the required number of disks. When selecting a
configuration, a message indicates how many more disks are required.

When finished, click :guilabel:`Next` to choose cache and log devices,
shown in :numref:`Figure %s <install10>`.

.. _install10:

.. figure:: images/install10b.png
   :scale: 100%

   L2ARC and ZIL

This screen can be used to specify an SSD as an L2ARC read cache or as a
secondary log device (ZIL). Any available devices are listed in the
boxes in this screen.

.. note:: A separate SSD is needed for each type of device.

Refer to the descriptions for ZIL and L2ARC in the :ref:`ZFS Overview`
to determine if the system would benefit from any of these devices
before adding them in this screen. When finished, click :guilabel:`Next`
to move to the encryption options, shown in
:numref:`Figure %s <install11>`.

.. _install11:

.. figure:: images/install11d.png
   :scale: 100%

   Encryption

This screen can be used to configure full-disk encryption. This is
meant to protect the data on the disks should the system itself be
lost or stolen. This type of encryption prevents the data on the disks
from being available during bootup unless the correct passphrase is
typed at the bootup screen. Once the passphrase is accepted, the data
is unencrypted and can easily be read from disk.

To configure full-disk encryption, check
:guilabel:`Encrypt disk with GELI`. This option will be greyed out if
:guilabel:`GPT (Best for new hardware)` is not selected as GELI does not
support MBR partitioning. If needed, use :guilabel:`Back` to go back to
the :ref:`Advanced Mode` screen and select
:guilabel:`GPT (Best for new hardware)`. Once that box is checked, input
a strong passphrase twice into the :guilabel:`Password` fields. It is
recommended to create a long and memorable password, but something
difficult to guess.

.. danger:: This passphrase is required to decrypt the disks. If the
   passphrase is lost or forgotten, all access will be lost to the
   encrypted data!

When finished, click :guilabel:`Next` to move to the mount point screen
shown in :numref:`Figure %s <install12>`.

.. _install12:

.. figure:: images/install12c.png
   :scale: 100%

   Default ZFS Layout

Regardless of how many disks are selected for the ZFS configuration, the
default layout is the same. ZFS does not require separate partitions for
:file:`/usr`, :file:`/tmp`, or :file:`/var`. Instead, create one ZFS
partition (pool) and specify a mount for each dataset. A :file:`/boot`
partition is not mandatory with ZFS as the |trueos| installer puts a
64k partition at the beginning of the drive.

.. warning:: Do not remove any of the default mount points. These are
   all used by |trueos|.

Use :guilabel:`Add` to add additional mount points. The system will ask
for the name of the mount point as size is not limited at creation time.
Instead, the data on any mount point can continue to grow as long as
space remains within the ZFS pool.

To set the swap size, click :guilabel:`Swap Size`. This prompts you to
enter a size in MB. If a RAIDZ* or mirror exists, a swap partition
of the specified size is created on each disk and mirrored between the
drives. For example, if a 2048 MB swap size is specified, a 2 GB swap
partition is created on all the specified disks, but the total swap
size is 2GB because of redundancy.

Right-click any mount point to toggle between enabling or disabling many
ZFS properties:

* **atime:** When set to :guilabel:`on`, controls whether the access
  time for files is updated when they are read. When set to
  :guilabel:`off`, this property avoids producing write traffic when
  reading files. This can result in significant performance gains,
  though it may confuse mailers and other utilities.

* **canmount:** If set to :guilabel:`off`, the filesystem is
  unmountable.

* **casesensitivity:** The default is :guilabel:`sensitive`, as UNIX
  filesystems use case-sensitive file names. For example, "kris" is
  different from "Kris". To tell the dataset to ignore case, select
  :guilabel:`insensitive`.

* **checksum:** Automatically verifies the integrity of the data
  stored on disks. Turning this property :guilabel:`off` is highly
  discouraged.

* **compression:** If set to :guilabel:`on`, automatically compresses
  stored data to conserve disk space.

* **exec:** If set to :guilabel:`off`, processes can not be executed
  from within this filesystem.

* **setuid:** If set to :guilabel:`on`, the set-UID bit is respected.

After clicking :guilabel:`Next`, the wizard shows a summary of the
selections. To make further changes, use :guilabel:`Back` to return to
a previous screen. Otherwise, click :guilabel:`Finish` to leave the
wizard and return to the :guilabel:`Disk Selection` screen.

.. index:: install progress
.. _Installation Progress:

Installation Progress
=====================

Once :guilabel:`Yes` is selected to start the installation, a progress
screen, seen in :numref:`Figure %s <install13>`, updates the user on
the installation progress.

.. _install13:

.. figure:: images/install13c.png
   :scale: 100%

   Installation Progress

How long the installation takes depends upon the speed of the hardware
and the installation type selected. A typical installation takes between
5 and 15 minutes.

.. index:: installation finished screen
.. _Installation Finished:

Installation Finished
=====================

The **Installation Finished** screen, shown in
:numref:`Figure %s <install14>`, appears once the installation is
complete.

.. _install14:

.. figure:: images/install14c.png
   :scale: 100%

   |trueos| Installation Complete

Click :guilabel:`Finish` to complete the |trueos| installation. The
system immediately begins the reboot process. Once the system is
fully shut down, remove the installation media to ensure the system
boots from the freshly installed local drive.

.. index:: booting into TrueOS
.. _Booting Into TrueOS:

Booting Into |trueos|
=====================

After installation, |trueos| reboots and displays a boot menu. The
first menu displayed depends on whether or not rEFInd is installed or
the user customized the boot loader during the installation.

.. index:: rEFInd
.. _rEFInd Boot Manage:

rEFInd Boot Manager
-------------------

For EFI or UEFI systems, the user can choose to install rEFInd. This is
a boot manager that is useful when :ref:`Dual Booting`.
:numref:`Figure %s <refind1.2>` shows the initial rEFInd screen.

.. _refind1.2:

.. figure:: images/refind1.png
   :scale: 100%

   rEFInd Boot Manager

rEFInd displays any installed operating systems, booting into the
default choice after a few seconds. Press any key other than
:kbd:`Enter` to pause automatic booting, then use the arrow keys to
select the desired operating system. Press :kbd:`Enter` to continue
booting.

There are a number of options in rEFInd aside from choosing an
operating system:

* **About rEFInd:** This option displays the version and copyrights of
  rEFInd. It also shows the EFI Revision, Platform, Firmware, and
  Screen Output.

* **Shut Down Computer**

* **Reboot Computer**

* **Reboot to Computer Setup Utility:** Not recommended for use with
  |trueos|.

Additional boot options for an operating system are available by
highlighting the OS and pressing :kbd:`F2` or :kbd:`Insert`.

Once |trueos| is chosen in rEFInd, the next boot screen displays.

.. index:: bsd boot loader
.. _BSD Boot Loader:

BSD Boot Loader
---------------

A system with a default or "BSD" install option for the boot loader
loads the boot menu seen in :numref:`Figure %s <install4>`.

.. note:: This menu is modified from the one seen when booting into
   the :ref:`installer <install1>`. While the options are the same,
   they are rearranged slightly to prevent confusion and unnecessary
   clutter.

.. _install4:

.. figure:: images/install4.png
   :scale: 100%

   |trueos| Boot Menu

This menu provides several options. Pause this menu by pressing any key
except for :kbd:`Enter`. To select an option, press either the bolded
number or key for that option. Once any selections are made, press
:kbd:`Enter` to boot using the specified options.

* :guilabel:`1. Boot TrueOS [Enter]`: This is the default option for
  booting |trueos|. The system automatically uses this option either
  after pausing for a moment or if :kbd:`Enter` is pressed while the
  boot menu is displayed.

* :guilabel:`2. Configure Boot Options`: Press either :kbd:`2` or
  :kbd:`o` to see the boot options screen, shown in
  :numref:`Figure %s <boot1>`. To change an option, press either the
  bolded number or key for the option to toggle through its available
  settings. When finished, press either :kbd:`1` or :kbd:`Backspace` to
  return to the |trueos| boot menu.

* :guilabel:`3. Select Boot Environment`: In |trueos|, boot environments
  are automatically created when the system updates. They can also be
  manually created using the
  :sysclbk:`Boot Environment Manager <boot-environment-manager>`. This
  allows the system to boot to the point of time before an update
  occurred and can be used to recover from a failed update. Press either
  :kbd:`3` or :kbd:`e` to view the available boot environments.

.. tip:: The first time the system boots, no additional environments are
   available. This menu populates as boot environments are created.

.. _boot1:

.. figure:: images/boot1c.png
   :scale: 100%

   Boot Options Menu

Several boot options are available in the Boot Options Menu:

* :guilabel:`3. Boot Single User`: Advanced users can select this option
  to fix critical system failures.

* :guilabel:`4. Verbose`: Select this option to see more detailed
  messages during the boot process. This can be useful when
  troubleshooting a piece of hardware.

* :guilabel:`5. Kernel`: This option indicates how many kernels are
  available. Press either :kbd:`5` or :kbd:`k` to toggle between
  available kernels. This option is available to the user if they have
  created a custom kernel, but wish to have a :file:`kernel.old` boot
  option available in case the custom primary kernel fails.

* :guilabel:`6. Escape to loader prompt`: Advanced users can select this
  option to perform advanced operations, such as loading kernel modules.

.. index:: encrypted disks
.. _Encrypted Disks:

Encrypted Disks
---------------

If :guilabel:`Encrypt disk with GELI` was selected during installation,
physical access to the |trueos| system when it boots is required. As the
system starts to boot, it displays a message similar to the one shown in
:numref:`Figure %s <encrypt1>`.

.. _encrypt1:

.. figure:: images/encrypt1.png
   :scale: 100%

   Master Key Decryption

The boot process will wait for the password created in the installation
screen shown in :ref:`Configure Encryption <install11>`. If the correct
password is typed, the system calculates the GELI encryption key then
continues to boot.

.. index:: display detection
.. _Display Detection:

Display Detection
=================

.. TODO update screenshot and remove note box when advanced tab is
   removed.

When booting for the first time, |trueos| shows a
:guilabel:`Display Settings` screen, reproduced in
:numref:`Figure %s <display3>`.

.. _display3:

.. figure:: images/display3a.png
   :scale: 100%

   Display Settings

Use this screen to view the detected video card and choose a graphics
driver from the expanding menu. |trueos| also suggests a driver.

The :guilabel:`vesa` driver always works but provides sub-optimal
performance. Click on the drop-down menu to select the driver most
closely matching your video card name.

When finished, click :guilabel:`Apply` for the settings to be tested. If
anything goes wrong during testing, the system returns to the
:guilabel:`Display Settings` screen in order for the user to select
another driver. Once satisfied with the settings, click :guilabel:`Yes`
when prompted to accept them.

.. note:: The :guilabel:`Advanced` tab is disabled and scheduled for
   removal.

.. index:: choose language
.. _Choose a Language:

Choose a Language
=================

:numref:`Figure %s <config1>` shows the language selection screen.

.. _config1:

.. figure:: images/config1a.png
   :scale: 100%

   Language Selection

This allows for the selection of the language used to access the
installed system. It also contains three icons from the installer
screens to enable:

* **Light Bulb**: Reading the screen's *Help* text.

* **Keyboard**: Use the onscreen keyboard.

* **Key with US and Brazilian Flag**: Choose a different keyboard layout
  other than the default US style.

Once the selection is made, click :guilabel:`Next` to move to the next
configuration screen.

.. index:: time zone select
.. _Time Zone Selection:

Time Zone Selection
===================

The timezone select screen, shown in :numref:`Figure %s <config2>`,
allows selection of the timezone and configuring the system's host and
domain names.

.. _config2:

.. figure:: images/config2c.png
   :scale: 100%

   Time Zone Selection

Use the drop-down menu to select the city closest to the system's
location. If the system is connected to the Internet, the installer
automatically attempts to detect the correct timezone.

If the system is dual booting and the other operating system expects the
BIOS to use UTC, also check :guilabel:`Set BIOS to UTC time`.

A default system hostname is created. Change the name by typing the
desired hostname in the :guilabel:`System Hostname` field. If the
computer is a member of a DNS domain, the :guilabel:`Domain Name` is
also an option.

When finished, click :guilabel:`Next` to proceed to the next screen.

.. index:: setting a root password
.. _Set the Root Password:

Set the Root Password
=====================

This screen, seen in :numref:`Figure %s <config3>`, **requires** setting
the root (administrative) password.

.. _config3:

.. figure:: images/config3b.png
   :scale: 100%

   Root Password Creation

The password must be a minimum of **4** characters and typed twice to
confirm the password. Try to create a complex, but memorable password,
as this is used whenever the system indicates administrative access is
required. Click :guilabel:`Next` when finished.

.. index:: create a user
.. _Create a User:

Create a User
=============

This screen is used to create the primary user account used to login to
the system.

:numref:`Figure %s <config4>` shows the configuration screen used to
create the initial user account.

.. _config4:

.. figure:: images/config4b.png
   :scale: 100%

   User Creation

The :guilabel:`User Details` tab is used to create a login user. This
screen requires completing several fields:

* **Name:** This value displays in the login screen. It can be the
  user's full name and can contain both capital letters and spaces.

* **Username:** This is the name used when logging in. It can **not**
  contain spaces and **is** case sensitive (e.g. *Kris* is a different
  username from *kris*).

* **Password:** This is the password to use when logging in. It must
  be typed twice for confirmation.

* **Specify UID:** By default, the user is assigned the next available
  User ID (UID). If a specific UID is required, it can be set here. A
  UID can not be set lower than 1001, and a UID already in use by
  another account is also unavailable.

|trueos| provides the ability to use a removable device, such as a USB
stick, as the user's encrypted home directory. This is useful in a
multi-user or multi-computer environment, as it provides the user with
secure access to their encrypted files.  When a user initializes
:sysclbk:`PersonaCrypt <personacrypt>` with their account, their
username only appears in the login menu if the removable media
associated with that |trueos| system is inserted. They must input the
password associated with the removable device in order to log in.

When a user is configured to use a PersonaCrypt device, that user cannot
log in using an unencrypted session on the same system. In other words,
the PersonaCrypt username is reserved only for PersonaCrypt use. If
necessary to login to both encrypted and unencrypted sessions on the
same system, create two different user accounts; one for each type of
session.

.. note:: Encryption is also possible without requiring removable
   devices using *PEFS*. Refer to the |sysadm| handbook section on
   :sysclbk:`PEFS Encryption <pefs>` for more detailed instructions to
   initialize a user with *PEFS*.

:numref:`Figure %s <persona1>` shows the :guilabel:`PersonaCrypt` tab.
This is used to initialize PersonaCrypt for the user.

.. _persona1:

.. figure:: images/persona1a.png
   :scale: 100%

   User's PersonaCrypt Initialization

Check :guilabel:`Initialize PersonaCrypt Device`, insert a removable
media device large enough to hold a user's home directory, then click
:guilabel:`Select`.

.. warning:: Ensure there are no desired files on the removable media.
   Initializing the media for PersonaCrypt formats the device with ZFS
   and then encrypts it with GELI, deleting any existing data.

Input and repeat the :guilabel:`Device Password` to associate with the
device. A pop-up window indicates the current contents of the device
will be wiped. Click :guilabel:`Yes` to initialize the device.

To share the computer with other users, create additional login and
*PersonaCrypt* accounts using the |sysadm|
:sysclbk:`User Manager <user-manager>`. After creating at least one
user, click :guilabel:`Next` to continue.

.. index:: configure audio output
.. _Configure Audio Output:

Configure Audio Output
======================

:numref:`Figure %s <audio1>` shows the Audio Output screen, where you
can choose the output device and test it.

.. _audio1:

.. figure:: images/audio1b.png
   :scale: 100%

   Configure Audio Output

Click the :guilabel:`Output Device` drop-down menu to select the
desired sound device. Click :guilabel:`Test` to verify the setting. If
the device works, a test sound plays. The :guilabel:`Testing Volume`
slider is also used to set the default system volume level.

All these settings can be viewed and edited at any time using the
instructions in :ref:`Sound Mixer Tray`.

.. index:: connect to a wireless network
.. _Connect to a Wireless Network:

Connect to a Wireless Network
=============================

.. note:: The network card must be supported by FreeBSD. Refer to
   :ref:`Supported Hardware` for links to FreeBSD support and a list of
   known issues with different hardware.

If the system has an active wireless interface, a screen similar to
:numref:`Figure %s <config5>` indicates which wireless networks are
automatically detected. Available networks are ordered by signal
strength.

.. _config5:

.. figure:: images/config5a.png
   :scale: 100%

   Wireless Network Connections

To set the default wireless connection, click the desired network in the
:guilabel:`Available Wireless Networks` area. If the network requires a
password, a window appears requesting the password and indicating the
security type used by the desired network. If the desired network is not
visible in the :guilabel:`Available Wireless Networks` area, click
:guilabel:`Rescan`. If unable to connect or to configure the connection
later, refer to :ref:`Network Manager` for more detailed instructions.

.. index:: enable optional services, SSH, IPv6
.. _Enable Optional Services:

Enable Optional Services
========================

:numref:`Figure %s <config6>` shows a few optional system services you
can toggle.

.. _config6:

.. figure:: images/config6a.png
   :scale: 100%

   Optional Services

Check :guilabel:`Disable IPV6 (Requires Reboot)` to reconfigure the
system to only support IPv4 addresses. By default, the system supports
both IPv4 and IPv6, and IPv6 is preferred over IPv4.

.. tip:: Altering this setting does not take affect until the next
   system reboot.

:guilabel:`Enable Intel HDA polling` enables the audio driver polling
mode. It is used in |trueos| to support additional Intel audio devices
that would not function without polling. However, it is recommended to
**not** enable unless you are having extensive audio device issues, or
your Intel device requires polling mode enabled. See the
`FreeBSD Manual Page <https://www.freebsd.org/cgi/man.cgi?query=snd_hda&apropos=0&sektion=4&manpath=FreeBSD+12-current&arch=default&format=html>`_
for more details.

:guilabel:`Enable Realtek Wireless` activates the Realtek wireless
networking drivers.

If :guilabel:`Enable SSH` is checked, the SSH service both starts
immediately and is configured to start on system boot. This option also
creates the firewall rules needed to allow incoming SSH connections to
the |trueos| system.

.. danger:: **Do not** check this box if SSH connections to the system
   are undesired.

:guilabel:`Enable Verbose Boot` is the same option as in :ref:`boot1`.
Select this option to see more detailed messages during the boot
process. This can be useful when troubleshooting a piece of hardware.

When finished choosing optional services, click :guilabel:`Next`. The
screen in :numref:`Figure %s <config7>` indicates the post-installation
setup is complete. Click :guilabel:`Finish` to access the login menu.

.. _config7:

.. figure:: images/config7a.png
   :scale: 100%

   Setup Complete

.. index:: logging in
.. _Logging In:

Logging In
==========

Once finished setting up the system, the PCDM (|pcbsd| Display Manager)
graphical login screen displays. An example is seen in
:numref:`Figure %s <login1>`.

.. _login1:

.. figure:: images/login1.png
   :scale: 100%

   |trueos| Login

The hostname of the system is displayed at the top of the login window.
In this example, it is *trueos-5026*. This login screen has several
configuration options:

* **User:** Upon first login, the created **username** (from
  :ref:`Create a User`) is the only available login user. If additional
  users are created using the |sysadm|
  :sysclbk:`User Manager <user-manager>`, they are added to the
  drop-down menu for more login choices. PCDM does not allow logging in
  as the *root* user. Instead, whenever a utility requires
  administrative access, |trueos| asks for the password of the login
  account.

* **Password:** Input the password associated with the selected user.

* **Desktop:** If any additional desktops are installed using
  :sysclbk:`AppCafe <appcafe>`, use the drop-down menu to select the
  desktop to log into.

.. note:: If a PersonaCrypt user is active, insert the PersonaCrypt
   device in order to log in. As seen in :numref:`Figure %s <login5>`,
   this adds an extra field to the login screen so the password
   associated with the PersonaCrypt device can be typed.

.. _login5:

.. figure:: images/login5.png
   :scale: 100%

   |trueos| PersonaCrypt Login

The toolbar across the bottom of the screen allows several options to be
selected on a per-login basis:

* **Locale:** If the localization was not set during installation, or
  needs to be changed, click this icon to set the locale for this login
  session.

* **Keyboard Layout:** Click this icon to change the keyboard layout
  for this login session. This opens the window seen in
  :numref:`Figure %s <keyboard1>`.

.. _keyboard1:

.. figure:: images/keyboard1.png
   :scale: 100%

   Keyboard Settings

Click the :guilabel:`Keyboard model` drop-down menu to select the type
of keyboard.

.. note:: The default model of :guilabel:`Generic 104-key PC` does
   **not** support special keys such as multimedia or Windows keys.
   Choose another model to enable support for hot keys.

This screen also allows selection of the :guilabel:`Key Layout` and
:guilabel:`Variant`. After making any selections, test them by typing
some text into the :guilabel:`you may type into the space below...`
field.

.. tip:: It is possible to change keyboard layouts during an active
   desktop session using the included :command:`fcitx` utility

* **Restart/Shut Down:** To restart or shutdown the system without
  logging in, click the :guilabel:`Power Button` icon in the
  lower-right corner of the screen. This icon also allows you to
  :guilabel:`Change DPI`, :guilabel:`Refresh PCDM`, and
  :guilabel:`Change Video Driver`.

Once any selections are made, input the password associated with the
selected user and press :kbd:`Enter` or click the :guilabel:`blue arrow`
to login.
