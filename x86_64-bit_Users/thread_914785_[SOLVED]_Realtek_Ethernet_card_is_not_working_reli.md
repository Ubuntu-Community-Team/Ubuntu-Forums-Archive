---
title: "[SOLVED] Realtek Ethernet card is not working reliably"
date: 2008-09-09
forum: x86 64-bit Users
---

### Post by Idefix82 on 2008-09-09
I have just installed Ubuntu 64bit parallel to WinXP. When I first boot Ubuntu, the internet connection works (over DHCP). Then I install the required updates, restart, boot Ubuntu again and the ethernet card does not work.
This is the relevant output from lshw:
*-generic
  description: Ethernet interface
  product: Illegal Vendor ID
  vendor: Illegal Vendor ID
  physical id: 0
  bus info: pci@000:07:00.0
  logical name: eth0
  version: ff
  serial: *my MAC address*
  width: 32 bits
  clock: 66MHz
  capabilities: bus_master vga_palette cap_list ethernet physical
  configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=255 maxlatency=255 mingnt=255 module=r8169 multicast=yes

I have read elsewhere that I should enable wake-on-lan after shutdown under Win XP which I have done, but this evidently didn't solve the problem. Moreover, when I shutdown the computer, unplug the cable for half a minute and start Ubuntu again, the internet still doesn't work.
Your help would be much appreciated!

---

### Post by Idefix82 on 2008-09-09
An update: I just realised that I had Wake-on-LAN disabled in the BIOS. I enabled it, started Windows once more, after that Ubuntu (without unplugging the cable and so on) and the Ethernet card works. I will report back later if it stops working again.
I should also mention that the Ethernet card is an RTL8168C/8111C

Request to MODS: Maybe you could move this thread to the hardware and laptop section if it seems more appropriate. Thanks!

---

### Post by Idefix82 on 2008-09-18
In case, anyone is interested, this page describes the solution to my problem:
[http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html")

---

