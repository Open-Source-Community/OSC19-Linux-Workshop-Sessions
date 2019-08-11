# Session#1 Part 2
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)


# Linux Installation Alongside Windows

## Choosing a Suitable Distribution

> There are a lot of Linux distros offered and there are 3 main aspects yo look for when deciding which distro to go for.

* #### Base Distro

For the first-time linux users it's recommended to start with Ubuntu and Ubuntu based distros such as:
   - The Ubuntu Family(Ubuntu, Kubuntu, Lubuntu, Ubuntu Budgie, etc..)
   - Linux Mint
   - KDE Neon

* #### Look and Feel
There are many flavours in how the OS looks and how it can be customized to look even better to be more suitable for every taste and this is determined by what's called Desktop Environment of the distro and some distros can be found with different Desktop Environments such as:

   * Linux Mint can be found in 3 desktop environments

        * Cinnamon
   
             ![](https://www.linuxmint.com/pictures/screenshots/tessa/thumb_cinnamon.png)
   
        * MATE
   
             ![](https://www.linuxmint.com/pictures/screenshots/tessa/thumb_mate.png)
   
        * Xfce
   
             ![](https://www.linuxmint.com/pictures/screenshots/tessa/thumb_xfce.png)


`Note:` Each one of these looks has a difference from its relatives other than the shape and look.

`e.g. Xfce is more lightweight relative to Cinnamon and MATE.`

* #### Applications

Every OS comes with preinstalled applications and every distro comes with pretty much the same applications preinstalled except for some distros like [Ubuntu Studio](https://ubuntustudio.org) for example which combines the ease of use (as it's a member of the Ubuntu Family) and the set of Applications that it comes with.

![](https://ubuntustudio.org/wp-content/uploads/2012/06/feature-tour.png)

[Ubuntu Studio](https://ubuntustudio.org) comes with applications for:
  * Audio Production
  * Graphic Design
  * Video Production
  * Photography
  * Publishing

Which makes it a great OS and a very suitable distro for a lot of people that need these kinds of applications on their daily basis.

***

## Understanding and Preparing the PC
>In order to install any OS on a PC a specific amount of unallocated disk space is needed and providing this space requires a basic knowlede of what partition table you're using.  

There are 2 types of firmwares
* #### Old BIOS (Legacy Boot)
![](https://upload.wikimedia.org/wikipedia/commons/0/05/Award_BIOS_setup_utility.png)

This type of firmware uses **MBR** (Master Boot Record) partition table.

**A Partition table that allows the creation of 4 primary partitions that can include a maximum count of one `Extended Partition` which is a type of partitions that includes `Logical Partitions` that functions like a primary partitions.**

* #### UEFI (Unified Extensible Firmware Interface)
![](./Images/Session%201/UEFI%20Screen.png)
![](./Images/Session%201/The%20Cooler%20UEFI%20Screen.png)

This type of firmware uses **GPT** (GUID Partition Table) as the default partition table.

**A partition table that allows the creation of many primary partitions and doesn’t have neither `Extended Partitions` nor `Logical Partitions` as they are not needed.**


`Note:` **MBR** can be used but only if the boot option was set to **Legacy Boot**

**`Caution Notice:` Converting from MBR to GPT or vice versa will cause all of the data on the drive to be erased as a result of the conversion.**

### In Conclusion
* ##### If you have `old BIOS` or your system is using `Legacy Boot` then the disk is using the `MBR` partition table and you are limited to `4 partitions`.
  * ###### If you already have `4 primary partitions`
    * You’ll have to `delete` one of your partitons and make a new `Extended partiton`.
    * Back up your data from a partition.
    * Delete the partition.
    * Create a new extended partition from the unallocated space.
    * Make a new NTFS partition to continue using it from Windows, leaving at least 30 GiBs to install GNU/Linux on them.

  * ###### If you have `3 primary partitions`
    * You’ll have to `shrink` one of the existing partitions leaving at least 30 GiBs of unallocated space after it.

  * ###### If you have `less than 3 Primary Partitions` and `1 Extended Partition`
    * You'll have to `shrink` one of the existing `Logical Partitions` inside the `Extended Partiton` preferably the last one leaving at least 30 GiBs of unallocated space after it.

* ##### If you are using `UEFI` then your disk drive is using the `GPT` Partition table which means you can create multiple `Primary Partitons`.

  * you’ll only need to `shrink` one of the existing partitions and leaving at least 30 GiBs of unallocated disk space after it.

`Tip:` It’s recommended to use `GParted` from the live USB for deleting, shrinking and/or creating extended partitions before the installation. It is highly inadvisable to use the Windows Disk Management utility from Windows.

***

## Installing GNU/Linux
You can check this guide in Arabic for more details at oscgeeks.org/Linux
>After partitioning, if you’ve done everything correctly, the installation should be very straight forward.

1. Boot from your installation media in the right mode (`UEFI` or `Legacy`)
(If you already had the installation media running, make sure you’re in the correct boot mode by restarting and choosing the correct one)

2. Start the installation software `Install _____ on this PC`.
![](./Images/Session%201/Install%20Linux%20Mint.png)

3. Make sure to check this box if you don’t mind using some proprietary software, a lot of them may be essential for your system.
![](./Images/Session%201/Install%20third-party%20software.png)

4. You should find an option for `Install _____ alongside Windows Boot Manager` or something in a similar fashion. Select it.
![](./Images/Session%201/Install%20Linux%20Mint%20alongside%20Windows%2010.png)

5. Continue entering the required information when prompted during the installation.

**`Caution Notice`: Do not ignore any dialog box you encouter as it may cause critical damage to your PC.**

You can ask for help on the workshop’s group(If you've attended) or on our [Facebook group](https://facebook.com/groups/osc.troubleshot)
