---
title: "rebuilding kernel"
date: 2007-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebichuhamster on 2007-03-10
Ok, so I have an HP dv6000, Nvidia 6150 Geforce Go, Broadcom wireless, Fujitsu ATA 120 Gb Hardrive, AMD turion x2....

its a laptop so i cant just change the card as easily as with a desktop

I've been on the process of installing Ubuntu for about 3 weeks and i've received helpful details on just the basic installation process for amd64.  Now for the drivers,, pum pum pum

I tried installing the drivers indiviually but each time i double click on the file it does nothing.  I try to run it on the terminal and it says 

Anyways,, i was referred by a fellow ubuntu expirienced friend of mine to try and recompile the whole kernel, which will take a lot of time but after that i should have no trouble at all. "Just follow the details in this webpage.

This webpage tells me that in order to succesfully enter the rebuilding-kernel menu i must have some packages installed, most of which were on the synaptic package manager.

THe website even provided me with commands to verify the installation of the package.  It all seems pretty perfect,, just unitll this:

i type in :

cardmgr -V (to check the version of the pcmcia-cs package)

prints out:

command not found 

In the synaptic package manager there is no "pcmcia-cs" package, so i download it from the net.  But i'm not able to install it.

Again i refer to the webpage and it tells me tu input './configure' and then 'make'.  It says if the './configure' outputs an error message or something it doesnt matter, but as i type in the 'make' command it just doesnt work.

As you probablly know im new at all this, so any helpful advice woud be invredibly apreciated >_<

---

### Post by teaker1s on 2007-03-12
If we are talking aboutt nvidia beta driver, this needs to be run with xserver stopped.
I did this by connecting an ethernet cable so I had internet access and booting recovery kernel.

It will also need to be granted execution rights using chmod 755 command.

make sure "build-essential" kernel source and headers are installed

To run the driver from command line you will need to put in the full path and name of driver including **.run**extension,even if you in the same directory.

further to this we have a dv6000 page here
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

