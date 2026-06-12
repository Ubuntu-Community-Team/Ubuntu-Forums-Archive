---
title: "NIC killed immediately at boot"
date: 2007-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoWayBill on 2007-12-24
I installed Ubuntu Gutsy x64 tonight, wanting to upgrade to Studio.
My first experience with Ubuntu/Debian Linux, long time Fedora user.
I wanted x64 because of the size of files that I would be mixing/editing.

Cut to the chase...........
I installed from the Live cd, networking worked fine.
However after installation, immediately after loading the kernel, 1st boot, the NIC is shut down.
If you can see the splash screen the NIC is dead, light on modem goes from solid green to blinking amber.
"ifup eth0" and "ifdown eth0" have no effect as the card has been turned off.
Ticking and unticking the card in U Network Manager does nothing.
Card is configured the same as in Fedora, DHCP.

Booting back into Fedora (i386) gives a warning during boot "Eth0.....No link present......Check cable?"
It's a simple matter of activating the card in Network Manager, and all is well, until booting back into Ubuntu.

I reinstalled 3 times, formatting each time, to no avail.
Actually, the first install it worked, until upgrading to Studio, after that no more network.

My network cards are as follows.....
Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet
.....onboard, used for internet connection
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8138C+ 
.....PCI, used occasionally for internet connection sharing

---

### Post by Ehtetur on 2007-12-24
> **NoWayBill said:**
> My network cards are as follows.....
Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet
.....onboard, used for internet connection
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8138C+ 
.....PCI, used occasionally for internet connection sharing

My desktop also has an integrated realtek 8139...
And if I didn't start a terminal session on tty2 and edit /etc/modprobe.d/aliases before the install loaded gdm I had no network connection for updates during the install.
I disabled the loading of ipv6 AND bluetooth modules in order to get a network connection.
Here's what I did:

Edit aliases:
> sudo vim /etc/modprobe.d/aliases 
Look for the lines that contain ipv6 and bluetooth.
Add the word off in front of ipv6 and bluetooth:
> alias net-pf-10 off ipv6
alias net-pf-31 off bluetooth
Reboot the OS.
Hopefully you'll now be able to connect to the network.

---

### Post by NoWayBill on 2007-12-25
Thanks for the try, unfortunately the NIC is still killed as the kernel boots.

---

### Post by terminal on 2007-12-25
You can see in fedora which module was loaded for your nic to run ? Make sure that module is loade . Also are you sure that there is no problem with cable since its showing link down ?

---

### Post by NoWayBill on 2007-12-25
There is no hardware problem, the NIC works fine in Fedora and XP.
XP restarts the NIC automatically, Fedora simply requires "ifup eth0", after booting from Ubuntu.

Results of lsmod, lspci & lspci -n.
According to log files "r8169" (in lsmod) refers to the card I need to run.
In compairing these aren't we looking at apples and oranges?
I mean, a 32-bit Fedora install to a 64-bit Ubuntu?

I have never had to edit kernel mods, so bear with me.
Any logs anyone would like to see?

---

### Post by NoWayBill on 2007-12-25
Strange how it works booting from live cd (that installed from)
here are the same tests as above from cd boot.

---

### Post by misterhead on 2008-03-27
Strange. I have 2 hard drives for my laptop. 1 dual boots XP pro and Hardy. (previously Gutsy) with no network issues. Installed Gutsy Studio on the other and it seems to only be pulling a loopback "169" ip. (no network).

---

