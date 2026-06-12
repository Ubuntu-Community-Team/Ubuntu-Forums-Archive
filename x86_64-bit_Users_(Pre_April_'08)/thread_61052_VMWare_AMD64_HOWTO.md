---
title: "VMWare AMD64 HOWTO"
date: 2005-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbzdeath on 2005-08-30
can anyone out there write one up or briefly explain how to get it going(preferably without a 32bit chroot if possible..)?

---

### Post by earthfall on 2005-08-30
I have no problem in running vmware 5.0 workstation using ia32 libraries.

---

### Post by dbzdeath on 2005-08-30
[QUOTE=earthfall]I have no problem in running vmware 5.0 workstation using ia32 libraries.[/QUOTE]

yeah i installed them and when i run a vm i get "Unable to change virtual machine power state: Failed to connect to peer process."

---

### Post by sonni_kuba on 2005-08-30
[I]Sure thing... it is quite simple

First, make sure you have the build essentials
[/I]
> sudo apt-get install linux-headers-2.6.10-5-amd64-generic
> sudo apt-get install gcc

[I]Then, create the proper symbolic link
[/I]
> sudo ln -s /usr/src/linux-headers-2.6.10-5 /lib/modules/2.6.10-5-amd64-generic/build
[I]
Then untar your vmware archive[/I]

> sudo tar zxvf VMware-workstation-5.0.0-13124.tar.gz
[I]
Go inside the directory[/I]

> cd vm*
[I]
Run the install program[/I]

> sudo ./vmware-install.pl

*After that, just agree to the default values by pressing [Enter] or typing 'yes'*

Hope that this works well for you. :-)

---

### Post by dbzdeath on 2005-08-30
[QUOTE=sonni_kuba][I]Sure thing... it is quite simple

First, make sure you have the build essentials
[/I]
> sudo apt-get install linux-headers-2.6.10-5-amd64-generic
> sudo apt-get install gcc

[I]Then, create the proper symbolic link
[/I]
> sudo ln -s /usr/src/linux-headers-2.6.10-5 /lib/modules/2.6.10-5-amd64-generic/build
[I]
Then untar your vmware archive[/I]

> sudo tar zxvf VMware-workstation-5.0.0-13124.tar.gz
[I]
Go inside the directory[/I]

> cd vm*
[I]
Run the install program[/I]

> sudo ./vmware-install.pl

*After that, just agree to the default values by pressing [Enter] or typing 'yes'*

Hope that this works well for you. :-)[/QUOTE]

what about ia32-libs?




hmmm during the install i do get this...

The correct version of one or more libraries needed to run VMware Workstation
may be missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0x00000000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x5557c000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5559f000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x555a3000)
        libX11.so.6 => /usr/X11R6/lib32/libX11.so.6 (0x555b2000)
        libXtst.so.6 => /usr/X11R6/lib32/libXtst.so.6 (0x55679000)
        libXext.so.6 => /usr/X11R6/lib32/libXext.so.6 (0x5567e000)
        libXt.so.6 => /usr/X11R6/lib32/libXt.so.6 (0x5568c000)
        libXpm.so.4 => /usr/X11R6/lib32/libXpm.so.4 (0x556dd000)
        libICE.so.6 => /usr/X11R6/lib32/libICE.so.6 (0x556ed000)
        libSM.so.6 => /usr/X11R6/lib32/libSM.so.6 (0x55704000)
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib32/libz.so.1 (0x5570d000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5571e000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x55555000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc
before you can run VMware Workstation.

---

### Post by dbzdeath on 2005-08-30
**** i just figured out the problem... for some reason it needed to be run as root ... anyone know why that might be? and how i can fix it?

---

### Post by earthfall on 2005-08-31
Check for your /etc/ld.so.conf file. Here follows my configurations:

> cat /etc/ld.so.conf
/usr/X11R6/lib
/lib32
/usr/lib32
/usr/X11R6/lib32

> dpkg -L ia32-libs-gtk | grep render
/usr/lib32/libXrender.so.1.3.0
/usr/lib32/libXrender.so.1

---

### Post by Kemotaha on 2005-08-31
[QUOTE=dbzdeath]**** i just figured out the problem... for some reason it needed to be run as root ... anyone know why that might be? and how i can fix it?[/QUOTE]
 It needs to be run as root because it sets up stuff that starts at boot time, like all the networking for the VMs.  I don't know if there is a way not to have it run as root.  I guess if you went with host only networking you might be able too, but it may not even give you that option.

---

### Post by dbzdeath on 2005-08-31
[QUOTE=Kemotaha]It needs to be run as root because it sets up stuff that starts at boot time, like all the networking for the VMs.  I don't know if there is a way not to have it run as root.  I guess if you went with host only networking you might be able too, but it may not even give you that option.[/QUOTE]


i know for a fact that its possible with or without host only networking.... i used to use gentoo amd64 which ran vmware fine as a normal user

---

### Post by mlomker on 2005-08-31
I had it running just fine on the standard kernel.  The GUI ran fine when logged in as a standard user (I use KDE).  The services do have to load at boot, but I'm surprised if you're saying that the GUI won't run if you're not root.  I had that problem when I was on Linspire but 'things just work' on Ubuntu.

I'm having a heck of a time getting the VMWare kernel modules to compile on a new/custom 2.6.13 kernel.  I'm building the headers, so I don't understand what it thinks is missing.  I'm trying to figure that out this morning...

---

### Post by dbzdeath on 2005-08-31
[QUOTE=mlomker]I had it running just fine on the standard kernel.  The GUI ran fine when logged in as a standard user (I use KDE).  The services do have to load at boot, but I'm surprised if you're saying that the GUI won't run if you're not root.  I had that problem when I was on Linspire but 'things just work' on Ubuntu.

I'm having a heck of a time getting the VMWare kernel modules to compile on a new/custom 2.6.13 kernel.  I'm building the headers, so I don't understand what it thinks is missing.  I'm trying to figure that out this morning...[/QUOTE]


the GUI runs fine but when i try to start a vm it says it cannot connect to peer process... obviously due to permission errors... my guess is the bridged adapter?

---

### Post by Kemotaha on 2005-08-31
[QUOTE=mlomker]I had it running just fine on the standard kernel.  The GUI ran fine when logged in as a standard user (I use KDE).  The services do have to load at boot, but I'm surprised if you're saying that the GUI won't run if you're not root.  I had that problem when I was on Linspire but 'things just work' on Ubuntu.

I'm having a heck of a time getting the VMWare kernel modules to compile on a new/custom 2.6.13 kernel.  I'm building the headers, so I don't understand what it thinks is missing.  I'm trying to figure that out this morning...[/QUOTE]

I am not saying the gui won't run as root.  I helped beta test 5.0 so I don't have it now.  But I had to run the vmware-install file as root and then I could run the GUI.  I think there was also a config file that you had to run as root the first time before it would run as a normal user, but I could be think ing of something else.

---

