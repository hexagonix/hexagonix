<!--

Version of this file: 5.0

Copyright © 2021-2022 Felipe Miguel Nery Lunkes
All rights reserved.

-->

# Hexagonix/Andromeda Operating System

# First of all - a shortcut to get straight to the point

<details title="License" align='left'>
<br>
<summary align='left'><strong>License</strong></summary>

Hexagonix Operating System

BSD 3-Clause License

Copyright (c) 2015-2022, Felipe Miguel Nery Lunkes
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

</details>

<details title="Download and test the system right now" align='left'>
<br>
<summary align='left'><strong>Download and test the system right now</strong></summary>

At [end of this file](https://github.com/hexagonix/hexagonix/blob/main/README.pt.md#como-testar-o-hexagonix-ou-o-andromeda) you will find a tutorial to run the Hexagonix/Andromeda on your computer, either in a virtualized or native version. Remember that it is necessary to have an x86 architecture computer or an emulator, if you are using a device of another architecture for testing.

You can go to the [releases](https://github.com/hexagonix/hexagonix/releases) session for stable system releases. You can access the Hexagonix/Andromeda [release announcement](REL.en.md) file. Whenever possible, get the latest release and download the available .img images or the complete package in zip format. The versions available directly in this repository are always development versions (beta and release candidate), which can also be run and are minimally functional. At the end of each development cycle, the final versions will be available in the [releases](https://github.com/hexagonix/hexagonix/releases) session.

</details>

<details title="System documentation" align='left'>
<br>
<summary align='left'><strong>System documentation</strong></summary>

* [System Documentation (under construction)](https://github.com/hexagonix/Doc)

</details>

<details title="Help with the development of Hexagonix/Andromeda" align='left'>
<br>
<summary align='left'><strong>Help with the development of Hexagonix/Andromeda</strong></summary>

If you have knowledge of writing x86 assembly code and would like to help develop the system, feel free to send me an email! See [here](https://github.com/hexagonix/hexagonix/blob/main/README.en.md#author--contact) how to contact me!

</details>

<details title="Report system errors" align='left'>
<br>
<summary align='left'><strong>Report system errors</strong></summary>

You can report system errors [here](https://github.com/hexagonix/hexagonix/blob/main/README.en.md#reportar-errors).

</details>

<hr>

# About the system

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix.png" width="250" height="250">
</p>

<details title="Development" align='left'>
<br>
<summary align='left'><strong>Development</strong></summary>

Hexagonix/Andromeda and all its components have been developed since 2015 and were written completely in Assembly language.

</details>

<details title="Why two names? Hexagonix and Andromeda, what are they?" align='left'>
<br>
<summary align='left'><strong>Why two names? Hexagonix and Andromeda, what are they?</strong></summary>

In the beginning, Andromeda was intended to be a complete operating system, composed of the kernel, libraries, graphical and text interface and utilities. Later, with the passage of time and the change in approach to the architecture and objectives of the system, the components were separated and became independent projects in terms of functioning, organization and development. As you will see below, the Andromeda core was separated from the rest of the Andromeda code tree, becoming an independent project, even given a name, Hexagon. From then on, the idea arose of making the composition of the system more flexible and allowing the development of distributions, as in GNU/Linux. In this way, distributions of Hexagon could be created, grouping the necessary components for the basic functioning (Hexagonix) and allowing the extension of the system if necessary, with new components, modules and utilities, being the userland defined in each case. With the change of architecture of the system itself, with the core approaching a Unix-like architecture, new utilities in Unix style and syntax were developed and kept separate, in another project. From the original Andromeda project we have the Andromeda-specific applications and graphics libraries. A base system was then created, which by itself can already be fully executed, and became the base of Andromeda. This base system is called Hexagonix, and it consists of the HBoot boot loader, the Hexagon kernel, the shell, Unix environment libraries (here called Hexagonix environment) and Unix utilities. This system is fully functional, but lacks graphical resources and applications developed for the Andromeda environment. In this way, Andromeda stands out for being one more layer built on top of Hexagonix, with graphics resources, a graphics library and utilities that work on top of Hexagonix and extend its function. This built environment was named the Andromeda environment. To meet different needs, the two distributions will always be kept. Both versions are functional and can be used depending on the desired end use. In summary, both Hexagonix and Andromeda are distributions of the Hexagon kernel, differing in the components included.

To better understand this distribution model, a suitable example would be what happens with macOS (Apple)[^1]. macOS is a Unix-like operating system built on top of Darwin, a free operating system composed of the XNU kernel, libraries and utilities, adding on top of Darwin the Aqua graphical interface and other applications and utilities developed by Apple and other vendors. The Darwin environment is easily accessed and observed through macOS, such as using the terminal, for example. Darwin is a complete and functional system, but it lacks some graphical resources, for example, which are only distributed together with macOS. In this analogy, we have macOS as Andromeda and Darwin as Hexagonix.

</details>

<details title="What about the source code?" align='left'>
<br>
<summary align='left'><strong>What about the source code?</strong></summary>

The project's source code has now been made publicly available. The kernel code and Unix-like utilities and Andromeda applications are available, as well as the source package that makes up HBoot. Disk images with both Hexagonix and Andromeda are now available and free to distribute. Please note the [license](LICENSE) available in this repository for more information. It is worth mentioning that the license of each code package that makes up the system (Hexagon, HBoot, Hexagonix utilities, Andromeda utilities, fonts and other components) may vary. Each package can be released with a different license type (like GPL, MIT or BSD, for example). Keep an eye on each license in the respective repositories. Components that are not available in the official repository are still closed source, governed by a proprietary Hexagonix license, which can be found [here](https://github.com/hexagonix/Doc/blob/main/LICENSES/Hexagonix ).

</details>

<details title="The Hexagonix/Andromeda story" align='left'>
<br>
<summary align='left'><strong>The Hexagonix/Andromeda story</strong></summary>

Andromeda started as an implementation in a structure similar to DOS-like systems, with an interpreter with built-in commands with names, syntax and results similar to a generic DOS. The command interpreter presented file manipulation and other commands internally, as in conventional DOS systems. Disk drives were also defined as letters. Later, there was a growing interest and fascination in the functioning of Unix systems and all the code was rewritten or adapted to make the System kernel a Unix-like kernel. All System components, as in DOS, were kept in a single tree until then. With Andromeda version 1.5, codenamed "Unix-like", the kernel has been heavily modified and rewritten to fit the Unix philosophy. Changes even included the way devices were handled, writing a hardware abstraction layer managing devices as files, and adding open(), close(), write() and to read(). The Unix-based utilities were also written, removing commands from the default interpreter, which was rewritten to make way for a Unix-like shell. The internal commands were moved to the utilities, which now have a Unix-style structure and syntax. The rest of the utilities, such as mount, were written already taking advantage of the open() call, which is also used to mount volume, in addition to opening ordinary files from the volume. The open() call is also used to start other peripherals such as serial and parallel ports. The write() call also works with devices and files, as well as close(). A VFS (Virtual File System) was also introduced, which will support multiple file systems in the future and make file management transparent to the System, programmers and users. Also included are new hardware management functions and many improvements and bug fixes. The System gains new Unix utilities until the present moment. After this change in the proposal and architecture, the components were separated and allocated to specific projects. The union of these components forms the operating system. In the case of Hexagonix, we have HBoot, Hexagon, shell, Unix libraries and applications, while Andromeda extends Hexagonix, incorporating other libraries and applications that use them.

</details>

<hr>

# System components

<details title="Saturno" align='left'>
<br>
<summary align='left'><strong>Saturno</strong></summary>

The first component of Hexagonix/Andromeda is Saturno. It is responsible for taking control of the boot process performed by the BIOS/UEFI and looking in the volume for the second boot stage. For that, it implements a driver for reading a FAT16 file system. The second boot stage (see below) can implement drivers for other filesystems and is responsible for finding Hexagon, loading HBoot modules or loading a compatible DOS-like system (BETA version).

</details>

<details title="Hexagon Boot (HBoot)" align='left'>
<br>
<summary align='left'><strong>Hexagon Boot (HBoot)</strong></summary>

Hexagon Boot (HBoot) is a component designed to allow the Hexagon kernel to boot. Until then, initialization was performed by just one stage, which defined a very basic environment, loaded Hexagon into memory and immediately executed it, providing a very limited set of parameters. This is due to the fact that the code of this stage is restricted to 512 bytes, which limits the performance of several tests and data processing. With HBoot, it was possible to expand the number of tasks performed before running Hexagon, as well as the possibility to provide more information about the device and boot environment. This is particularly important to allow the creation of a device tree that Hexagon can use to decide how to handle each identified device. HBoot is able to check which disk drives are available on the machine, emit a boot tone, obtain the amount of available RAM memory installed and allow or not to proceed with the boot process according to this information. If no user interaction is detected (within 3 seconds after HBoot is started and messages are displayed to the user), HBoot will perform additional tests to verify the device's ability to run the system and will load and run Hexagon (present in a file on the volume named **HEXAGON.SIS**). After loading, HBoot transfers control to Hexagon, which is initialized and stores the data provided by HBoot in the kernel environment.

### How to interact with HBoot

Interaction with HBoot takes place by pressing the F8 key after booting and displaying messages on the screen. HBoot waits for 3 seconds for any interaction and, if none has occurred, it continues executing the boot protocol. The interaction with HBoot can be interesting to load modules in the HBoot format, provide boot parameters to Hexagon, load a DOS-type system whose files are present on the same volume or even load HAPP images from other cores (if the developer wants to use the HBoot implementation in your project). Below, see some more details of additional and diagnostic functions that can be performed via interaction with HBoot before loading Hexagonix.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/HBoot.png" width="600" height="500">
</p>

### Other functions available (HBot and modDOS modules)

#### HBoot Modules

HBoot allows loading modules in HBoot format, which may be useful in the future to allow hardware tests such as memory and disk tests if modules are available on disk. Modules can also be used to extend HBoot functions. The format specification is now available and an example can be found below. These modules can be used to test specific devices, obtain hardware information, or load files into file systems not originally supported by HBoot.

##### HBoot modules already implemented

HBoot modules have been developed to extend the functionality of HBoot. So far these are:

* Spartan: model implementation of an HBoot module. Displays a message on the screen and prompts the user to press any key to restart the computer and launch Hexagonix.
* x86-Detect: Computer hardware initialization and diagnostics module. This module detects available storage drives, checks for minimum computer requirements for running Hexagon (such as RAM and processor), detects and initializes serial and parallel ports, and displays to the user whether or not the device can run Hexagonix. In the future, it will be used to find other installed operating systems, perform RAM and disk performance tests, and find and configure PCI devices. A quickboot entry for x86-Detect can be permanently added to HBoot, for easier execution with fewer steps.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/x86-Detect.png" width="600" height="500">
</p>

#### Load a DOS-like operating system with modDOS

In the context of Hexagonix development, HBoot can also load and run the FreeDOS[^2] open source operating system core, so that established and robust utility tools that run in a DOS environment can run on top of the volume and files. Hexagonix/Andromeda. This function is performed by an HBoot module (modDOS) which, until now, has been integrated into HBoot as a module library, already containing all the necessary structure to be an independent module. Going forward, the plan is for this library/module to be removed from HBoot and kept as a separate module, removing complexity and code from HBoot. For performance, at this point, modDOS is still kept in the HBoot source tree. FreeDOS was chosen because of several interesting features that facilitate the necessary implementation in modDOS. Firstly, the system kernel is contained in a single file, usually "KERNEL.SYS"[^3] (although in the context of modDOS, the filename is not important, as it will not be booted by the project initiator FreeDOS, which hopes to find a file with that name), in addition to its free distribution. On the other hand, other DOS-type systems, such as MS-DOS (especially in its version prior to 7.0), can use more than one file on the disk, as well as requiring these files to be in defined locations and to be contiguous on the disk. This defined location requirement cannot be satisfied here, as the installation of a copy of the DOS system takes place already on a Hexagonix partition. Installing a DOS system is optional and modDOS makes running this type of system easier, requiring only a copy of the kernel, command interpreter and other utilities desired on a Hexagonix partition. Furthermore, using a free distribution system removes any licensing issues. Installing a DOS system together with Hexagonix/Andromeda allows DOS tools to be used to perform specific tasks in this environment or to add functions and utilities that are not yet available or finished for use in Hexagonix, such as a disk partitioning utility, for example. example [^4]. If the FreeDOS system components are not present on the disk (copying the FreeDOS files is not part of the standard installation and image), booting in DOS compatibility mode will not occur.

### HBoot module example

Below you can find an example implementation of the HBoot module (HBoot module specification v2.0):

```assembly
;;*************************************************************************************
;;
;;
;; HBoot module
;;
;; Hexagon® Boot - HBoot
;;
;; Copyright © 2020-2022 Felipe Miguel Nery Lunkes
;; All rights reserved
;;
;;*************************************************************************************

use16

;; The module must have a special HBoot image header
;; It's 6 bytes, with signature (magic number) and target architecture

headerHBoot:

.signature: db "HBOOT" ;; Signature, 5 bytes
.architecture: db 01h ;; Architecture (i386), 1 byte
.Modversion: db 01h ;; Version, with 1 byte
.subverMod: db 00h ;; Subversion, with 1 byte
.modname: db "NAME " ;; Module name, 8 bytes

;; Configure stack and pointer

    cli ;; disable interrupts
    
    mov ax, 0x2000 ;; Define stack registers here
    mov ss, ax
    mov sp, 0
    
    sti;; enable interrupts
     
    clc

    mov ax, 0x2000 ;; Define segment registers here
    mov ds, ax
    move es, ax
    
    sti;; Enable interrupts

;; your code here

```

### Supported file systems

* FAT16B
* FAT12 (under development)

New file systems will be implemented in the future, including their support through HBoot modules.

### Report bugs

HBoot has gained a lot of complexity since the beginning of its development in 2020. Due to this increase in code and the nature of its operation (16-bit), bugs can be found. They can be reported in the repository or by email, available at the end of this file.

</details>

<details title="Hexagon kernel" align='left'>
<br>
<summary align='left'><strong>Hexagon kernel</strong></summary>

### Which is

Hexagon is a monolithic kernel running in 32-bit protected mode, designed with the PC architecture in mind (x86). It's a kernel written from scratch, aiming for the speed and compatibility of modern hardware but also being able to run on older hardware (like a Pentium III). At the moment, it guarantees a single-user environment, despite the use of virtual terminals, and single-tasking, despite the ability to load, keep in memory and control more than one process, in an execution stack. In the future, the kernel may support running multiple processes in preemptive multitasking. Hexagon is a Unix-like kernel and tries to implement POSIX compatibility, although far from it, and forms the basis of the Hexagonix/Andromeda Operating System, although independent of it. It runs executable images in the HAPP format, developed exclusively for Hexagon. Hexagon also implements a very sophisticated API accessible through a system call.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/LogoHexagon.png" width="250" height="250">
</p>

### History

The kernel was initially designed and written aiming at a structure and operation close to DOS (Disk Operating System) systems, such as MS-DOS, in the years 2015 to 2017. Therefore, many system calls and device names followed a syntax and names FROM. Over time, there was an interest in bringing the then core of Andromeda, which at that time had no name and was kept together with the distribution's code, closer to a structure and functioning closer to Unix-like systems, such as BSD or Linux. , for example. In this way, many parts of the kernel were re-implemented with the new purpose in mind. The core code was separated from the rest of the System and became independent, both in terms of development and operation, in addition to gaining a name, Hexagon. A hardware abstraction layer was written with the inclusion of system calls known in the Unix world, such as open(), close(), read() and write()[^5]. Devices were named and disk drives changed from DOS naming to Unix device names. The kernel then proceeds to follow a known initialization process, executing, with PID 1, the first user process, init, which then loads the rest of the components. Unix-like utilities were then written that used the kernel's Unix-like API, and several Unix-like tools have been written since then (2017 onwards).

### The HAPP executable format

The HAPP executable image format was developed for Hexagon to allow the development of images that can be verified and validated for architecture and minimum kernel versions necessary for correct execution. The header also stores important information, allowing the developer to directly add an entry point, regardless of where it is inside the image, something that should have been redirected earlier when the executable image was in pure binary format. The HAPP image also allows you to validate that the image to be loaded is really an executable image, preventing unsupported files from being executed, even if they are not even executable files. It also allows the system to check code dependencies, such as the aforementioned architecture, as well as Hexagon version numbers, which must be equal to or greater than the minimum specified by the header. All HAPP images must have this full header, including reserved sessions, in order to function correctly in later versions of the System. HAPP images are always 32-bit. For 16-bit images, the system uses the HBoot header implementation (implementation found in system boot modules).

In Assembly language, the system development language, the header, in its 2.0 specification:

```assembly
headerAPP:

.signature: db "HAPP" ;; Signature
.architecture: db 01h ;; Architecture (i386 = 01h)
.MinimumVersion: db 8 ;; Minimal version of Hexagon
.Minimum subversion: db 40 ;; Minimal Hexagon Subversion
.inputpoint: dd ;; Input point offset (reference to main function here)
.ImageType: db 01h ;; Executable image type (executable = 01h)
.reserved0: dd 0 ;; Reserved (Dword)
.reserved1: db 0 ;; Reserved (Byte)
.reserved2: db 0 ;; Reserved (Byte)
.reserved3: db 0 ;; Reserved (Byte)
.reserved4: dd 0 ;; Reserved (Dword)
.reserved5: dd 0 ;; Reserved (Dword)
.reserved6: dd 0 ;; Reserved (Dword)
.reserved7: db 0 ;; Reserved (Byte)
.reserved8: dw 0 ;; Reserved (Word)
.reserved9: dw 0 ;; Reserved (Word)
.reserved10: dw 0 ;; Reserved (Word)
```

Applications for Hexagonix/Andromeda can be developed in Assembly, so far, using the assembler of your choice (provided it can generate x86 code). Libraries for application development, containing macros, functions and system calls, can be found [here (libasm)](https://github.com/hexagonix/libasm) and are designed to work with assemblers [fasm]( https://flatassembler.net/) and [nasm](https://www.nasm.us/). When accessing the **libasm** repository, you will have access to the libraries divided according to the support of a specific assembler. Support for more assemblers may be added in the future. A C library (libc) is also in the pipeline for the near future.

Below, an implementation of a small application written as an example, which uses the Hexagon header and system calls, written in x86 assembly language in Intel syntax and assembled with the help of the flat assembler (FASM). Note that to request access to Hexagon calls, this application must import the **hexagon.s** file from libasm (depending on the chosen assembler. In this case, fasm/hexagon.s). This application sends a message to the terminal and then exits. You can get more information about the HAPP format specification in the HAPP library of [libasm for fasm](https://github.com/hexagonix/libasm/blob/main/fasm/HAPP.s) or [libasm for nasm]( https://github.com/hexagonix/libasm/blob/main/nasm/HAPP.s). Below you can get more information about system calls.

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

format binary as "app" ;; Defines the format and extension of the generated file

use32

;; Header can be set directly like this and filled in manually
;; or through a macro available in the HAPP.s library, from libasm.
;; Below is manual implementation (which should be discouraged as it
;; API changes would lead to manual changes to all sources. That
;; does not occur with the use of the library, which, when updated,
;; to make all sources compatible, automating the process).

headerAPP:

.signature: db "HAPP" ;; Signature
.architecture: db 01h ;; Architecture (i386 = 01h)
.MinimumVersion: db 1 ;; Minimal version of Hexagon
.Minimum subversion: db 00 ;; Minimal Hexagon Subversion
.EntryPoint: dd startAPP ;; entry point offset
.ImageType: db 01h ;; executable image
.reserved0: dd 0 ;; Reserved (Dword)
.reserved1: db 0 ;; Reserved (Byte)
.reserved2: db 0 ;; Reserved (Byte)
.reserved3: db 0 ;; Reserved (Byte)
.reserved4: dd 0 ;; Reserved (Dword)
.reserved5: dd 0 ;; Reserved (Dword)
.reserved6: dd 0 ;; Reserved (Dword)
.reserved7: db 0 ;; Reserved (Byte)
.reserved8: dw 0 ;; Reserved (Word)
.reserved9: dw 0 ;; Reserved (Word)
.reserved10: dw 0 ;; Reserved (Word)

;;*************************************************************

include "hexagon.s" ;; Include system calls

;;************************************************ *************

;; Variables and constants

msg: db 10, 10, "This is a template with a simple HAPP application example!", 10, 0

;;************************************************ *************

;; Entry point

startAPP:

    move esi msg

    printString ;; Here we have a macro that configures and calls an API function

    Hexagonix terminateProcess ;; Another macro that asks which call to make
```

More detailed Hexagon documentation is in the pipeline and is being released as ready.

### System calls

System calls are BSD-style, with the function number present on the stack and the parameters/arguments next to the registers. For a complete list of system calls available in the current version of the system, have a look at the Hexagon library at [libasm for fasm](https://github.com/hexagonix/libasm/blob/main/fasm/hexagon.s ) or [libasm to nasm](https://github.com/hexagonix/libasm/blob/main/nasm/hexagon.s).

</details>

<details title="Hexagonix environment" align='left'>
<br>
<summary align='left'><strong>Hexagonix environment</strong></summary>

Hexagonix implements, together with Hexagon, a series of Unix-like utilities, with functionality and syntax similar to UNIX and Unix-like systems. **Utilities such as init, login, sh, top, ps, cp, rm, cat, clear, man, among others, are included in the standard distribution of Hexagonix**. These utilities make up the Hexagonix base utilities package. The login and user-mode environment startup tools are in this package, as well as several configuration files for this environment. These utilities generally do not have a graphical interface, only a command-line interface (CLI). However, they can be requested by applications that have a graphical interface. This environment is available in both the [Hexagonix](hexagonix.img) distribution and the [Andromeda](andromeda.img) distribution.

### Some applications and utilities in the Hexagonix environment

Hexagonix includes many of the Unix utilities you may already be familiar with, such as:

* init
* login
* ls
* cat
* cp
* rm
* clear
* top
* ps
* man
* su
* sh (shell padrão)
* uname
* whoami, among others.

Some applications and utilities were developed exclusively for Hexagonix, such as:

* atop (alternate version of top)
* power (computer state control)
* fnt (Hexagonix graphic font change utility)
* hash (alternate shell)
* log (used to get internal Hexagon logs, but now deprecated)
* lshapp (gets and displays information from HAPP images)
* lshmod (gets and displays information from HBoot modules and HBoot itself)

It is worth remembering that Hexagonix utilities try to implement a POSIX interface as far as possible, similar in syntax to Unix utilities (FreeBSD and Linux used as a template).

### Third party applications available for Hexagonix

* [Flat Assembler (fasm)](https://flatassembler.net/index.php)

Hexagonix received a port of the [fasm](https://flatassembler.net/index.php) assembler, which was adapted for Hexagonix, allowing the user to develop applications directly on the system. This port is called fasmX. Changes added to the code, as well as the software license, can be found in the [fasm repository for Hexagonix](https://github.com/hexagonix/fasm). This repository is a fork of [original repository](https://github.com/tgrysztar/fasm). Added code is based on modifications made to the original code and authorial additions. This modified/authored code can be found in the repository, [clicking here](https://github.com/hexagonix/fasm/tree/master/SOURCE/HEXAGONIX). fasmX, the fasm port for Hexagonix, is always updated when new features are added to the fasm repository. To indicate that it is a stable and tested version, the fasmX version number always inherits the fasm numbering, followed by a character x (for example, the version based on fasm 1.73.30, after testing, receives the numbering 1.73 .30x). You can report bugs or code generation or optimization issues in the Hexagonix version [here](https://github.com/hexagonix/fasm/issues). To report general fasm bugs, use the [official](https://github.com/tgrysztar/fasm) repository.

</details>

<details title="Andromeda environment" align='left'>
<br>
<summary align='left'><strong>Andromeda environment</strong></summary>

The Andromeda environment is built on the solid foundation provided by Hexagonix, including applications and utilities that do not implement the Unix philosophy or have a very different syntax and usage than you would expect from a Unix environment. In this way, they are separated as **Andromeda apps**, and are not part of the standard distribution of Hexagonix. Here are the System settings app, calculator, font manager, text editors and the IDE developed for Andromeda. These utilities may or may not have a graphical interface. Together with them, the Andromeda environment comprises libraries developed to allow the development of applications, such as the **Estelar** library. This environment is only available in the [Andromeda](andromeda.img) distribution.

### Some Andromeda applications and utilities

* System Settings (config)
* Quartzo text editor
* Lyoko IDE for application development
* Electronic piano return Piano;
* Serial communication utility
* Andromeda Shell (ASH) - A new shell for Andromeda
* Andromeda calculator
* Font change utility
* Andromeda shutdown utility

### Third-party apps available for Andromeda

There are no third-party applications available for the Andromeda environment yet. If interested, you can build the first one!

</details>

<details title="Hexagonix graphic fonts" align='left'>
<br>
<summary align='left'><strong>Hexagonix graphic fonts</strong></summary>

The default installation of Hexagonix also provides a number of fonts that can be loaded by the settings application or the font utility (font manager). These files are used to change the graphical display font for Hexagonix and Andromeda.

Graphics mode fonts for Hexagon are developed as a bitmap in Assembly which, when compiled, generate a binary image of the font with representations of each character. The standard Hexagonix fonts have now been released as open source and are available in the [Hexagonix font repository](https://github.com/hexagonix/Fontes).

### How to create your own graphic font

Feel free to download the font [model](https://github.com/hexagonix/Fontes/blob/main/modelo.asm), which is already structured but with blank characters, and draw the your own graphic font! For that, you need to know some technical information about them:

* Fonts have a height of 16 and a width of 8 pixels. This information is necessary to ensure that your font does not experience problems during use.
* You can freely divide the placeholders for accents and other graphic features of each character, such as cedilla or portions that fall below the character line, such as y, comma, etc.
* Fonts are drawn in bitmap format. Therefore, each character is a pixel map composed of 0s and 1s. The 0s symbolize undisplayed areas of the character, while the 1s represent the pixels of the character that will be displayed to the user. You must change each character array in the template font by adding the 1s where you want the pixels to appear to form the character. Below you will see an example of a blank character and the same representation of this character ready for the font.

The code below shows the bitmap representation of the hash sign (#) in the font [model](https://github.com/hexagonix/Fontes/blob/main/modelo.asm) and the implementation in the font [hint](https: //github.com/hexagonix/Fontes/blob/main/hint.asm).

```assembly
;; Blank representation of the hash (#) character in the template

.quill:

db 00000000b ;; Two pixels high for characters above the letter
db 00000000b

db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b

db 00000000b ;; Five pixels tall for characters above the letter
db 00000000b
db 00000000b
db 00000000b
db 00000000b

;; Blank representation of the hash character (#), in hint font

.quill:

db 00000000b
db 00000000b

db 00000000b
db 00000000b
db 00100010b
db 00100010b
db 01111111b
db 00100010b
db 01111111b
db 00100010b
db 00100010b

db 00000000b
db 00000000b
db 00000000b
db 00000000b
db 00000000b

```

You should already be able to see, inside the matrix, the hash mark, marked by the presence of 1s.

You can develop as many fonts as you like and play around with different and innovative designs, as well as extend the available characters (using the ASCII reference).

</details>

<details title="System development libraries" align='left'>
<br>
<summary align='left'><strong>System development libraries</strong></summary>

Hexagonix/Andromeda also provides functions that must be used to interact with the system environment itself. Libraries are used to access functions implemented by Hexagon or by the libraries themselves, allowing easy development of applications and utilities for both the Hexagonix and Andromeda environments. The libraries implement functions for displaying text, mathematical calculations, sending messages, opening files and devices, and much more. The core library (hexagon.s) provides functions accessible to both possible distribution environments, while other libraries may be unique to the Andromeda environment. These libraries include graphical functions to build interfaces in graphical mode (Andromeda), as well as functions to check the currently running system version (Hexagonix and Andromeda). The Hexagonix base utilities perform the Hexagon version check to see if they can be run, using the Unix utility uname or directly via a Hexagon system call.

To learn more and check each function available in the system development libraries, see the [libasm] repository (https://github.com/hexagonix/libasm).

</details>

<hr>

# How to test Hexagonix or Andromeda

## System requirements

Below is a list of minimum and recommended requirements for testing Hexagonix/Andromeda on a virtual machine or physical machine.

<details title="Minimum requeriments" align='left'>
<br>
<summary align='left'><strong>Minimum requeriments</strong></summary>

* Processor: Pentium III (1999) with SSE and MMX support or newer;
* RAM memory: 32 Mb minimum (a minimum installation with 32 Mb is usually enough, in most cases);
* Hard disk: IDE or SATA hard disk with a minimum of 50 Mb;
* Necessary peripherals:
  * Serial port (1-4);
  * Parallel port (1-4);
  * PS/2 or USB keyboard;
  * VGA video card with 2 Mb of video memory (with color support).

</details>

<details title="Recommended" align='left'>
<br>
<summary align='left'><strong>Recommended</strong></summary>

* Processor: Pentium D or newer;
* RAM memory: 50 Mb;
* Optional peripherals:
  * PS/2 or USB mouse;
  * Video card with > 2 Mb of video memory.

</details>

## Get the disk images with the system instalation

To test Hexagonix or Andromeda, you will need one of the disk images available in this repository, as well as the [qemu](https://www.qemu.org) tool installed on your computer, if you want to test the system in an environment virtualized. The image can also be used for writing to a physical disk on a real machine.

To test Hexagonix, get the ['hexagonix.img'](hexagonix.img) file from this repository.
To test Andromeda, get the ['andromeda.img'](andromeda.img) file from this repository.

## For testing in virtualized environment

First, you must install the qemu tool, which will manage the virtual machine. To do so, you can install qemu using official Linux distribution repositories or by accessing [here](https://www.qemu.org) to get installation files for Windows and macOS. 

<details title="Install on Debian, Ubuntu and Pop!_OS and derivatives" align='left'>
<br>
<summary align='left'><strong>Install on Debian, Ubuntu and Pop!_OS and derivatives</strong></summary>

For Ubuntu, the following line will install qemu and all its dependencies (root privileges required):

```
sudo apt install qemu qemu-system-i386
```

</details>

Now that you have qemu installed on your computer, you can proceed with running the system.

To run the system satisfactorily, you must provide at least 32 MB of RAM for the virtual machine. This is due to Hexagon's memory management architecture, which requires 16 MB of RAM dedicated to the kernel and at least 16 MB for allocating applications, utilities and open files. Hexagon doesn't allow less than that to run. If more memory is provided, the additional memory will always be reserved, with priority, to be made available to user processes. Normally, the command line below fulfills all requirements for running the system:

```
qemu-system-i386 -hda andromeda.img -m 32 -soundhw pcspk --enable-kvm -serial file:"Serial.txt"
qemu-system-i386 -hda hexagonix.img -m 32 -soundhw pcspk --enable-kvm -serial file:"Serial.txt"
```

You can omit the -serial parameter if you want. This parameter ensures that debug output from Hexagon and applications will be directed to a file on your computer, where you can see what was sent. You can also omit the -soundhw parameter, which is responsible for directing the sound output from the virtual system to your physical computer. On some Linux systems, the above configuration may conflict with pulseaudio, and may be omitted. Remember that by omitting the parameter, system sounds will not be output to you.

Remembering that you must use a version/edition of qemu that can run software written for the x86 architecture (i386 or x86_64). To download and install qemu, click [here](https://www.qemu.org/download/).

## For testing on physical machine

You must use Linux/macOS or some tool available for Windows that allows you to burn this image to disk.

On Linux/macOS/Unix, use the line below:

```
dd if=andromeda.img of=/dev/device
```
where drive is the desired device (usually sdb or sdc for USB devices and hda, hdb, sda or sdb for hard/solid state drives). Restart your computer and test the system. It is worth remembering that secure boot mode is not supported, and booting is only supported in BIOS or UEFI legacy BIOS mode.

Note that system performance may vary depending on the machine being tested. Added to this is the fact that the latest versions of the system have not been or are being tested directly on the physical machine, as the main operating system. If any problem occurs when running Hexagonix/Andromeda on a physical machine, please report the detailed error [here](https://github.com/hexagonix/Distro/issues), in Portuguese or English, informing data such as device, processor, amount of RAM memory, video card (if available) and peripherals connected, as well as the device used to install the system (internal disk drive or USB removable media).

## First use

When starting the system, you will be asked to enter a username and password. For the first use, use

```
User: root
Password: root
```

You can add another user by changing the 'USUARIO.UNX' file at the root of the disk. Remember not to remove the root user. This can make the system permanently inoperable.

<details title="Report errors" align='left'>
<br>
<summary align='left'><strong>Report errors</strong></summary>

You can report bugs and help develop the system. To do this, open an error notification [here](https://github.com/hexagonix/Distro/issues), informing the error as detailed as possible (such as device brand, processor, amount of RAM, video and connected peripherals, as well as the device used to install the system, such as an internal disk drive or USB removable media). Remember to inform which application the error occurred in, if the error occurs while the system is already in operation. If the problem occurs in the boot process, please report what was displayed/observed behavior of the machine.

</details>

<hr>

# Screenshots

<details title="Hexagonix" align='left'>
<br>
<summary align='left'><strong>Hexagonix</strong></summary>

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix1.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix2.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix3.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix4.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix5.png" width="500" height="400">
</p>

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

</details>

<details title="Andromeda" align='left'>
<br>
<summary align='left'><strong>Andromeda</strong></summary>

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda1.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda2.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda3.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda4.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda5.png" width="500" height="400">
</p>

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

</details>

<hr>

# More information

<details title="Languages" align='left'>
<br>
<summary align='left'><strong>Languages</strong></summary>

At this moment, both the system and the documentation are only available in Portuguese. Documentation in English will be available soon, and there are plans to support English as a primary language possibility in addition to Portuguese (most of the work has already been done).

</details>

<details title="Inspiration" align='left'>
<br>
<summary align='left'><strong>Inspiration</strong></summary>

This project was possible and today it can see the light of day thanks to many others who have come before and contributed with design ideas and teaching how an operating system should work, even if simple. Are they:

* MS-DOS, with code available [here](https://github.com/microsoft/MS-DOS)
* [MikeOS](http://mikeos.sourceforge.net/)
* [Linux 0.1.1](https://kernel.org)
* [FreeBSD](https://www.freebsd.org/)
* [XNU/Darwin](https://github.com/apple/darwin-xnu)
* [LittleKernel](https://github.com/littlekernel/lk)
* [Google Fuchsia](https://fuchsia.googlesource.com/fuchsia/)

In addition, other projects helped in the development of Hexagonix/Andromeda, either by providing new design ideas that go beyond the traditional organization of an operating system, or providing well-documented code that allowed us to understand how certain parts of an operating system work, or contributing with code examples that later came to inspire functions that were written exclusively for Hexagonix/Andromeda (mainly the kernel code). Despite not having been copied and reused in the system, the code of these public domain projects made it possible to understand the operation of certain computer components, opening doors for copyright codes to be written based on the study of the code of these projects. It is worth mentioning that the projects below were released by their original developers in the public domain. Are they:

* [Snowdrop OS](http://www.sebastianmihai.com/snowdrop/), which inspired me to write various hardware control routines and other 16-bit functions available in HBoot. The code for this system has been released into the public domain.
* [Alotware](https://github.com/0x5CE/alotware), which inspired me to create the process management functions in early versions of Hexagon (now rewritten numerous times). The code for this system has been released into the public domain.

</details>

<details title="Author, contributors and contact" align='left'>
<br>
<summary align='left'><strong>Author, contributors and contact</strong></summary>

## Author

* [Felipe Miguel Nery Lunkes](https://github.com/felipeldev)

Feel free to contact me, report bugs or be interested in participating in the project.

## Contributors

* [Felipe Miguel Nery Lunkes](https://github.com/felipeldev)

## Email

* hexagonixdev@gmail.com (PT/EN)
* felipemiguel_nery@hotmail.com (PT/EN)

## Social networks

* [Twitter](https://twitter.com/felipemnlunkes) (Felipe Miguel Nery Lunkes)

</details>

<details title="Copyright notes" align='left'>
<br>
<summary align='left'><strong>Copyright notes</strong></summary>

Hexagonix/Andromeda was developed from scratch by [Felipe Lunkes](https://github.com/felipenlunkes).

Read the [license](LICENSE) for more information on copyright, code ownership, and redistribution that apply only to files available in this repository (does not apply to the set of data and source code files that make up Hexagonix/Andromeda) . It is worth mentioning that the code of the system components is being released little by little and that each package can be released with a different license. Always keep an eye on the 'LICENSE' file available in each repository to be aware of legal rights and obligations.

</details>

[^1]: You can get more information about the relationship between Darwin and macOS [here](https://en.wikipedia.org/wiki/Darwin_(operating_system)).
[^2]: You can find the project page [here](https://www.freedos.org/).
[^3]: Booting in DOS mode was possible after searching the FreeDOS documentation, especially the "SYS.C" file (which can be found [here](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/2043/), which indicates in which thread the kernel expects to be loaded and which parameters are needed to boot the kernel correctly. Each DOS system has a preferred loading segment and this loading of other DOS editions can be implemented in the future with the help of new HBoot modules (in case of a proprietary system, the user must have a license). All the code for loading the kernel was developed from scratch and not based on any existing ones (the implementation of HBoot and modDOS, which are original, is done in Assembly, while the FreeDOS loading code is developed in C). The original implementation of modDOS code and other modules for DOS systems also frees the implementation from any legal problems.
[^4]: HBoot's DOS compatibility mode (modDOS) boot can be useful for running volume error checking, volume defrag, partitioning and other diagnostic as well as development tools such as compilers and assemblers which are not supported by Hexagonix/Andromeda (the 16-bit tools for example).
[^5]: Supports open(), close(), read() and write() calls, at least in concept. System calls are always BSD-style, with a function number on the stack and parameters in the registers.
