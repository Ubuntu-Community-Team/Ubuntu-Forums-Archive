---
title: "Ubuntu 64 login problem at MSI S270 notebook"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Spippo on 2005-11-20
Hi,

I installed ubuntu 5.10  (64-bit) at my msi S270 mega book. The installation went realy great and smooth, but i have a problem with the login.
When i start my notebook and select Ubuntu, it loads a bit and then gets into the login screen.
Here I can enter my username and my password, and then it loads a small image of ubuntu and tries to log me in. My notebook loads for a few seconds, and then it doesn't do anything. I cant even move my mouse anymore, CTRL-ALT-DEL doesn't work. The only thing I can do is to press my power button a few seconds so that it shuts down the hard way.
I can startup in recovery mode so that i use the text mode and explore my HD and do my normal commands. Even when i use Xstart, it gives my the same problem, i cant even close it with CTRL-backspace.

Anyone have the same problem? Or anyone knows a good solution?
Sorry for the spelling errors, but im not English.

Here are the specs for my notebook:

Processor type:  AMD Mobile Processor Turion64 MT30 1,6 GHz
Chipsets: ATi RS480M + ATi SB400
System memory: 512Mb
LCD: 12.1" TFT WXGA
Graphics & Video Module: ATi RS480 (Integrated Graphics)
Audio: AC'97 2.2, SoundBlaster compatible
HDD: 80GB
Optical Drive:  CD-RW Combo/DVD Dual/ DVD Dual Layer
Communication Ports:
-Built-in 10/100Mbps Ethernet LAN & Modem Module
-Built-in 802.11 b/g WLAN card
-Bluetooth supported
I/O Port: 
-VGA Output (D-Sub, 15-pin) *1
-USB2.0 Port *3
-IEEE1394 Port *1
-Micro Phone Input *1
-Head Phone Output *1
-Modem Port *1
-LAN Port *1

---

### Post by Aphorism on 2005-11-20
You can thank the lovely proprietary close source idiots at ATI for that I think.

The RS480 has an evil ATI Xpress 200 onboard graphics chip (if it is the same as a motherboard I threw out the window vowing never to support ATI again.)  ATI doesn't seem to want to support all of their cards, so you are stuck with a half baked card for display.

If you boot into your little recovery mode (hitting escape during the grub boot and selecting recovery mode), the following MAY fix your problem:

[list]
[*]Boot to recovery mode (ESC during grub loading at boot)
[*]Logged in as root, use a text editor to manually edit the file /etc/X11/xorg.conf file.  The line in question we are looking for is under the section "Device".  It reads
```

      Driver        "ati"

```
[*]Change the above line to read
```

      Driver        "vesa"

```
[/list]

To round things out, send some hatemail to ATI and beg them to support truly opensource oses -- to help not only Linux, but OpenBSD, FreeBSD, and the like.


I sincerely hope this helps.

---

### Post by bonzodog on 2005-11-21
Yep, i'd agree with that. looked at the specs, saw the letters 'ATI' and went, 'there's his problem'. Evil graphics card and chipset my friend.....

---

### Post by Spippo on 2005-11-21
Wow,

was that all? Just that one line and my Ubuntu started realy great.
Aphorism you are the best !!!!! :KS 

Now the only thing i have to do is to make sure all my other drivers work and the most important: To send that hatemail to ATI :D 


Thank you very much


Spippo

---

### Post by Aphorism on 2006-01-13
Glad to have helped.  

Please note when sending mail to ATI -- don't request Linux support solely -- that doesn't help us.  If another operating system comes out, and you choose to run it, you should be entitled to use the hardware.


We need open documents and specifications.  Let's take the momentum of Ubuntu and try to make a serious dent in computing.  Lean on ATI and Nvidia.  One might just crack and become the first vendor to have fully open and transparent 3D.

The implications are huge -- *every* operating system currently out there and, most importantly **to come**, would have access to 3D accelleration if their designers choose to write drivers for the given card.

---

