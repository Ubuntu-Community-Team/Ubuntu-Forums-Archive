---
title: "Video, Audio, and Wifi Problems"
date: 2006-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by steelspyder on 2006-07-05
I have used Ubuntu for almost a year now, but only on intel xeon computers at work with little or no issues at all.  I recently purchased a HP AMD64 4200+, 2gig RAM, 250gb SATA HD, NVIDIA Integrated Video, 5.1 integrated Digital Audio.  The system came with XP Media Center on the 250gb SATA HD.  I added a Linksys WMP54G PCI Network Adaptor.  I then purchased a Maxtor 300gb SATA HD and installed Ubuntu 6.06 on the second HD.

My first minor problem was that the install was not visible at first on my HDTV.  So I had to temporarily plug in a CRT PC monitor to do the install.  After the install was complete I then swapped out the CFT Monitor for my HDTV VGA connection.  Here is where my major issues begin.

1.)  I have the video resolution set on the highest setting but, it is only a 4:3 resolution.  Is it possible to enable higher resolutions so that I can have a wide-screen display that is not all distorted?

2.)  I have the computer connected to my Home Theatre Reciever with the digital coaxial audio cable.  I do not get any sound from the Ubuntu OS.  Do I have to activate the sound through Ubuntu to recognize this connection?

3.)  Probably most important.  I do not have a wired network connection in this room.  I have installed the Linksys WMP54G PCI adapter.  It works fine with Windows.  In Ubuntu it shows up as Ra0 network DISABLED.  I have tried to activate it.  When I use the gui and click properties in the network settings the computer hangs and I am forced to manually cycle the power on the machine.  I have read all sorts of conflicting reports on how to get wireless networking working.  This adaptor is advertised to work with Ubuntu "out of the box".  Does it work with the 64bit version?  How can I activate it and get it up and running?  I have WPA security on my network.

Thank you in advanced for any help you can provide with these issues.

Mike

---

### Post by steelspyder on 2006-07-05
I also forgot to mention that the AMD 64 4200+ is a dual core processor.  Is Ubuntu able to take advantage of the dual core technology by default?  Or do I need to activate this feature in a system setting or with an install?

Thanks again.
Mike

---

### Post by steelspyder on 2006-07-06
I was able to get the audio working using alsamixer.

Still no luck on the wireless networking or the video issues though.  I think I will be able to get the video working better once I am connected to the Internet and can install updates.  For now I am stuck switching back and forth between Windows and Ubuntu to seek advice though.  I try something in Ububtu and then I have to switch back to Windows to do some more research on the Internet.  Find another suggestion and reboot back into Ubuntu to try it.  This cycle is getting annoying.

I really wish I could get the Internet running through Ubuntu.

Any Ideas?

---

### Post by Teroedni on 2006-07-07
> 3.) Probably most important. I do not have a wired network connection in this room. I have installed the Linksys WMP54G PCI adapter. It works fine with Windows. In Ubuntu it shows up as Ra0 network DISABLED. I have tried to activate it. When I use the gui and click properties in the network settings the computer hangs and I am forced to manually cycle the power on the machine. I have read all sorts of conflicting reports on how to get wireless networking working. This adaptor is advertised to work with Ubuntu "out of the box". Does it work with the 64bit version? How can I activate it and get it up and running? I have WPA security on my network.


I have had the same problem eith the gui freezing. Its seems the linksys wireless have lots of problems with ubuntu. To make mine partially working(Unstable driver its disconnect with too much load:evil: )

```
sudo gedit /etc/network/interfaces
```

that will show the configured cards
Mine looks like this(i have wusb54g ver 4 rt2570 module)

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid linksys
wireless-key  xxxxxxxxx




The last line i have added myself 
My wusb54g have the name rausb0 .
This is for wep. Wap require some more work as far as i know

---

