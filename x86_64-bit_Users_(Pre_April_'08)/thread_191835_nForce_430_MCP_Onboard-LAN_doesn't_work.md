---
title: "nForce 430 MCP Onboard-LAN doesn't work"
date: 2006-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by 8200 on 2006-06-08
The onboard-Gigabit-NIC of my nForce 430 MCP doesn't work. I have already tried via DHCP and static IP. No way.

If anyone has an idea... please!

---

### Post by ipa on 2006-06-08
Are you dual booting to windows?
If so, you will need to to turn off your computer at the wall for 20 seconds or so before booting into Ubuntu.

Ivan

---

### Post by Hendrik van den Boogaard on 2006-06-08
At my Asus A7N VM CSM it works just fine, no problems at all. What motherboard do you have? Does assigning a static IP work?

---

### Post by 8200 on 2006-06-09
Yeah I'm dualbooting with windows.

Will try to boot Ubuntu next time after more then 20seconds of windows-shutdown.

---

### Post by 8200 on 2006-06-09
What exactly do you mean with "at the wall for 20 seconds" ?

---

### Post by Tarhan on 2006-06-09
Cause of ploblem is kernel's build-in freeware driver (it's called **forcedeth**). You have to install **nvnet** driver from Nvidia. It works fine with windows.

---

### Post by daffy256 on 2006-06-09
Hi there. I'm having a similar problem with my Gigabyte GA-K8N51GMF-9 motherboard which has a nForce 430 MCP /Vitesse 8201 phy. When I first installed ubuntu 6.06 (as dualboot to Win XP Prof), I immediately got the network up and running. I surfed around on the web but when I pressed the Update button it failed. I eventually found out that i couldnt even ping my router any more (I use static IP). I've tried all I could think of with no success, including rebooting a number of times, switching to DHCP and back, cutting the power at the wall...

Ifconfig reports something *like* (this is pasted on another machine) 

eth0      Link encap:Ethernet  HWaddr 00:E0:29:88:08:55
          inet addr:172.18.18.1  Bcast:172.18.18.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe88:855/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:  0 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1593311 (1.5 MiB)  TX bytes:326677 (319.0 KiB)
          Interrupt:5 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:927612 (905.8 KiB)  TX bytes:927612 (905.8 KiB)

No errors, no overruns but a number of packets dropped.
What causes the TX packets to be dropped. 
Any clue will be appreciated. 

Daffy

---

### Post by ipa on 2006-06-11
[QUOTE=8200]What exactly do you mean with "at the wall for 20 seconds" ?[/QUOTE]
I mean physically turn off the power coming to the computer, either by switching of the power where the power lead comes from (wall plug or power strip etc.) or you may find a switch at the back of the computer. It seems windows sets something in the network chips rom which resets when the power is removed from it completely.

I had no luck installing nvnet drivers.
Hope this helps.

Ivan

---

### Post by ipa on 2006-06-11
Daffy, type lsmod into a terminal, and see if the forcedeth or nvnet module is loaded

---

### Post by lnxconvrt on 2006-06-11
I have the same mobo as Hendrick van den Boogaard, also working fine using the forcedeth kernel module.

I have been using Dapper on AMD 64 for some months now.  I've been using "acpi=off" as a kernel option, as I believe that at one time I found it necessary.  Otherwise after a few minutes networking would die.

So you might try that and/or possibly the nolapic and noapic kernel options in your /boot/grub/menu.lst.  Making a backup copy is not a bad idea, since this is a critical file for booting.

Here is one example line from mine:
kernel          /vmlinuz-2.6.15-23-amd64-generic root=/dev/mapper/vg0-root ro acpi=off quiet splash

You probably have a similar line for at least one kernel, and can just add the acpi=off.

You can also interupt the boot sequence and add kernel options manually to the default ones to test them before editing menu.lst.

---

### Post by 8200 on 2006-06-13
Thank you ipa - shutting the pc down for 20seconds and then using Ubuntu works fine (default driver - nothing changed).

---

### Post by netztier on 2006-06-13
[QUOTE=lnxconvrt]So you might try that and/or possibly the nolapic and noapic kernel options in your /boot/grub/menu.lst.  Making a backup copy is not a bad idea, since this is a critical file for booting.
[/QUOTE]

On my Shuttle SN95Gv3 (nForce3 Chipset), nothing short of adding the "noapic" kernel option would help. Neither *nvnet* nor *forcedeth* would work; only **sk98lin** was good, **if** noapic was set as kernel option in grub.lst

kind regards

Marc

---

### Post by hantsy on 2006-06-14
The same problem here.
My motherboard is GigaByte C51(GForce6100+MCP430)&#12290;I&#12288;use a static IP.
The network did not work.
When I installed the official driver ,It works well .
Firstly ,install build tool from cd rom ,and  the run the downloaded file. 
sudo sh NFORCE-XXX.run
It will install the network driver and the audio driver .
Reboot the computer .
That is all.

---

### Post by 8200 on 2006-06-15
On my A64 PC running final Dapper Drake (with all updates) everything is default and works fine.
The only thing you have to keep in mind, if you are using Dualboot with Windows, is to shutdown the PC for 20seconds and take it from current.

---

### Post by kronick on 2006-10-29
if i add acpi=off linux doesn't boot

---

