---
title: "A bizarre wireless nightmare ubuntu 64 7.10, Belkin 802.11G USB"
date: 2008-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by wishful9 on 2008-04-21
Recently converted to ubuntu 64 from windows xp.  totally fed u with performance and microsoft's business practices and future outllook.

Thought myself as somewhat of a competent user, advanced to some extent.  with ubuntu i'm slowly getting there but initially i was like a rabbit in headlights.

Started out with internal wireless and trying to get that to work but gave up it's a nightmare.  I have a HP Pavillion zv5000 series laptop, specifically zv5255EU.  

This contains the Broadcom 43xx wireless card, actually 4303 rev2.  couldn't do with various techniques, updates and then fwcutter restricted drivers and then ndiswrapper which in ubuntu 64 requires some work anyway got nowhere.

Anyway updated system via wired connection and resigned to buy the wlan adapter Belkin 802.11G USB, as it was the cheatest and listed as compatable with ubuntu 64.

To my surprise and delight it worked out of box, perfect.  however i tried to set up media server with playstation 3 and other windows xp. namely fuppes, cups and samba.  however i had no idea what i was doing and installed about a million libraries, plugins. ended up with web server, sql server and three media servers.

i descided to start again updated via wired connection, installed some inoccuous software and then nothing.  the dongle doesn't work.  arrgghh.

i've tried a few things and some results are attached.

1.  help please, it doesn't appear to be turned on from the results.

2.  do i need to disable the broadcom wireless? and how?

3.  ifup and ifdown didn't work and i'm a bit clueless.

4.  i've read a bit about rt73 drivers but i'm not convinced, with it working perfectly in revious install.

5.  Where can i ind a list of sudo and general commands and terminal functionality, in idiots english.  i know there is probably a forum HOWTO but i've missed it.

6. step by step solution would be wonderful.

I apologise if attachments aren't displayed in text body but i can't do any coding, building fuppes the first time was as close as i get at the minute.  Thank you very much in anticipation.

Simon

[ATTACH]66672[/ATTACH]

[ATTACH]66673[/ATTACH]

[ATTACH]66674[/ATTACH]

[ATTACH]66675[/ATTACH]

---

### Post by wishful9 on 2008-04-22
bump

---

### Post by wishful9 on 2008-04-22
Seems to be working with serialmonkey rt73 driver fix but currently having wpa problems.

was reluctant to use rt73 as with f5d7050 there's alot of conflicting information out there about chipsets and version number.

will play arround.

thanks anyway

---

### Post by wishful9 on 2008-04-23
fully functioning

gksu gedit /etc/modprobe.d/blacklist

[ATTACH]66918[/ATTACH]

in the end i didn't need the serial monkey rt73 driver i just needed to blacklist rt2500usb; and then rt73usb works fine!!!

---

### Post by usernamed on 2008-04-25
Hi Wishful,

I have what (theoretically) is the same card but I'm not mirroring your success.  I have the Belkin F5D7050 (revision E) which when I run 'lsusb -v' gives me:

```
Bus 007 Device 006: ID 050d:705e Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705e 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1

```

I'm dual booting and the device works fine in WinXP so I'm struggling to understand what's going on.  I've blacklisted the modules you've suggested and still no joy.  Any advice would be very much appreciated.

ifconfig shows nothing but loopback and eth0: (my wired connection)

---

### Post by wishful9 on 2008-04-29
[http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=283](http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=283)

tells you how to work out version number, if you look on the underside fcc id, really small text.

most of the belkin f5d7050 contain ralink chipset  but i think version two and four contain zydas.  have a google and download drivers, i think from atheros, and use ndiswrapper. if it's not the ralink chipset.

if you use ifconfig -a you should get all the interfaces.

---

### Post by wishful9 on 2008-04-29
if you follow the serialmonkeys advice.  [http://backports.ubuntuforums.com/showthread.php?t=400236](http://backports.ubuntuforums.com/showthread.php?t=400236)

if your version is ralink chipset.  it should work.  remove copied blacklist and start from scratch in regard to what you added. i've blacklisted the serial monkeys driver rt73 and bcm43xx.

the bcm43xx is for a crap internal wireless from broadcom, couldn't be bothered to even look at it displayed in network manager it frustrated me that much. it may be unecessary to blacklist this for yourself.

the serialmonkeys guide and driver is excellent and works stabaly.  the only thing is that wpa isn't supported and i don't think wep is secure enough.

i played around with that drivers were loaded and found the rt73usb worked fine if the rt2500usb wasn't loaded.  hence the solution to my problem.

recently though i've found that the stability of my fix isn't there.  it's ok if you're constantly useing the connection but left on it's own, connection is lost and when trying to mediaserve to ps3, it just gives up.

so i suggest if the chipset is correct for yourself follow the letter of the above guide.

i'm just gonna have to put up with wep and mac address filtering.

---

### Post by wishful9 on 2008-04-29
i am far from knowing what i'm doing so don't expect great things. but i am happy to help and advise if i can.

---

