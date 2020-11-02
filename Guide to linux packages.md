# [Guide to Linux Packages](https://www.lifewire.com/guide-to-linux-packages-2202801)
- window rely on executable __installers__
- linux depends on __packages__ that are administered through __software repositories__

## what is a packages
- a package consists of a __collection__ of files that _perform a task_
- for example : GIMP distributes through a package
- all the files that GIMP needs to run appear in a tidy __archive__
- moreover, the package offers a small file that provides __important metadata__ about the program

## why packages
- because each Linux computer or server uses __different__ software including different __kernels__
- developers cannot guarantee that a "linux program" will run correctly on any given computer
- to fix this __interoperability__ problem, packages include a __manifest__ of [dependencies](dependencies)
- or lists of programs and versions that must be satisfied for the packaged software to run correctly on a given computer

## how do i use packages
- linux supports several major different types of package managers
- each performs __same__ basic function of installing and managing new programs
- but each use a __slightly differnt__ under-the-hood [architecture](architecture) and different user interfaces to perform the package-manager's __core tasks__
- common package-management systems include :
    - dpkg : base package manager for debian-based distributions
    - apt : a front-end for dpkg system, found in Debian-based distributions, such as Ubuntu, Linux Mint, and Elementary OS
    - apt-get : a more feature-rich front-end for the dpkg system, found in __debian-based distributions__
    - rpm : the base package manager found in redhat-based distributions, such as rhel, centos, fedora
    - yum : a front-end for the RPM system, found in red hat-based distributions
    - dnf : a more feature-rich front-end for the rpm system
    - zypp : found in suse and opensuse
    - pacman : the package manger for Arch-based distributions
- regardless of the specific package manager, the process of maintaining software on a Linux-based computer is generally the same
- you launch a software catalog that reads from one or more __repositories__ (archive of software optimized for given platform)
- pick-and-choose which software to install or remove through the graphical catalog, or use a shell session to execute the commands manually

## what is an alternative to a package
- although packages remain the tried-and-true method of distributing linux software
- in recent years alternative technologies aim to simplify software management
- for example : the new snap format treats programs as self-contained, isolated objects that run in their own protected space
- so they aren't 'dependent on dependencies'
- in addition, the really old-school method of software installation requires __compilation from source__
- this process is less common than it used to be, although linux veterans and slackware aficinados still do it
- a __compilation-from-source__ installation requires that you obtain the actual code for a program
- which you then compile and install on your own computer
- this process is, in theory, more efficient
- the installation is optimized for your specific computer
- but's it's generally a power-user strategy for people accustomed to developing their own software
