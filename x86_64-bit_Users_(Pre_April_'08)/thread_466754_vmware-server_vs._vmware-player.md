---
title: "vmware-server vs. vmware-player"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by XhwMikey on 2007-06-07
All,

  I am running Feisty AMD64 and I have some packages installed that depend on vmware-player, which as a result, has been installed.  I am planning to venture into the virtualization arena (WinXP Guest OS), and am intrigued by the additional capabilities (most notably the ability to create a virtual machine without resorting to EasyVMX).  I am not opposed to using EasyVMX, but I just like the idea of self containment.  That said, installation of vmware-server (64bit) necessitates the removal of vmware-player, and I'm wondering if I will "break" the packages that depend upon vmware-player.  I suspect not, but would like backup opinions from the community.  Thanks

XhwMikey

---

### Post by greenfrog on 2007-06-07
Everything that I have run on vm-server that were developed for vm-player has worked without any problems.
:D:D:D

---

### Post by nxt on 2007-06-07
> **XhwMikey said:**
> All,

  I am running Feisty AMD64 and I have some packages installed that depend on vmware-player, which as a result, has been installed.  I am planning to venture into the virtualization arena (WinXP Guest OS), and am intrigued by the additional capabilities (most notably the ability to create a virtual machine without resorting to EasyVMX).  I am not opposed to using EasyVMX, but I just like the idea of self containment.  That said, installation of vmware-server (64bit) necessitates the removal of vmware-player, and I'm wondering if I will "break" the packages that depend upon vmware-player.  I suspect not, but would like backup opinions from the community.  Thanks

XhwMikey


The images can run in player or server. Uninstalling one thing should not have any effect on the vmx files.

The problem with the vmware server I have, is that I always have to run vmware-config.pl after reboot - it seems to be unable to save the setting permanently. From what I have read it is connected with the previous installation of vmware player. I haven't been able to fix that yet :( If you plan to install server I therefor suggest uninstalling vmware player and deleting it's files first (not the vmx/vmdk virtual macines of course!)

I am kind sad, that I can not have server and player on the same machine. I am running couple of virtual machines and I owuld appreciate being able to place each one on a different desktop. With vmware server, I'm stuck in vmware tabs. :((

---

### Post by dabl on 2007-06-07
> **nxt said:**
>  I always have to run vmware-config.pl after reboot - it seems to be unable to save the setting permanently.

I'm having that problem too -- apparently there is some "lockfile" issue -- I just found this:

[http://www.vmware.com/community/forum.jspa?forumID=123](http://www.vmware.com/community/forum.jspa?forumID=123)

Look down the list to the one that mentions Ubuntu 7.04

---

### Post by kuja on 2007-06-07
> **nxt said:**
> The images can run in player or server. Uninstalling one thing should not have any effect on the vmx files.

The problem with the vmware server I have, is that I always have to run vmware-config.pl after reboot - it seems to be unable to save the setting permanently. From what I have read it is connected with the previous installation of vmware player. I haven't been able to fix that yet :( If you plan to install server I therefor suggest uninstalling vmware player and deleting it's files first (not the vmx/vmdk virtual macines of course!)

I am kind sad, that I can not have server and player on the same machine. I am running couple of virtual machines and I owuld appreciate being able to place each one on a different desktop. With vmware server, I'm stuck in vmware tabs. :((

In Feisty, you can just install the vmware package from the canonical commercial repository, I doubt you'd have problems with that? If interested just uninstall and then install with the packages :)

---

### Post by ericdegen on 2007-06-07
First off as a long time user of VMware with windows hosts, I would recommend the server as opposed to the player product.  I have been running VM server on 32-bit feisty with good success the last few weeks. 

I was having the same "reconfig" problem you described till I found this walk thru.

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

Right now I'm building an Intel quad core 64-bit box.  I'll keep you posted on my progress, and would welcome any heads ups you guys might have.

Cheers,

---

### Post by dabl on 2007-06-07
I have found (i.e. been provided) the fix for the "must reconfigure VM Player after every re-boot" problem.

```

sudo rm /etc/vmplayer/not_configured
```


Apparently it is a lockfile that is set when re-installing VM Player, and interferes with subsequent saved configurations.

:)

---

### Post by veloce on 2007-06-08
> **nxt said:**
> 
I am kind sad, that I can not have server and player on the same machine. I am running couple of virtual machines and I owuld appreciate being able to place each one on a different desktop. With vmware server, I'm stuck in vmware tabs. :((

I achieve this, for windows vms, by using rdp to access the vms.  Over the host only network the reaction time is great (better than vmserver console in a window) and the windowing is better. You just set up the vm to allow rdp access then I use gnome-rdp to access them either in a window or full screen.  Works great full screen in one of my dual monitors. Mouse just moves back to the other monitor and I have my mail / browser / etc running locally on ubuntu on that one.

---

### Post by XhwMikey on 2007-06-09
All,

   Thanks for your replies.  Sorry it took me so long to get back to this thread - hate it when work interferes with matters of real consequence;)  Anyway, it looks like I'll have a go of installing Vmware-server on my system.  I have really minimized my use of Windoze, so it will be used for the odd Windoze Only app that happens once in a while.  Thanks again!

Mikey

---

