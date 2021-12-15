<!-- Versão em inglês -->

# Hexagonix/Andromeda Operating System

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix.png" width="250" height="250">
</p>

Welcome to the Hexagonix/Andromeda Operating System

## Copyright Notes

Hexagonix/Andromeda was developed from scratch by [Felipe Lunkes](https://github.com/felipenlunkes).

Read the [license](LICENSE) for more information on copyright, code ownership and redistribution.

* Hexagonix Operating System & Andromeda Operating System. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Hexagon kernel. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Saturn Boot Manager. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Hexagon Boot (HBoot). Copyright © 2020-2022 Felipe Miguel Nery Lunkes. All rights reserved.

## First of all

At the end of this file you will find a tutorial to run Hexagonix/Andromeda on your computer, both in a virtualized version and natively. Remember that you must have a computer with x86 architecture or an emulator if you are using a device of another architecture for testing.

* [System Documentation (under construction)](https://github.com/hexagonix/Distro/tree/main/Doc)

# About the system

## Development

Hexagonix/Andromeda and all its components have been in development since 2015 and were written completely in Assembly language.

## Why two names? Hexagonix and Andromeda, what are they?

In the beginning, Andromeda was intended to be a complete operating system, consisting of the kernel, libraries, graphical and text interface and utilities. Later, with the passage of time and the change in approach to the system's architecture and objectives, the components were separated and became independent projects in terms of functioning, organization and development. As you can see below, the core of Andromeda was separated from the rest of the Andromeda code tree, becoming an independent project, even given a name, Hexagon. From then on, the idea of ​​making the composition of the system more flexible and allowing the development of distributions, as in GNU/Linux, arose. In this way, Hexagon distributions could be created, grouping the components necessary for the basic operation (Hexagonix) and allowing the extension of the system if necessary, with new components, modules and utilities, with the userland defined in each case. With the architecture change of the system itself, with the core approaching a Unix-like architecture, new utilities in Unix style and syntax were developed and kept separate, in another project. From the original Andromeda project we have Andromeda-specific graphical libraries and applications. A base system was then created, which by itself can be fully implemented, and became the base of Andromeda. This base system is called Hexagonix, and is composed of the HBoot boot loader, the Hexagon kernel, the shell, Unix environment libraries (here called Hexagonix environment) and Unix utilities. This system is fully functional, but lacks graphical resources and applications developed for the Andromeda environment. In this way, Andromeda stands out for being an extra layer built on the base of Hexagonix, with graphics resources, a graphics library and utilities that work on top of Hexagonix and extend its function. This built environment was named the Andromeda environment. To meet different needs, the two distributions will always be maintained. Both versions are functional and can be used depending on the desired end use. In summary, both Hexagonix and Andromeda are Hexagon kernel distributions, differing in the components included.

To better understand this distribution model, a suitable example would be what happens with macOS (Apple)[^5]. macOS is a Unix-like operating system built on top of Darwin, a free operating system composed of the XNU kernel, libraries and utilities, adding the Aqua GUI and other applications and utilities developed by Apple and other vendors on top of Darwin. The Darwin environment is easily accessed and observed through macOS, such as using the terminal, for example. Darwin is a complete and functional system, but it lacks some graphical features, for example, which are only distributed together with macOS. In this analogy, we have macOS as Andromeda and Darwin as Hexagonix.

[^5]: You can get more information about the relationship between Darwin and macOS [here](https://en.wikipedia.org/wiki/Darwin_(operating_system)).

## And the source code?

The project's source code is not yet publicly available, but there are plans to make it available in the future. However, distribution of disk images with both Hexagonix and Andromeda is free. Please note the [license](LICENSE) available in this repository for more information.

## What is an operational system?

The Hexagonix/Andromeda Operating System is a collection of software pieces that manage the hardware of the computer where it is installed, allowing the loading and operation of applications and communication between the different devices connected to the device. It is composed of several components, which act in the computer boot process, resource testing and loading of the operating system kernel (core), the kernel, a user interaction interface and a series of utilities.
Both hexagonix and Andromeda are distributions that incorporate a Unix-like kernel, called Hexagon, support libraries, utilities developed exclusively for the Andromeda environment, and Unix-like command-line utilities (the latter and the Hexagon kernel itself are already there configure a base operating system, Hexagonix).

## The Hexagonix/Andromeda history:

Andromeda started as a structured implementation similar to DOS-like systems, with an interpreter with built-in commands with names, syntaxes and results similar to a generic DOS. The command interpreter had file manipulation and other commands internally, as in conventional DOS systems. Disk drives were also defined as letters. Later, there was a growing interest and fascination in the functioning of Unix systems and all the code was rewritten or adapted to make the System kernel a Unix-like kernel. All System components, just like in DOS, were kept in a single tree until then. With version 1.5 of Andromeda, codenamed "Unix-like", the kernel has been heavily modified and rewritten to suit the Unix philosophy. Changes even included the way devices were handled, with writing a hardware abstraction layer with managing devices as files, as well as adding system calls open(), close(), write() and read(). The base Unix utilities were also written, with the removal of commands from the standard interpreter, which was rewritten to make way for a Unix-like shell. The internal commands were moved to the utilities, which now have a Unix-style structure and syntax. The rest of the utilities, such as mount, were written, already taking advantage of the open() call, which is also used to mount volume, in addition to opening ordinary files on the volume. The open() call is also used to start other peripherals such as serial and parallel ports. The write() call also works with devices and files as well as close(). A VFS (Virtual File System) was also introduced, which in the future will support various file systems and makes file management transparent to the System, programmers and users. Also included are new hardware management functions and many improvements and bug fixes. The System gains new Unix utilities to date. After this change in proposal and architecture, the components were separated and allocated to specific projects. The union of these components forms the operating system. In the case of Hexagonix, we have HBoot, Hexagon, shell, Unix libraries and applications, while Andromeda extends Hexagonix, incorporating other libraries and applications that use them.

## Hexagonix/Andromeda versioning:

The operating system features version numbering independent of the associated components. Each component, from the boot loader to a simple utility, is given an independent version number that reflects its development status. A Hexagonix/Andromeda version number has three sets of numbers divided into three blocks separated by a period character ".". The first one represents the major version number and is based on number one. The second number refers to the release, this is the number that varies from one Hexagonix/Andromeda release to another and distinguishes between the major versions of the System, in addition to being used as a version number that is checked by applications and utilities to verify whether the system version meets the minimum requirements for running the software. The third is the revision number of each major release and, if it is 0, it can be omitted, leaving the version with only two digit blocks. An example would be versions "1.14.4", whose base version is always 1, so far, 14 indicates the release (this refers, most of the time, to the actual version of the System. Think, for example, of the system of numbering Apple with Mac OS X/OS X/macOS up to version 11.0 Big Sur, which always starts with 10 and is followed by the release and revision number). Number 4, on the other hand, would be the revision within the major release, which concerns fixing bugs and adding some functionality that does not profoundly change the System or its use.

Normally, Hexagonix and Andromeda have the same major version numbering, but this is not necessarily mandatory. Version numbers may differ at some point, as well as the components of each distribution. The Hexagon version, for example, can be different even with identical version numbers, but this kind of divergence will always be avoided.

# System components

## Saturn

The first component of Hexagonix/Andromeda is Saturn. It is responsible for taking control of the boot process performed by the BIOS/UEFI and searching the volume for the second boot stage. For that, it implements a driver for reading a FAT16 file system. The second boot stage (see below) can implement drivers for other file systems and is responsible for finding Hexagon, loading HBoot modules or loading a DOS compatible system (BETA).

## Hexagon Boot (HBoot)

Hexagon Boot (HBoot) is a component designed to allow booting of the Hexagon kernel. Until then, initialization was performed by just one stage, which defined a very basic environment, loaded the Hexagon into memory, and immediately passed control to it, providing a very small and limited set of parameters, since the code for that stage stays restricted to 512 bytes, which limits the performance of several tests and data processing. With HBoot, it was possible to expand the number of tasks performed before the Hexagon runs, as well as the possibility to provide more information regarding the machine and boot environment. This is particularly important to allow the creation of a device tree that Hexagon can use to decide how to handle each identified device. HBoot is able to check which disk drives are available on the machine, emit a boot tone, obtain the amount of available RAM memory installed and allow or disallow the boot process to proceed according to this information. If no user interaction is detected 3 seconds after all essential tests and activities to create a boot environment for Hexagon, the system will load and run Hexagon (present in a file in the volume named **HEXAGON.SIS**** ) being unloaded from memory. The interaction with HBoot is done by pressing the F8 key after the respective message appears on the screen.

### Other functions

* HBoot allows loading modules in HBoot format, which may be useful in the future to allow for hardware tests such as memory and disk tests if the modules are available on disk. Modules can also be used to extend HBoot's functions. The format specification is now available and an example can be found below. These modules can be used to test specific devices, obtain hardware information, or load files into file systems not originally supported by HBoot.
* In the context of Hexagonix development, HBoot can also load directly, from a currently built-in module (this function will be moved to a standalone module as soon as possible) the core of the FreeDOS open source operating system[^6] , so that established and robust utility tools that run in a DOS environment can run on the Hexagonix/Andromeda volume and files. FreeDOS was chosen because of its feature of a kernel composed of a single file, usually "KERNEL.SYS"[^7], in addition to its free and free distribution. On the other hand, other DOS, such as MS-DOS, prior to version 7.0, use two files that must be contiguous on the disk, and this is not possible here, since the installation of FreeDOS already takes place on a Hexagonix volume, with the kernel copy , command interpreter and other DOS utilities, the main operating system being Hexagonix/Andromeda, with optional launching of FreeDOS for some special activity[^8]. If the FreeDOS system components are not present on the disk (the copy of FreeDOS files is not part of the default image), booting into DOS compatibility mode will not occur.

[^6]: You can find the project page [here](https://www.freedos.org/).
[^7]: Booting in DOS mode was possible after searching the FreeDOS documentation, especially the "SYS.C" file (which can be found [here](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/2043/), which indicates in which segment the kernel expects to be loaded and which parameters are needed. Each DOS system has a preferred loading segment and this loading of other DOS editions can be implemented in the future with the help of HBoot modules. All code for core loading was developed from scratch and is not based on any existing ones.
[^8]: Booting in DOS compatibility mode of HBoot can be useful for running volume error checking, volume defragmenting, partitioner and other diagnostic tools, as well as development tools such as non-compilers and assemblers. supported by Hexagonix/Andromeda (the 16-bit tools, for example).

### HBoot Module Example

Below you can find an example of HBoot module implementation:

```assembly
;;**************************************************** ***********************************
;;
;;
;; HBoot Module
;;
;; Hexagon® Boot - HBoot
;;
;; Copyright © 2020-2021 Felipe Miguel Nery Lunkes
;; All rights reserved
;;
;;**************************************************** ***********************************

use16

;; The module must have a special HBoot image header
;; There are 6 bytes, with signature (magic number) and target architecture

HBootHeader:

.signature:    db "HBOOT" ;; Signature, 5 bytes
.architecture: db 01h     ;; Architecture (i386), 1 byte

;; Configure stack and pointer

    cli;; Disable interrupts
    
    mov ax, 0x2000 ;; Define stack registers here
    mov ss, ax
    mov sp, 0
    
    sti;; Enable interrupts
     
    clc

    mov ax, 0x2000 ;; Define segment registers here
    mov ds, ax
    mov es, ax
    
    sti;; Enable interrupts

;; Your code here

```

### Supported file systems

* FAT16B
* FAT12 (under development)

New file systems will be implemented in the future.

### Report bugs

HBoot has gained a lot of complexity since the beginning of its development in 2020. Due to this increase in code and the nature of its operation (16-bit), bugs can be found. They can be reported in the repository or by email, available at the end of this file.

## Kernel Hexagon

### What is it

Hexagon is a monolithic kernel (kernel) running in 32-bit protected mode, developed with the PC architecture (x86) in mind. It is a kernel written from scratch, aiming for the speed and compatibility of modern hardware but also being able to run on older hardware. For the moment, it guarantees a single-user environment, despite the use of virtual terminals, and monotasking, despite the ability to load, keep in memory and control more than one process, in a chronologically-ordered execution stack. In the future, the kernel will be able to support the execution of multiple processes in preemptive multitasking. Hexagon is a Unix-like kernel and forms the basis of the Hexagonix/Andromeda Operating System, although independent of it. It runs executable images in HAPP format, developed for Hexagon. It implements a very sophisticated API accessible via a system call.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/LogoHexagon.png" width="250" height="250">
</p>

### History

The kernel was initially designed and written aiming at a structure and functioning similar to DOS (Disk Operating System) systems, such as MS-DOS, in the year 2015 to 2017. Therefore, many system calls and device names followed a syntax and names FROM. Over time, there was an interest in bringing the then core of Andromeda, which at that time did not have a name and was kept with the distribution code, to a structure and operation closer to Unix-like systems, such as BSD or Linux , for example. In this way, many parts of the kernel were redeployed with the new goal in mind. The core code was separated from the rest of the System and became independent, in terms of development as well as functioning, in addition to gaining a name, Hexagon. A hardware abstraction layer was written with the inclusion of system calls known in the Unix world, such as open(), close(), read() and write(). Devices were named and disk drives were changed from DOS naming to Unix device names. The kernel then goes through a known boot process, with the execution, with PID 1, of the user's first process, init, which then loads the rest of the components. Unix-like utilities were then written that used the kernel's Unix-like API, and several Unix-like tools have been written since then (2017 onwards).

### The HAPP executable format

The HAPP executable image format was developed for Hexagon to allow the development of images that can be verified and validated for architecture and minimum kernel versions necessary for correct execution. The header also stores important information, allowing the developer to directly add an entry point, regardless of where it is inside the image, something that would have been redirected earlier when the executable image was in pure binary format. The HAPP image also allows you to validate that the image to be loaded is really an executable image, thus preventing unsupported files from being executed, even if they are not even executable files. It also allows the system to check code dependencies, such as the aforementioned architecture, as well as Hexagon version numbers, which must be equal to or greater than the minimum specified by the header. All HAPP images must have this complete header, including reserved sessions, in order to function correctly in later versions of the System. HAPP images are always 32-bit.

In assembly language, the system development language, the header, in its 2.0 specification:

```assembly
APPHeader:

.signature:          db "HAPP" ;; Signature
.architecture:       db 01h ;; Architecture (i386 = 01h)
.Minimum Version:    db 8 ;; Minimal version of Hexagon
.Minimum subversion: db 40 ;; Minimal Hexagon Subversion
.entrypoint:         dd ;; Input point offset (reference to main function here)
.ImageType:          db 01h ;; Executable image type (executable = 01h)
.reserved0:          dd 0 ;; Reserved (Dword)
.reserved1:          db 0 ;; Reserved (Byte)
.reserved2:          db 0 ;; Reserved (Byte)
.reserved3:          db 0 ;; Reserved (Byte)
.reserved4:          dd 0 ;; Reserved (Dword)
.reserved5:          dd 0 ;; Reserved (Dword)
.reserved6:          dd 0 ;; Reserved (Dword)
.reserved7:          db 0 ;; Reserved (Byte)
.reserved8:          dw 0 ;; Reserved (Word)
.reserved9:          dw 0 ;; Reserved (Word)
.reserved10:         dw 0 ;; Reserved (Word)
```

Below is an implementation of a small application written as an example, which uses the Hexagon header and system calls, written in x86 assembly language in Intel syntax and assembled with the aid of a flat assembler (FASM). This app sends a message to the terminal and then exits.

```assembly
;; This is a template for building a text mode app for
;; the Hexagonix/Andromeda!
;;
;; Written by Felipe Miguel Nery Lunkes on 12/04/2020
;;
;; You can generate an executable HAPP image using the assembler
;; FASM. To do this, use the command line below:
;;
;; fasmX tapp.asm
;; or
;; fasmX tapp.asm tapp.app

use32

APPHeader:

.signature:          db "HAPP" ;; Signature
.architecture:       db 01h ;; Architecture (i386 = 01h)
.Minimum Version:    db 8 ;; Minimal version of Hexagon
.Minimum subversion: db 40 ;; Minimal Hexagon Subversion
.Entrypoint:         dd startAPP ;; Input point offset
.ImageType:          db 01h ;; executable image
.reserved0:          dd 0 ;; Reserved (Dword)
.reserved1:          db 0 ;; Reserved (Byte)
.reserved2:          db 0 ;; Reserved (Byte)
.reserved3:          db 0 ;; Reserved (Byte)
.reserved4:          dd 0 ;; Reserved (Dword)
.reserved5:          dd 0 ;; Reserved (Dword)
.reserved6:          dd 0 ;; Reserved (Dword)
.reserved7:          db 0 ;; Reserved (Byte)
.reserved8:          dw 0 ;; Reserved (Word)
.reserved9:          dw 0 ;; Reserved (Word)
.reserved10:         dw 0 ;; Reserved (Word)

;;**************************************************** *************

include "andrmda.s" ;; Include system calls

;;**************************************************** *************

;; Variables and constants

msg: db 10, 10, "This is a template with a simple HAPP application example!", 10, 0

;;**************************************************** *************

;; entry point

startAPP:

    mov esi, msg

    printString ;; Here we have a macro that configures and calls an API function.

    Andromeda terminateProcess ;; Another macro that asks which call to make
```

More detailed Hexagon documentation will be made available in the future.

## Hexagonix environment:

Hexagonix implements, together with Hexagon, a series of Unix-like utilities, with functionality and syntax similar to UNIX and Unix-like systems. **Utilities such as init, login, sh, top, ps, cp, rm, cat, clear, man, and more are included in the standard Hexagonix distribution**. These utilities make up the base Hexagonix utility package. The login and user mode environment startup tools are in this package, as well as several configuration files for this environment. These utilities generally don't have a graphical interface, just a command line interface (CLI). However, they can be requested by applications that have a graphical interface. This environment is available in both the [Hexagonix](en.hexagonix.img) distribution and the [Andromeda](en.andromeda.img) distribution.

### Some applications and utilities in the Hexagonix environment

Hexagonix includes many of the Unix utilities that you may already be familiar with, for example:

* init
* Login
* ls
* cat
* cp
* rm
* clear
* top
* ps
* man
* su
* sh (default shell)
* uname
* whoami, among others.

### Third Party Applications Available for Hexagonix

* [Flat Assembler (fasm)](https://flatassembler.net/index.php)

Hexagonix received an assembler port [Fasm](https://flatassembler.net/index.php), which was adapted for Hexagonix, allowing the user to develop applications directly on the system. Changes added to the code, as well as the software license, can be found in the [fasm repository for Hexagonix](https://github.com/hexagonix/fasm). This repository is a fork of the [original repository](https://github.com/tgrysztar/fasm). Added code is based on modifications made to the original code and copyright additions. This modified/authored code can be found in the repository, [by clicking here](https://github.com/hexagonix/fasm/tree/master/SOURCE/HEXAGONIX).

## Andromeda Environment:

The Andromeda environment is built on the solid foundation provided by Hexagonix, including applications and utilities that either don't implement the Unix philosophy or have quite different syntax and usage than you'd expect from a Unix environment. As such, they are separated as **Andromeda apps**, and are not part of the standard Hexagonix distribution. Here are the System settings app, calculator, font manager, text editors and the IDE developed for Andromeda. These utilities may or may not have a graphical interface. Together with them, the Andromeda environment comprises libraries developed to allow the development of applications, such as the **Stellar** library. This environment is only available in the [Andromeda](en.andromeda.img) distribution.

### Some apps and utilities from the Andromeda environment

* System Settings (Config)
* Quartz text editor
* Lyoko IDE for application development
* Electronic Piano return Piano;
* Serial communication utility
* Andromeda Shell (ASH) - A new shell for Andromeda
* Andromeda Calculator
* Font change utility
* Andromeda shutdown utility

### Third-party apps available for Andromeda

There are no third-party applications available for the Andromeda environment yet. If interested, you can build the first one!

## Hexagonix fonts:

The default Hexagonix installation also provides a number of fonts that can be loaded by the settings application or font utility (font manager). These files are used to change the graphic mode display font of Hexagonix and Andromeda.

# System development libraries:

Hexagonix/Andromeda also provides functions that must be used to interact with the system environment itself. Libraries are used to access functions implemented by Hexagon or by the libraries themselves, allowing easy development of applications and utilities for both the Hexagonix and Andromeda environments. Libraries implement functions for displaying text, math calculations, sending messages, opening files and devices, and much more. The base library (andrmda.s or hexagonix.s) provides accessible functions for both possible distribution environments, while other libraries may be unique to the Andromeda environment. These libraries include graphical functions to build interfaces in graphical mode (Andromeda), as well as functions to check the version of the system currently running (Hexagonix and Andromeda). The Hexagonix base utilities perform a Hexagon version check to see if they can be run using the Unix uname utility or directly via a Hexagon system call.

# A little bit about system startup:

After booting the firmware, the [BIOS](https://en.wikipedia.org/wiki/BIOS) or other firmware, such as [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) in legacy mode, performs fetches a volume/disk marked bootable and, when found, loads the first sector to address 0x7C00. In the case of a Hexagon volume, the component named Saturn is located in the first sector of the volume. Saturn is the MBR boot manager of a Hexagon volume and acts as the first stage in the System load chain. It performs the search, in the volume, of the second stage, much more robust, the Hexagon Boot (HBoot). HBoot does not have the same limitations as the previous component, as it is not restricted to 512-byte size. When starting, HBoot performs a series of machine tests and diagnostics, checking which disks/volumes are available on the machine, how much RAM memory is installed and initializing some peripherals, such as serial ports, in addition to checking the installed processor for its ability to run Hexagon. If the amount of RAM memory installed is less than the minimum, the processor is not supported or an error occurs in an essential peripheral, the initialization protocol is canceled. If the tests are successful, the volume is searched for the file containing the Hexagon kernel, with its loading, construction of a parameter structure, configuration of registers with basic hardware information and subsequent execution. HBoot is also capable of loading and executing modules in the HBoot format, as well as booting a DOS-like system whose files are present on the Hexagon volume (so far, only FreeDOS is supported). It is also capable of performing some hardware tests on demand, such as sound and graphics. After loading the Hexagon, the kernel takes control of the device and performs peripheral configuration, builds internal control structures and starts the first user process, with PID 1, usually the System Initiator, or init. init will read the configuration file "INIT.UNX" from the volume and start the services described there, usually the Login and User Manager, or simply login. This, in turn, fetches the information in "USER.UNX" and compares it with the user's entries, and if the credentials are valid, starts the first shell or utility described in the user's entry. Afterwards, Hexagon goes into administrative mode and manages requests from applications and peripherals, exposing the API for building and executing the other components of the System (for more information, see the header file "ANDRMDA.S", which already documents the API).

# How to test Hexagonix or Andromeda:

## System requirements

### Minimum requirements

* Processor: Pentium III (1999) with SSE and MMX support or newer;
* RAM memory: 32 Mb minimum (a minimum installation with 32 Mb is usually sufficient in most cases);
* Hard disk: IDE or SATA hard disk with a minimum of 50 Mb;
* Necessary peripherals:
  - Serial port (1-4);
  - Parallel port (1-4);
  - PS/2 or USB keyboard;
  - VGA video card with 2 Mb video memory (with color support).

### Recommended

* Processor: Pentium D or newer;
* RAM memory: 50 Mb;
* Optional peripherals:
  - PS/2 or USB mouse;
  - Video card with > 2 Mb of video memory.

## Get disk images with system installation

To test Hexagonix or Andromeda, you will need one of the disk images available in this repository, as well as the [qemu](https://www.qemu.org) tool installed on your computer. The image can also be used for writing to a physical disk on a real machine.

To test Hexagonix, get the ['en.hexagonix.img'](en.hexagonix.img) file from this repository.
To test Andromeda, get the ['en.andromeda.img'](en.andromeda.img) file from this repository.

## For testing in a virtualized environment

You must provide at least 32 MB of RAM for the virtual machine. Typically, the command line below fulfills all requirements for running the system:

```
qemu-system-i386 -hda en.andromeda.img -m 32 -soundhw pcspk
qemu-system-i386 -hda en.hexagonix.img -m 32 -soundhw pcspk
```

Remembering that you must use a qemu version/edition that can run software written for the x86 architecture. To download and install qemu, click [here](https://www.qemu.org/download/).

## For physical machine testing

You must use Linux/macOS or some Windows tool that allows you to burn this image to disk.

On Linux/macOS/Unix, use the line below:

```
dd if=en.andromeda.img of=/dev/unit
```
where unit equals the desired device. Restart your computer and test the system. Keep in mind that secure boot mode is not supported, and booting is only supported in BIOS or UEFI BIOS legacy mode.

## First use

When starting the system, you will be asked to enter a username and password. For first use, use

```
Username: root
Password: root
```

You can add another user by changing the 'USUARIO.UNX' file in the root of the disk. Remember not to remove the root user. This can make the system permanently inoperable.

# System screenshots

## Hexagonix

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix1.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix2.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix3.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix4.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix5.png" width="400" height="300">
</p>

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

## Andromeda

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda1.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda2.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda3.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda4.png" width="400" height="300">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda5.png" width="400" height="300">
</p>

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

# Languages

At the moment, both the system and the documentation are only available in Portuguese. Documentation in English will be available soon, and there are plans to support English as a primary language possibility in addition to Portuguese (much of the work has already been done).

# Inspiration

This project was possible and today it can see the light of day thanks to many others who have come before and contributed with design ideas and teaching how an operating system, even a simple one, should work. Are they:

* MS-DOS, with code available [here](https://github.com/microsoft/MS-DOS)
* [MikeOS](http://mikeos.sourceforge.net/)
* [Linux 0.1.1](https://kernel.org)
* [FreeBSD](https://www.freebsd.org/)
* [XNU/Darwin](https://github.com/apple/darwin-xnu)
* [LittleKernel](https://github.com/littlekernel/lk)
* [Google Fuchsia](https://fuchsia.googlesource.com/fuchsia/)

In addition, other projects have helped in the development of Hexagonix/Andromeda, either by providing new design ideas that go beyond the traditional organization of an operating system, or by providing well-documented code that allows us to understand the functioning of certain parts of an operating system, or by contributing with code examples that later came to inspire functions that were written exclusively for Hexagonix/Andromeda (mainly kernel code). Despite not having been copied, the code of these projects made it possible for the functioning of certain computer components to be understood, opening doors for author codes to be written based on the study of the code of these projects. Are they:

* [Snowdrop OS](http://www.sebastianmihai.com/snowdrop/), which supported 16-bit functions available on HBoot
* [Alotware](https://github.com/0x5CE/alotware), which inspired me to create the process management functions in early versions of Hexagon (now rewritten countless times)

# Author & Contact

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)

Feel free to contact me, report bugs or be interested in participating in the project.

## Email:

* hexagonixdev@gmail.com (PT/EN)
* felipemiguel_nery@hotmail.com (PT/EN)

## Social networks:

* [Twitter](https://twitter.com/redLipes)

Copyright © 2021 Felipe Miguel Nery Lunkes