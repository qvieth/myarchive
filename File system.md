# file system
File systems are the standard for __organizing data__ on storage devices
- when formatting ssd, usb flash drive use : 
    - window : ntfs, exfat
    - linux : fat32, ntfs, ext4

File systems divide the storage space on a drive into compartment known as __clusters__ 
and maintain an __index__ of where individual files are located and available free space, different in __max file size, max volume size__
- fat : file allocation table : major variants = fat12, fat16 & fat32
- ntfs : new technology file system : introduce in 1993 to overcome limitation of fat32, limited compability on different OS
- exfat : extended file allocation table : file system optimized for high-capability USB flash drive and memory cards, default for __SDXC memory card__
- ext2, ext3, ext4 : extended filesystem : ext4 become linux default in 2008
- hfs, hfs+, apfs: hierarchical file system : macos standard, apfs 2017
- zfs : zed file system : integrated volume manager to control storage hardware, hence provides increased data protection
Which file system should you choose :
- for a system drive : use __ntfs__-window, __ext4__-linux, __hfs+__/apfs-macos
- for usb drives and memory cards, use __fat32__ for capacities under 32gb, __exfat__ for 32gb+ volume or 4gb+ files
- for other drives, use __NTFS__ if windows based, __exfat__ if pc/mac based or __fat32__
my learning experience :
- pay attention on max file size of the file system used on USB, memory cards

layout for the most part is outline in the FHS : File Hierarchy Standard

- /bin : binary : another word for programs or applications, basic functions are stored here
- /sbin : system binary : system admin would use, standard user wouldn't have access without permisions 
- /boot : contain things os need to boot, __boot loader__ live here
- /cdrom : legacy mounting rom
- /dev : where your __devices__ live : everything is a file : hardware, partition, ...
- /etc : et cetera, your configuration live here
- /lib , /lib32, /lib64 : this is where libraries are stored
- /media : mounted drive automatically by OS : usb, network drive, external hardrive,
- /mnt : like /media but for manually
- /opt :
- /proc : process
- /root : 
- /run : tempfs : run in ram
- /snap : snap packages stored here
- /srv : service directories where service data is stored, handy for external user acess
- /sys : way to interact with kernel, it's created everytimes system boot up
- /tmp : temporary files
- /usr : user application 
- /var : variables
- /home : where you store your personal files and documents
