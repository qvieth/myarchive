# [bootloader and boot process](https://www.ionos.com/digitalguide/server/configuration/what-is-a-bootloader/)
# [bios vs uefi vs bootloader vs firmware](https://www.quora.com/what-is-difference-between-bios-uefi-bootloader-and-firmware) 

<!-- vim-markdown-toc GFM -->

* [bootloader](#bootloader)
	* [where is boodloader stored](#where-is-boodloader-stored)
	* [a summary of bootloader's function](#a-summary-of-bootloaders-function)
	* [name of the bootloaders](#name-of-the-bootloaders)
* [firmware, bios, uefi](#firmware-bios-uefi)
	* [definitions](#definitions)
	* [boot process](#boot-process)

<!-- vim-markdown-toc -->
## bootloader
- __bootloader__ aka __boot program__ or short term for __bootstrap loader__ : a special operating system software
- boot loader is a piece of code that runs before any operating system is running
- boot loader may change with particular os type

- loads into the __working memory__ of a computer after start-up
- for this purpose, immediately after a device starts, a bootloader is generally launched by a __bootable medium__ like a hard drive, cd/dvd or usb stick
- the __boot medium__ receives information from the computer's __firmware__ (bios) about where the __bootloader__ is
- the hold process is also described as __booting__ (__boot process__)


- __boot signature__ aka __boot record__
### where is boodloader stored
can be stored in 2 different places :
- in the __first block__ of the __bootable medium__
- on a __specific partition__ of the __bootable medium__

the first available memory block or sector in the medium is always reserved for the record.
- because of this important function, it is also known as the __boot block__ or __boot sector__

in the second case, the operating system uses a selected partition as the storage location for the bootloader
[..readmore](https://www.ionos.com/digitalguide/server/configuration/what-is-a-bootloader/)

### a summary of bootloader's function
- as soon as a bootloader has been initialized __by the respective firmware__
- it has system responsibility to get the boot process going
- the __first task__ is to __load the main memory__, which is essential for the processor to work.
- the __second task__ : loads the [kernel](kernel) of the operating system
- the bootstrap loader also processes different routine tasks and commands, e.g. integrating data storage
- some bootloaders also perform tasks beyond starting up software, including :
    - identifying and starting other available bootloaders
    - launching application programs (frequently used in the 1980s to launch computer games directly from a disk)
    - correcting or expanding missing functions and entries in the firmware
    - loading alternative firmware

### name of the bootloaders
- bootmgr : for ms system since window vista and window server 2008
- __barebox__ : for embedded systems in printers, cameras, cars, airplanes, and more
- boot.efi : efi bootloader that has been used in mac devices since 2006
- bootx : former bootloader for macos
- __grand unified bootloader (grub)__ : free boot program for unix-like os such as linux
- arm core bootloader : for microcontrollers (used in iphones among others)
- openbios : free portable boot manager under gpu-gpl licensce

## firmware, bios, uefi
### definitions
- firmware : programm that's written to the rom of a __computing device__, added at the time of manufacturing
- __bios : firmware__
- __bootloader : software__
- uefi : specification that allows firmware to access hardware in different manner than conventional way


### boot process
- bios, uefi(more modern) : usually be implemented by manufacturers in __flash memory__ on the computer's __motherboard__
- both applications collect the most diverse hardware data and create a complete list of all of the device’s available drives.
- when this process is complete : [..readmore](https://www.ionos.com/digitalguide/server/configuration/what-is-a-bootloader/)
