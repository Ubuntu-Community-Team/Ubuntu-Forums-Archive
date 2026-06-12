---
title: "Gateway T1620 - Realtek rtl818B - Sound - 64bit Flash"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bright Hammer on 2008-01-28
My old laptop died last week and I bought a new Gateway T1620 (See the specs below). I have spent all weekend trying to get it to work properly with mixed success. So to help anyone else out there with the same laptop or similar hardware I am starting this thread. I still need a couple of things worked out however so I am asking for the experts on this board to help me out. Below is a quick step by step of what I did from a clean install.

T-1620 Notebook Specifications
Part Number: 1014881R Gateway T-1620 Notebook
AMD Turion™ 64 X2 Mobile Technology TL-56
1.8 GHz | 512 KBx2 L2 Cache 
HyperTransport™ technology at up to 1600 MHz) 
Chipset ATI RS690T 
Display panel 14.1-inch WXGA TFT display (1280 × 800) 
Memory 2048 MB 667 MHz DDR2 SDRAM (2 × 1024)
Total slots: 2 DDR2 slots | Available slots: 0 DDR2 slots 
Video controller ATI Radeon® X1270 graphics		(Working)
Up to 256 MB of HyperMemory™ 
Webcam 1.3 Megapixel 					(Not Working)
Audio High definition audio - 2 channel 			(I have sound but sure it is HD)
Hard drive 250 GB 5400 RPM SATA hard drive 
Optical drive 8X Multi-Format Dual Layer DVDRW with DVD-RAM and Labelflash™ 
Modem Integrated V.92 56K modem 				(not tested)
Network 10/100 Ethernet LAN				(Working)
802.11a/b/g Wireless LAN 					(Not working RealTek rtl8187b- built in but connected via USB)
Memory card reader 5-in-1					(Working)
Interfaces Three - USB 2.0 ports 
One - VGA port 
One - HDMI connector 					(Working)

[COLOR="Blue"][SIZE="5"][SIZE="5"]Video[/SIZE][/SIZE][/COLOR]
I installed Ubuntu 7.10x64. When it came up I went out and got all the updates via update manger. I then installed Automatix and got the restricted codec’s installed along with Nautilus scripts( This is a must have if you aren’t great with command line editing i.e. gedit root and Nautilus root). Now let’s get the video card working to get some eye candy.

1.	You should have a restricted drives icon in the tray click it and select use restricted drivers.
2.	The user Nautilus to go to Filesystem\ect\x11\ and look for xorg.conf 
3.	Right click and select gedit root and go to the bottom of the file. Composite should be set to 0 change it to 1 save and close
4.	Open synaptic package manager and do a search for xservre-xgl and select it to be installed
5.	Do a search for compiz and install compizconfig-settings-manger and select it for install and hit apply 
6.	When it is done reboot 
7.	When it comes back up enable desktop effects and you should be up and running.

[COLOR="blue"][SIZE="5"]Sound [/SIZE][/COLOR]
I found this trolling the forums for help with sound after I tried compiling from source and running scripts that didn’t work and only served to cause more problems. Thanks to trjnhrse44 for posting this. Here is the link to the post if you have more problems but all you need to do is type the following in a teminal.  [http://ubuntuforums.org/showthread.php?t=588285](http://ubuntuforums.org/showthread.php?t=588285)

Code:
sudo apt-get install linux-backports-modules

[SIZE="5"][COLOR="blue"]Wireless ( rtl8187B)[/COLOR][/SIZE]
I have tried everything I but I can’t get this to work. So and some one help me by posting a step by step fix? It is a RealTek RTL8187B, in my laptop it is connected via USB so that is why I have been having problems using some of the guides in the forum. I got ndiswrapper to see it with a win 98 driver but it dosent show up in network manger. I tried to edit \ect\network\interface by adding wlan0 but still nothing.

[SIZE="5"][COLOR="blue"]Firefox[/COLOR][/SIZE] [COLOR="Blue"][SIZE="5"]*UPDATE!*[/SIZE][/COLOR]
I got flash working on my laptop now. Here is the link. Thanks to Kilz for the awesome script. Use the r48 plug in script. Works like a charm.

[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash)


[COLOR="blue"][SIZE="5"]WebCam[/SIZE][/COLOR]
I can’t get this to work so again please help me out. My buddy has a MacBook with a web cam with a nice feature which I am looking for in Linux. When someone trys to log in but gives an incorrect pass it takes a picture of the individual. If connected to the net It will send an email whit the pic of the unauthorized user. Does Linux have anything like this? I would be a nice feature.

[COLOR="blue"][SIZE="5"]Modem[/SIZE][/COLOR]
I have not tried I don’t need it but someone else might so if you have info on this that would be great.

So PLEASE can some one help me out to get my system running properly 

Thank you in advance 

Bright Hammer

---

### Post by Catholicnerd on 2008-01-31
I've got a T1620 running Gutsy as well, and I'm also having trouble with the Wireless adapter.  After spending several hours working on finding a fix, I'm looking at just buying a wireless card for the ExpressCard slot.  Have you tried that yet?  I know it's not ideal, but I am under the impression that the proprietary drivers for Realtek wireless adapters just aren't that well-developed yet.  

On the Compiz front:  my advice is that if you plan to do ANY 3D gaming at all, stay well away from it because of the state of the ATI drivers.  If you really like the Compiz effects, be prepared to switch back to a normal X session when you want to play a game that requires Direct Rendering.  It's an annoying reality, but hopefully it won't be for much longer.  

Sound isn't working for me either, but again I'm looking at a possible non-integrated solution.  It looks as if Creative does plan to support the X-Fi laptop cards.  Take a look at their Opensource development page. [http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

---

### Post by Catholicnerd on 2008-01-31
I just found this thread and am proceeding with the installation instructions.  [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

---

### Post by Bright Hammer on 2008-01-31
Thanks for the link for wireless. I tried it but was unable to get it to work for me. Let me know how you do. Sound is working but not properly. I have to keep the volume all the way up to hear anything. I am thinking of going to Hardy alpha and see how that works for me. I am running compiz but notice that it hangs a lot especially when you switch users. I hope someone post a deb package for the new catalyst drivers just released. 


FYI 	I did get my webcam working by installing cheese. However I cant get it to work for desktop users you have to be an admin. I am looking into it more however.

---

### Post by Catholicnerd on 2008-02-01
> **Bright Hammer said:**
> Thanks for the link for wireless. I tried it but was unable to get it to work for me. Let me know how you do. Sound is working but not properly. I have to keep the volume all the way up to hear anything. I am thinking of going to Hardy alpha and see how that works for me. I am running compiz but notice that it hangs a lot especially when you switch users. I hope someone post a deb package for the new catalyst drivers just released. 


FYI 	I did get my webcam working by installing cheese. However I cant get it to work for desktop users you have to be an admin. I am looking into it more however.

Thanks for posting about Cheese.  It's nice to know that I can use my webcam if I absolutely NEED to.  Unfortunately the ATI drivers are so BAD that I don't think I'll be that desperate anytime soon. 

The wireless driver install failed for me, too.  I caved and bought a Belkin Wireless G USB Adapter.  It worked right out of the box without having to resort to using ndiswrapper trickery!  I absolutely *have* to use this machine in the field, so spending another day dinking around with the wireless driver was not an option.

---

### Post by Catholicnerd on 2008-02-05
Great news on the sound front!  After installing the backports, sound is working.  I've discovered that the volume problem is due to the fact that the "Front" speaker isn't listed by default in the mixer menu.  Add it, turn it all the way up, and you'll be able to adjust the volume normally from there. :)

---

### Post by Bright Hammer on 2008-02-07
Thanks for the tip! Sound is working much better now. :KS

---

### Post by jdos2 on 2008-02-07
For Wireless, search for the "rtl8187b-modified" tarball and compile THAT. It's how I got my USB attached internal wireless working on my Toshiba.
Bringing it up is a manual process, but it's good enough as it is.

---

### Post by Bunnywinkles on 2008-03-09
I got my cam working. Only works with Ekiga as far as i know. If you google getting the "Acer crystal eye webcam ubuntu" there are ways to get it working, seeing as this is all the cam is. but to get it working goto Ekiga Edit>Prefences>Video Devices and use the V4l2 plugin. Should work then.

---

