# Session#1 Part 1
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)


# A Glimpse on Linux History & Introduction to Operating Systems

## Operating Systems
### OS Layers
An operating system is the main piece of software needed to run a computer, without it the computer won’t function. Here’s a simplified view:

![OS Layers](./Images/Session%201/Layers.png)

**The GUI:** Graphical User Interface, used to allow the user to interact with the system by using a graphical interface.

**The Shell:** Allows the user to use the OS by typing commands.

**The Kernel:** The core of the OS, responsible for memory management, and communication with the hardware.

### Boot Process
The boot process consists of many layers executing each other to load the operating system finally.

![Boot Process Order](./Images/Session%201/UEFI.png)


**BIOS/UEFI:** Checks that the system is working properly and then executes the MBR/EFI.

**MBR/EFI:** MBR/EFI executes the bootloader (In the case of Linux, it is GRUB)

**Bootloader(GRUB):** The bootloader then checks the kernel and loads it.

**Operating System:** The rest of the operating system loads.

## Open Source and Linux History

![Timeline](./Images/Session%201/Timeline.png)

**Note:** The *correct term* is GNU/Linux not just Linux or GNU, because it is the GNU operating system using the Linux kernel. 
We just say Linux because it is shorter, easier to say, and more popular.

## Linux Distribution Families
Since Linux and GNU are both open source, many people from different communities have made different Linux Distributions.
There are too many distributions to count, so we’ll talk about the three main families:

1. **Red Hat Family**

This family concentrated on the enterprise side of things, such as servers and company workstations.

2. **Debian Family**

The Debian family started with the home user in mind, the community wanted to make GNU/Linux available for the average user as much as it was for enterprises at the time.

3. **Other distributions built for specific use cases**

Distributions such as Arch Linux, openSUSE, SLES, Gentoo, and many others were made for specific use cases or optimisations based on what the community wanted.

![Distributions](./Images/Session%201/Distros.png)

[Here's a link to a more full and HUGE Linux family tree.](https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg)
## Why Linux?

There are many reasons to use Linux, I’ll name a few but there are always more reasons.

1. **Privacy and Security**

The operating system respects the privacy of users to a really unique extent, once the system starts running everything that happens is under your control unless a third party services is used.
That is mainly due to it being open source, so developers can’t hide spyware or force anything on the user, as they will be able to somehow avoid or change it.

2. **Required in Companies**

It is required in many companies, including Microsoft, ITWorx, Mentor, Valeo, and a lot of other big popular companies.

3. **Good Development Environment**

Due to features like package managers, the command line, the operating system being very low on resource usage, customisability, and many more, GNU/Linux is a great development environment.

4. **Free**

GNU/Linux is both free as in freedom and free of charge, it has a lot of great alternatives for proprietary sofrware that people use daily.

5. **Decentralised Development**

GNU/Linux isn’t owned by a single company, its development is community driven. People contribute to the Linux kernel and other assets of the GNU operating system.

6. **Customisability**

The operating system is very modular and customisable, which allows you to create your own customised system according to your needs.

7. **Much more!**

## Some Important Terminology
- **Kernel:** The core of the operating system, responsible for memory and process management, and communication with the hardware .
- **Shell:** One of the operating system layers that allows the user to use the OS by typing commands.
- **UNIX:** A proprietary software operating system that was designed for servers, programmers, and HPC.
- **Linux:** Free and open source kernel.
- **FOSS:** Free and Open Source Software.
- **Proprietary Software:** Closed source software that is copyrighted.
- **GNU:** GNU’s Not Unix, a free and open source operating system designed to replace Unix.
- **GNU/Linux:** Used to refer to the GNU operating system when it is using the Linux kernel.
- **Linux Distribution:** An operating system that is built on the Linux kernel or forked from an existing Linux distribution, like Ubuntu, Debian, Linux Mint, RHEL, etc..
- **Desktop Environment:** The GUI that a Linux distribution uses to allow the user to interact with it without having to type commands.
- **Debian:** A Linux distribution built for home users.
- **Red Hat Enterprise Linux (RHEL):** A Linux distribution built forservers targeted at the enterprise side.
- **Ubuntu:** A Linux distribution that is based on Debian, it is known to be very easy to use and very intuitive for new users.
