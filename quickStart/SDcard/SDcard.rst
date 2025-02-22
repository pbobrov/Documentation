.. _prepareSD:

Prepare SD card
###############

**********************************
Download and install SD card image
**********************************

The next procedure will create a clean SD card.

#. Download the Red Pitaya SD card image:

STEMlab 125-14 & STEMlab 125-10:

   - `Latest Stable <https://downloads.redpitaya.com/downloads/STEMlab-125-1x/STEMlab_125-xx_OS_1.04-11_stable.img.zip>`_  - |CHANGELOG|
   - `Latest Beta <https://downloads.redpitaya.com/downloads/STEMlab-125-1x/STEMlab_125-xx_OS_1.04-18_beta.img.zip>`_  - |CHANGELOG|

STEMlab 125-14-Z7020:

   - `Latest Stable <https://downloads.redpitaya.com/downloads/STEMlab-125-14-Z7020/STEMlab_125-14-Z7020_OS_1.04-10_stable.img.zip>`_  - |CHANGELOG|
   - `Latest Beta <https://downloads.redpitaya.com/downloads/STEMlab-125-14-Z7020/STEMlab_125-14-Z7020_OS_1.04-14_beta.img.zip>`_  - |CHANGELOG|

SDRlab 122-16:

   - `Latest Stable <https://downloads.redpitaya.com/downloads/SDRlab-122-16/SDRlab_122-16_OS_1.04-11_stable.img.zip>`_  - |CHANGELOG_Z20|
   - `Latest Beta <https://downloads.redpitaya.com/downloads/SDRlab-122-16/SDRlab_122-16_OS_1.04-15_beta.img.zip>`_  - |CHANGELOG_Z20|

SIGNALlab 250-12:

   - `Latest Stable <https://downloads.redpitaya.com/downloads/SIGNALlab-250-12/SIGNALlab_250-12_OS_1.04-27_stable.img.zip>`_  - |CHANGELOG_Z20_250_12|
   - `Latest Beta <https://downloads.redpitaya.com/downloads/SIGNALlab-250-12/SIGNALlab_250-12_OS_1.04-30_beta.img.zip>`_  - |CHANGELOG_Z20_250_12|


.. |CHANGELOG| raw:: html

   <a href="https://github.com/RedPitaya/RedPitaya/blob/master/CHANGELOG.md" target="_blank">CHANGELOG</a>

.. |CHANGELOG_Z20| raw:: html

   <a href="https://github.com/RedPitaya/RedPitaya/blob/master/CHANGELOG_Z20.md" target="_blank">CHANGELOG</a>

.. |CHANGELOG_Z20_250_12| raw:: html

   <a href="https://github.com/RedPitaya/RedPitaya/blob/master/CHANGELOG_Z20_250_12.md" target="_blank">CHANGELOG</a>
   
   

.. figure:: microSDcard-RP.png
    :width: 10%

#. Unzip the SD card image.

#. Write the image onto a SD card. Instructions are available for various operating systems:

.. contents::
    :local:
    :backlinks: none
    :depth: 1

4. Insert the SD card into Red Pitaya.

   .. figure:: pitaya-quick-start-insert-sd-card.png
      :align: center

.. note::
   
   The video shows how to identify the RedPitaya model and write a memory card.

   .. raw:: html

    <div style="position: relative; padding-bottom: 30.25%; overflow: hidden; max-width: 50%; margin-left:auto; margin-right:auto;">
        <iframe src="https://www.youtube.com/embed/Qq_YRv2nk3c" frameborder="0" allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe>
    </div>

=======
Windows
=======

#. Insert SD card into your PC or SD card reader.

   .. figure:: SDcard_insert.jpg
      :align: center

#. Download `Win32 Disk Imager <https://sourceforge.net/projects/win32diskimager/>`_ and extract it.

   .. figure:: SDcard_Win_Win32DiskImager.png
      :align: center

#. Open unzipped folder, right-click on the ``WinDisk32Imager``, and select **Run as Administrator**.

   .. figure:: SDcard_Win_RunAsAdmin.png
      :align: center

#. Under image file box select unzipped Red Pitaya image file.

   .. figure:: SDcard_Win_SelectImg.png
      :align: center

#. Under device box select the drive letter of the SD card.

   .. figure:: SDcard_Win_SelectDrive.png
      :align: center

   .. note::

      Be careful to select the correct drive.
      If you choose the wrong one you risk erasing data
      from the computer's hard disk!
      You can easily see the drive letter (for example E:)
      by looking in the left column of Windows Explorer.

   .. figure:: SDcard_Win_DriveLetter.png
      :align: center

#. Click Write and wait for the write to complete.

   .. figure:: SDcard_Win_Write.png
      :align: center

#. Exit the Imager.

   .. figure:: SDcard_Win_Exit.png
      :align: center

=====
Linux
=====

.. _linux_gui:

-------------------------
Ubuntu using Image Writer
-------------------------

1. Right click on the extracted SD card image and select **Open With > Disk Image Writer**.

.. figure:: DIW_1.png
      :align: center
      :width: 50%

      Context menu

.. figure:: DIW_2.png
      :align: center
      :width: 50%

      Select tool dialog

2. In the **Restore Disk Image** window select your SD card in the **Destination** pull down menu.
   Be carefull to select the correct device, use the size for orientation (for example 4GB SD card).

.. figure:: DIW_3.png
      :align: center
      :width: 50%

      Select drive dialog

3. You will be asked to confirm your choice and enter a password.
   Additiona dialog windows will again show the selected destination drive,
   take the oportunity to think again if you choose the right device.


.. _linux_cli:

------------
Command line
------------

.. note::
   Please note that the use of the ``dd`` tool can overwrite any partition of your machine.
   If you specify the wrong device in the instructions below, you could delete your primary Linux partition.
   Please be careful.

#. Insert SD card into your PC or SD card reader.

   .. figure:: SDcard_insert.jpg
      :align: center

#. Open the Terminal and check the available disks with ``df -h``.
   Our SD card is 4GB, it is named ``/dev/sdx`` and
   divided into two partitions ``/dev/sdx1`` and ``/dev/sdx2``.
   The drive mounted at ``/`` is your main drive,
   be carefull not to use it.

   .. code-block:: shell-session

      $ df -h
      Filesystem      Size  Used Avail Use% Mounted on
      /dev/sdx1       118M   27M   92M  23% /media/somebody/CAD5-1E3D
      /dev/sdx2       3.2G 1013M  2.1G  33% /media/somebody/7b2d3ba8-95ed-4bf4-bd67-eb52fe65df55

#. Unmount all SD card partitions with ``umount /dev/sdxN``
   (make sure you replace N with the right numbers).

   .. code-block:: shell-session

      $ sudo umount /dev/sdx1 /dev/sdx2

#. Write the image to the SD card with the following command.
   Replace the ``red_pitaya_image_file.img`` with
   the name of the unzipped Red Pitaya SD Card Image
   and replace ``/dev/device_name`` with the path to the SD card.

   .. code-block:: shell-session

      $ sudo dd bs=1M if=red_pitaya_image_file.img of=/dev/device_name

#. Wait until the process has finished.


=====
macOS
=====

.. _macos_gui:

-------------------
Using ApplePi-Baker
-------------------

#. Insert SD card into your PC or SD card reader.

   .. figure:: SDcard_insert.jpg
      :align: center

#. Download `ApplePi-Baker <https://www.tweaking4all.com/hardware/raspberry-pi/applepi-baker-v2/>`_. Direct link:

   - `ApplePi-Baker-v2.2.3.dmg <https://www.tweaking4all.com/downloads/raspberrypi/ApplePi-Baker-v2.2.3.dmg>`_
   - `ApplePi-Baker-1.9.9.dmg <https://www.tweaking4all.com/downloads/raspberrypi/ApplePi-Baker-1.9.9.dmg>`_

#. Click on *ApplePi-Baker* icon, then click *Open* in order to run it.

   .. figure:: SDcard_macOS_open.png
      :align: center

#. Drag and drop *ApplePi-Baker* for install it.

   .. figure:: SDcard_macOS_install.png
      :align: center

#. Enter your admin password and click OK.

   .. figure:: SDcard_macOS_password.png
      :align: center

#. Select SD card drive. This can be recognized by the size of the card that is 8GB.

   .. figure:: SDcard_macOS_ApplePi-Baker_drive.png
      :align: center

#. Select Red Pitaya OS image file.

   .. figure:: SDcard_macOS_ApplePi-Baker_image.png
      :align: center

#. It's coffee time, application will show you Estimated Time for Accomplishment.

   .. figure:: SDcard_macOS_ApplePi-Baker_wait.png
      :align: center

#. When operation is completed you can see status Idle.

   .. figure:: SDcard_macOS_ApplePi-Baker_quit.png
      :align: center

.. _macos_cli:

------------
Command line
------------

#. Insert SD card into your PC or SD card reader.

   .. figure:: SDcard_insert.jpg
      :align: center

#. Click **cmd + space**, type **Disk Utility** into the search box and press enter.
   From the menu select your SD card and click on **Erase** button (be careful not to delete your disk!).

   .. figure:: SDcard_macOS_DiskUtility.png
      :align: center

#. Click **cmd + space**, type in **Terminal** and press enter.
   In the terminal window type: ``cd``, press enter,
   then type: ``cd Desktop`` and press enter again.

#. Unmount the partition so that you will be allowed to overwrite the disk.
   In Terminal type: ``diskutil list`` and press enter.
   This will show you the list of all memory devices.

   .. figure:: Screen-Shot-2015-08-07-at-16.59.50.png
      :align: center

   Unmount with: ``diskutil UnmountDisk /dev/diskn``
   (insert the number ``n`` of your disk correctly!)

   .. figure:: Screen-Shot-2015-08-07-at-17.14.34.png
      :align: center

#. Type in: ``sudo dd bs=1m if=path_of_your_image.img of=/dev/rdiskn``
   (Remember to replace ``n`` with the number that you noted before!)
   (notice there is letter ``r`` in front of the disk name, use that as well!)

   .. figure:: Screen-Shot-2015-08-07-at-17.14.45.png
      :align: center

#. Type in your password and wait a few minutes for the image to be written.

#. When the image is written, type: ``diskutil eject /dev/diskn`` and press enter.

#. Safely eject the SD card.

**********
Background
**********

A Red Pitaya SD card contains two partitions:

1. 128MB FAT contains the **ecosystem**

   * boot files: FSBL, FPGA images, U-Boot, Linux kernel
   * Red Pitaya API libraries and header files
   * Red Pitaya web applications, scripts, tools
   * customized Nginx web server

2. ~4GB Ext4 contains the **OS**

   * Ubuntu/Debian OS
   * various libraries
   * network setup customization
   * systemd services customization

Most of Red Pitaya source code translates into the ecosystem,
Therefore this is updated more often.
The OS is changed less frequently.

.. note::

   You can find older and development Red Pitaya OS images and Ecosystem zipfiles
   on our `download server <https://downloads.redpitaya.com/downloads/>`_.

.. note::

   A list of new features, bugfixes and known bugs for each Red Pitaya release
   can be found in our `CHANGELOG <https://github.com/RedPitaya/RedPitaya/blob/master/CHANGELOG.md>`_.


**************
Manual upgrade
**************

Instead of writing the whole SD card image,
it is possible to upgrade only the ecosystem.

A manual upgrade allows you to fix a corrupted SD card image
(if only the FAT partition is corrupted) or to install
older, newer or custom ecosystem zip files.

#. Download a zip file from our `download server <https://downloads.redpitaya.com/downloads/>`_.

#. Insert SD card into card reader.

#. Delete all files from the FAT partition.
   Use ``Shift + Delete`` to avoid placing files
   into a trash bin on the same partition.

#. Extract the ecosystem zip file contents onto the now empty partition.

If you wish to keep wireless settings skip deleting the next files:

* ``wpa_supplicant.conf``
* ``hostapd.conf``


******************
Resize file system
******************

When recording an image to a flash card of any size, we get sections of the file system 4 GB in size.
In order to increase the available free space you need to execute the script:

      .. code-block:: shell-session

          root@rp-f03dee:~# /opt/redpitaya/sbin/resize.sh

After the script is completed, the system will ask you to restart Red Pitaya.
If everything is done correctly, start the system with an increased size of space. This can be checked with the command:

      .. code-block:: shell-session

          root@rp-f03dee:~# df -h


.. note::

   If the file system size has not changed, you can try to manually run the command:

      .. code-block:: shell-session

         root@rp-f03dee:~# sudo resize2fs /dev/mmcblk0p2

