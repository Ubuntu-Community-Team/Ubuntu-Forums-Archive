---
title: "vmplayer running virtual windows"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by computerjunkie on 2007-03-29
Hey, my laptop died that ran ubuntu 6.06 so I'm using the 64 bit version of edgy on my desktop. I was wondering how to make a virtual machine for vmplayer that would run the windows that came with this computer. The vmplayer thing says it can only run premade virtual machines so how do I install my XP and run it as a virtual OS?

---

### Post by thelinuxguy on 2007-03-29
> **computerjunkie said:**
> Hey, my laptop died that ran ubuntu 6.06 so I'm using the 64 bit version of edgy on my desktop. I was wondering how to make a virtual machine for vmplayer that would run the windows that came with this computer. The vmplayer thing says it can only run premade virtual machines so how do I install my XP and run it as a virtual OS?

You need VMWare server. Download it here: [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
Or follow the guide here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)

You may need to do some more reading on the 64-bit version issues though.

---

### Post by computerjunkie on 2007-03-29
well since i had the vmplayer installed when i try to install the server this is what i get: 

"chris@reddragon:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted."

I uninstalled vmplayer and removed the vmware directory from my home direcotry, but continue to get the same error.

Do i have to purge all of the files from my hard drive that has anything to do with vmplayer? And if so, why didnt the uninstaller (add/remove) do it properly?

---

### Post by thelinuxguy on 2007-03-29
> **computerjunkie said:**
> 
I uninstalled vmplayer and removed the vmware directory from my home direcotry, but continue to get the same error.


**Option 1**
System >> Administration >> Synaptic Package Manager
Search for vmware
Are the vmware-player-kernel-modules and other vmware-player-* packages still installed?

OR

```

sudo apt-get remove --purge vmware-player-kernel-modules
sudo rm -r /etc/vmware

```

**Option 2**
Found this a bit late: Create Virtual machines with VMPlayer with an easy hack: [http://linux.wolphination.com/?p=18](http://linux.wolphination.com/?p=18)
However, once you have VMWare server installed, playing with OSes will be simpler.

---

### Post by computerjunkie on 2007-03-29
ok thanks that removed it. I had to use sudo apt-get autoremove as well to get rid of some other packages that were not needed anymore. I tried the installer and it started, so I used control  z to get out of it so hopefully it'll work the next time I try it lol. Once I have vmware server installed, how do I install another OS?

---

### Post by thelinuxguy on 2007-03-29
> **computerjunkie said:**
> Once I have vmware server installed, how do I install another OS?

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

