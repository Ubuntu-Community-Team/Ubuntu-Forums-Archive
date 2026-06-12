---
title: "Problem with wusb600n"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by MacJ_007 on 2008-04-27
I recently updated from 7.10 Gutsy Gibbon to 8.04 Hardy Heron.  And at the same time upgraded from wusb54g to wusb600n.  I followed the same instructions on how to install wusb54g using ndiswrapper, but with no success.  I googled everywhere but I don't have any similar problems.

When I typed:  sudo modprobe -r netr28ux

I get these message: 
FATAL: Module netr28ux not found.

If I type: ndiswrapper -l

I get these messages:  
netr28ux : driver installed
	device (1737:0071) present

The driver is installed properly but the device is not blinking at all.  Any suggestions I would really appreciate it.  Thanks.

---

### Post by kevinmedina on 2008-05-17
I just bought the same adapter and am struggling to get this working (one computer is FF and the other is GG).  Any help would be appreciated!!

---

### Post by DataKnutten on 2008-06-09
One "geek" got it working using ndiswrapper. See this:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/)

---

### Post by bcavagnolo on 2008-06-19
Hello,

I was just googling around for fixes for this same problem.  I discovered that the WUSB600N has a Ralink chipset [1] and knew that Ralink provides Linux drivers for their hardware [2].  So I ran out and bought a WUSB600N.  But when I plugged it in, it didn't work.  Here's what I discovered:

The GPL'd Ralink vendor driver [3] that supports the chipset does not list the WUSB600N's vendor and product codes.  I discovered those with lsusb:

$ lsusb
...
Bus 001 Device 004: ID 1737:0071  
...

and added them to the table in the driver source (rt2870.h line 126.)  I also had to reconfigure my kernel to turn on NET_NS, which the driver seems to require.  Unfortunately, this option requires sysfs to be off!  After that, I was able to build and use the driver as directed in the README.

Anyhow, some other Ralink chips (rt2400 and rt2500, I think) are supported in the mainline kernel [4].  I don't know if anybody is planning to add support for the rt2800 chips.

Ciao,
Brian

[1] [http://www.wildpackets.com/support/downloads/drivers](http://www.wildpackets.com/support/downloads/drivers)
[2] [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
[3] [http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2)
[4] [http://www.linuxwireless.org/en/users/Drivers/rt73usb](http://www.linuxwireless.org/en/users/Drivers/rt73usb)

---

### Post by markackerman8@gmail.com on 2008-08-07
Thanks for the link to the driver 

[http://www.wildpackets.com/support/downloads/drivers](http://www.wildpackets.com/support/downloads/drivers)

as I could not find it anywhere, pheww... but as a newbie of course it seems that I cant get my WUSB600n working

HELP!!!????

points to consider

my USB300n is working fine with ndiswrapper
I installed the ralink_usb2870 with ndiswrapper and it says,

rt2870 : driver installed
	device (1737:0071) present

and the device is listed in lsusb (though without any description..i.e...

Bus 006 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 002: ID 1737:0071  

and in $ dmesg,  I get...
[  406.971325] ndiswrapper (load_wrap_driver:112): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'


Any suggestions for a newbie
(and if anyone by the way has there rtl8187b (rtl8197) inboard usb device functional with wpa, I would love to know so this would be unnecessary)

Thanks for the help Ubuntu helpers, you are why I am sticking it out to get away from WINDOWS!!

Mark

---

### Post by markackerman8@gmail.com on 2008-08-12
Well NO Responses, so I will update my problem, I have had success with the WUSB600N with the XP driver it comes with on disk and ndiswrapper but it is unstable when in WPK1 encryption mode and stops receiving after a short time of any slightly aggressive load.

I would like to point out that I tried the Ralink usb2870 driver and ndiswrapped crashed trying to install it??? any suggestions anyone,

Thanks in advance, Mark

---

### Post by MaindotC on 2008-10-03
I just got [WUSB600N](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175243256159&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5615933028B08) today becaue my campus bookstore sells it and I have 5 days to test and return it.  I used ndiswrapper and installed the [XP64 rt2870 driver ](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1175239737731&packedargs=sku%3D1175239525540&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3773125540B03&displaypage=nodata#versiondetail)and I'm running it on the platform specified in my sig and it works wonderfully!  Before I was using the [Belkin F5D7050](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211) adapter w/ the Very fast on-campus and I did a speedtest.net so you can see the difference:

Belkin F5D7050:
[[IMG]http://www.speedtest.net/result/333220650.png[/IMG]](http://www.speedtest.net)

Linksys WUSB600N
[[IMG]http://www.speedtest.net/result/333408454.png[/IMG]](http://www.speedtest.net)

---

### Post by MaindotC on 2008-10-04
Update - I've been having some difficulties.  It looks like (I'm speculating) after a period of inactivity it will go into some sort of sleep mode and I've difficulty getting it out of that mode even after a reboot.  I rebooted w/ the Belkin plugged in so I'll plug the Linksys back in and try different drivers.  Maybe the Vista 64 or maybe I shouldn't even use a 64-bit driver.

---

### Post by mizunoX on 2008-10-06
> **strAlan said:**
> Update - I've been having some difficulties.  It looks like (I'm speculating) after a period of inactivity it will go into some sort of sleep mode and I've difficulty getting it out of that mode even after a reboot. 

As odd as this sounds, I think your problem will be solved with the use of an externally powered USB hub.

I had this same problem in Windows and Linux with several different Wireless-N cards (including your linksys) and found support on other forums suggesting to move it to it's own powered USB hub.  Worked instantly and hasn't disabled itself since.  I think it's a hardware thing, not a linux thing.

---

### Post by MaindotC on 2008-10-10
Which one did you buy?

---

### Post by mizunoX on 2008-10-15
> **strAlan said:**
> Which one did you buy?


I still have a belkin N that I forgot to return, and I'm currently using the Linksys wusb600n.

I found a site that gave instructions for downloading the chipset driver and compiling it for use with this card.  So I'm not using ndiswrapper anymore.  Perhaps you should give that a try.

Check out the last post here:  [https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

It worked for me!  But I still have to have the usb device on a powered hub (as well in windows).

---

### Post by MaindotC on 2008-10-15
I meant which powered hub did you buy :-p

---

### Post by Chiatroll on 2009-01-31
Hi, I'm pretty need to linux but I made my new PC dual boot with it. I'm pretty happy with the linux side and learning a lot about it but, I just bought this exact wireless adapter and I can't seem to get it to run. 

So I got the drivers mentioned and... embarrassingly I don't know how to put them in. Trying to find out. I've been doing searches for it but I can't seem to pick the right words and end up at other ubuntu driver related answers.

How would I tell ubuntu that these files are the drivers it will use to run the adapter?

Nevermind I found [http://ubuntuforums.org/showthread.php?t=972060&highlight=wusb600n](http://ubuntuforums.org/showthread.php?t=972060&highlight=wusb600n)

---

