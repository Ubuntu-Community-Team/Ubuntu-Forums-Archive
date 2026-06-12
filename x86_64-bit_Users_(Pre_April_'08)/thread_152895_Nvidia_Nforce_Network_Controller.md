---
title: "Nvidia Nforce Network Controller"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by antd on 2006-03-30
The motherboard is ASRock K8NF4G-SATA2 and the problem is to do with the onboard ethernet. 
Eth0 is found but I have no internet connection because I need to install the chipset ethernet driver first.
This is also the case with windows xp, I must install the chipset drivers before I can use the ethernet.

How can I install the drivers for my chipset?

If it's possible I will paypal the person who is willing to help me as a gesture of good will.

Thank you.

---

### Post by mikalh on 2006-03-30
[QUOTE=antd]The motherboard is ASRock K8NF4G-SATA2 and the problem is to do with the onboard ethernet. Eth0 is found but I have no internet connection because I need to install the chipset ethernet driver first.[/QUOTE]

Mostly a guess, but if it's found eth0 then the driver should be installed. The nforce 4 ethernet driver was installed for me on Breezy automatically, though I've been using Dapper for a while now.

It could be a network configuration problem. What's your networking layout - routers, modems etc?

What output does 'ifconfig' give?

---

### Post by antd on 2006-03-30
I have a router, my pc is connected to it via ethernet cable and the router is connected to adsl.

It's weird because someone told me to put these as my settings (I told him all the settings I have:

"for IP put 192.168.2.5
for broadcast put 192.168.0.255
for network mask put 255.255.255.0
for gateway put 192.168.2.1
for nameserver put 192.168.2.1 or 80.225.252.58 "

With these settings my router's LED doesnt even flicker with activity. It has always been like this, even with exact same settings as my windows box.

Do you have any suggestion on what I should do?
Or should I just stick with using windows xp?

---

### Post by mikalh on 2006-03-30
Again, what output does 'ifconfig' give? That will tell you whether the network card is installed, and its settings.

if you could also give the output from 'ipconfig' (this time 'ip' not 'if'!) on Windows XP - while it's connected - that would be good.

---

### Post by antd on 2006-03-31
Here's the result of ipconfig in windows:

Ethernet Adapter LAN connection:

Connection-specific DNS Suffix . :
IP Address: 192.168.2.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1

Ubuntu uses different names/settings and therefore probably confuses me into putting in the wrong settings.

Hope you can help :)

---

### Post by mikalh on 2006-03-31
Those settings roughly correlate with what your friend told you :) - how did you enter them into Ubuntu?

Somewhere in one of the settings submenus off of the gnome panel at the top of the screen is somthing called 'networking' (it's moved for Dapper). Have you put the settings into that, including the nameserver/DNS, and made sure the connection is activated?

Also -- forgot you couldn't copy/paste 'ifconfig' output from Ubuntu. Run it anyway, and look at the output. It should have both 'lo', the loopback, and 'eth0', the ethernet.

For eth0, if it's running it should say the "inet addr", "Bcast" and "Mask" with which it's configured. These should match what your friend said. It should also say something like
UP BROADCAST RUNNING MULTICAST

---

### Post by antd on 2006-03-31
[QUOTE=mikalh]For eth0, if it's running it should say the "inet addr", "Bcast" and "Mask" with which it's configured. These should match what your friend said. It should also say something like
UP BROADCAST RUNNING MULTICAST[/QUOTE]

Yes it says that. It is active. However, in the real world it is not active. I am confused with what "broadcast address" means...

I'm going to install ubuntu again on a different partition. I'll try the settings again and let you know what happens.

---

### Post by antd on 2006-04-01
mikalh:

ifconfig gives my settings. Here are the values:

RX packets: 82
txqueuelen: 1000
RX bytes: 4920
Interrupt: 23

All other values are 0. My settings are correct.

I am so convinced that I need to install my chipset drivers. I think this because I have to even disable my graphics card to enable the xserver. Otherwise I'm stuck with command line.

Can you please help me to install my chipset drivers?
I have the linux version of the drivers on a DVD. How can I go about installing them. As you know I'm new to linux :)

---

### Post by Jason_25 on 2006-04-01
No you do not need "chipset drivers".  What's the problem?  Can you ping your gateway or not?

---

### Post by antd on 2006-04-01
No I cannot ping my gateway. 100% packet loss.

The problem is like all my chipset drivers (Ethernet, Graphics and Sound) are not working within Ubuntu

I am sure I need to install those drivers? The things that don't work:
Graphics, Sound and LAN

The thing I can install with chipset drivers:
Graphics, Sound and LAN

Any suggestions?
My internet settings are exactly the same as within windows, which I am using to type this out.
I'm gonna load up my nvidia drivers on a usb drive and see if I can install them. Last time I tried I got an error saying binutils wasn't found V_V.

Edit: As you can see here:- [https://launchpad.net/distros/ubuntu/+ticket/385](https://launchpad.net/distros/ubuntu/+ticket/385)
It seems like my mainboard isn't supported. What does this mean? I cannot use ubuntu?

---

### Post by mikalh on 2006-04-01
Well, if you're reinstalling, you could try Dapper flight 6. It's very stable; I've been using Dapper with no problems since mid February. As your motherboard is probably more recent than Breezy itself, this might be more successfull. 

I'm afraid I'm stumped if the network card settings are correct.

---

### Post by antd on 2006-04-01
Ok, thanks for your help. :)
I downloaded Dapper flight 6 from here [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

I really hope my motherboard is supported! :P

Another question:
Do you know the command to allow me to install the kernel source files? (aka kernel source packages)

---

### Post by Twinsen on 2006-04-02
I installed badger yesterday and have exactly the saem problems i have a nforce 4 DFI motherboard and an x800GTO2 I also neeeded to run my grapohics in vesa and canot access the internet at all have checked all my settings but they are the same as windows. It seems the answer is to get dapper right?

---

### Post by antd on 2006-04-03
I just installed Dapper. It fixes the graphics problem.
BUT
There's still no support for internet (LAN) or sound. I hope Dapper will fully support my board!!

Will Dapper fully support my baord and my wireless card too? Many people have this problem. surely the Dapper developers will take this into account.

---

