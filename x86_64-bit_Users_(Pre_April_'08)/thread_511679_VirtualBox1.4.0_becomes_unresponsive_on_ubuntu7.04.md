---
title: "VirtualBox1.4.0 becomes unresponsive on ubuntu7.04(amd64)!!!"
date: 2007-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by newbb on 2007-07-28
Hi,
To use VirtualBox, I reinstall the entire ubuntu7.04(64-bit OS on AMD Athlon 64 X2 Dual Core 3600+ processor and DDR2-667 1GB RAM). Immediately after successfully installing ubuntu7.04 OS( i.e. pure OS + some built-in apps, utilities, and libraries ), I install virtualbox without any kind of updates.

According to virtualBox install HowTo( [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") ), I install virtualBox as follows:
1. Add this line "deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free" into /etc/apt/sources.list file.
2. Save innotek public key for apt-secure on my Desktop
3. Add this key with "apt-key add innotek.asc" on the terminal
4. "sudo apt-get install libstdc++5" on the terminal( Version 5 of libstdc++ )
5. "sudo apt-get install virtualbox" on the terminal
6. Add my user-account to vboxusers group and restart ubuntu7.04
Now VirtualBox1.4.0 for ubuntu7.04(amd64) has been successfully installed and can be launched.

However, the virtual machine( configured for Windows XP ) always becomes unresponsive after starting the virtual machine. The virtual machine window always show 0% progress. I cannot close either VM or VirtualBox window( see the pic ). The whole VirtualBox hangs and cannot be stopped, I am forced to close it by ending process in system monitor.

Is there anything wrong with my installation step? WHY does the virtual machine window hang forever?
Any suggestion is appreciated. Many thanks for all your help.

---

### Post by Midahed on 2007-07-28
I'm running Ubuntu 7.04 Feisty Fawn 64-bit desktop edition and had very similar problems to those you describe.  I tried various things to get round the problem with Virtualbox 1.4.0, but none worked reliably.  When I did get a Windows guest session running, it would pretty-well always freeze within about 15 minutes of being started - sometimes on a completely quiescent machine without any user activity.  I needed a reliable Windows environment for a couple of my core apps for which there are no sensible equivalents under Linux.  Virtualbox just didn't provide that reliability.  In the end I switched to VMware Server.  It installed flawlessly and has been rock-solid in regular use for several weeks.

Mike

---

### Post by gaylapdancer on 2007-07-29
I installed the 64bit version using Automatix2 and It works perfectly. It hasn't hung once.

Specs are:

AMD64 Athlon X2 4200+
1gB DDR2 RAM
Ubuntu 7.04 64-bit

The only problem with mine was that it will only run as root, so I load a Terminal and type:

cameron@Apollo-Ubuntu:~$ sudo -i
Password:
root@Apollo-Ubuntu:~# VirtualBox


I get the error:

Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device


But it all runs fine.
I recommend trying the Automatix install and see if it fixes it.

---

