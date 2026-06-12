---
title: "wireless problems on hp pavilion zv5000"
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by oceanside on 2006-03-06
Hey -- I just installed ubuntu because I was impressed by the live cd and so far I really like it.  However, I am having trouble getting my wireless working.  I have ndiswrapper installed from synaptic and the wireless is broadcom internal wifi.  However when I downloaded the driver from HP it came in an exe file -- no .inf or whatever to install with ndiswrapper.  I haven't seen another thread explaining what to do...I basically know what to do once I have the driver files I need but I can't extract them from an exe.  I have another machien running xandros with crossover and crossover pulled up the exe's installation GUI perfectly.  Do I need to install crossover on my ubuntu machine as well?  What is the best way to get my wireless driver working?

---

### Post by bato on 2006-03-06
Hi oceanside,
I have an hp compaq nx6125.
If you have installed windows 64 and ubuntu 64 then you can search in windows directory for bcmwlf5.inf and .sys driver files.
In my case I have windows 32 bit and ubuntu 64 so the windows drivers don't work.
I have downloaded the 64 bit driver from [http://support.acer-euro.com/drivers/notebook/ferrari4000.html](http://support.acer-euro.com/drivers/notebook/ferrari4000.html) (802.11b+g (Broadcom)) and I followed this excellent tutorial
[http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan](http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan)

Hope it helps

---

### Post by oceanside on 2006-03-06
Thanks for the advice bato...I had XP Pro running on my machine before...not sure if it was 32 or 64 bit im guessing 32 because it had sp2.  When I installed ubuntu I replaced my windows OS rather than dual booting so I'm not sure how I would be able to get the files you speak of.  And my Processor is an Athlon XP-M which I believe is 64 bit so I am posting in the right area of the board correct?  Just wanted to clear that stuff up...I will try to implement your fix tonight after work.

---

### Post by oceanside on 2006-03-06
Ok, I downloaded the driver from the web site you provided and followed the instructions in the tutorial.  Everything seemed to work fine, but upon reboot there is still no wlan0 in my network configuration.  eth0 is working and fully functional.  What do I have to do to get wlan0?

---

### Post by bato on 2006-03-07
Try with

```
sudo modprobe ndiswrapper
```

then type ifconfig and you would see wlan0. You can go in System->Administration->Network and configure your wireless connection too.

---

### Post by oceanside on 2006-03-07
```
sudo modprobe ndiswrapper
```

When I tried this last night it returned a fatal error...I think I know what I did wrong (sort of.)  I have been reading through all kinds of posts on how to fix this problem and I recall one post suggested editing one of your files replacing everywhere it said i386 with amd64 or something to that effect.  Now I'm pretty sure my processor is not 64 bit (its an 800 mhz amd athlon xp-m) so I'm going to have to go back and find that file somehow (I already configured it incorrectly.)  If you know which one it might be def let me know all I remember is it was somewhere in /etc/.  Thanks for your help!

---

### Post by bato on 2006-03-07
well,
I don't know what is that file but if your processor is 32 bit you have to download the right 32 bit driver. Have you downloaded that or 64 bit driver? Eventually try with 32 bit driver.

If I understand what file you have to edit I will write as soon as possible.

---

### Post by oceanside on 2006-03-09
sorry it took so long to get back to you, have been quite busy with school and work...
anywho I couldn't find the file so I said oh well and reinstalled ubuntu, went thru the tutorial again, this time it seemed to do better...did sudo modprobe ndiswrapper when I was finished and then ifconfig which gave me a much nicer looking outcome than the error last time;

```
geoff@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:44:BF:19
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe44:bf19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:196615 (192.0 KiB)  TX bytes:11626 (11.3 KiB)
          Interrupt:19 Base address:0x7000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:65368 (63.8 KiB)  TX bytes:65368 (63.8 KiB)


```

However, still no wlan0 in my network settings...any ideas?

---

### Post by bato on 2006-03-10
mmhmm.... 

I don't have any idea....
what is the result of

```
ndiswrapper -l
```

??

Are your drivers the correct drivers for your wirleless card?? :-k

---

### Post by javaTard on 2006-03-17
Because I was in your boat and thought it would never work, I too have a HP zv5000, but have AMD 64 ATHLON, and wifi works, sort of. I take that back it works, I just need to adjust based on where I am trying to connect at

---

### Post by ruudiculus on 2006-03-19
Hi,

Any luck with your cards yet? Do you see your wireless card listed after the command:

**iwconfig** (for wireless) or **ifconfig** (for all cards)

If so, things have gone right you could edit this file: **/etc/network/interfaces** in case you're always in the same wireless network area. If you're moving around a lot with your laptop for instance, you'll often switch wireless networks. Editing the interfaces file every time is a bit un-userfriendly. I use GTKWIFI to search wireless networks and connect to it. It works great! Its an applet, I think you can find it in the Synaptic package manager. If not, this is the link: [http://gtkwifi.sourceforge.net/]("http://gtkwifi.sourceforge.net/").

I know this was a little off-thread, but I thought it was worth mentioning that when you've got things rolling with ndiswrapper, this last step is easy.

(Anyway, I'd be happy to help getting your cards up;) )

Oh. and by the way: there's a commercial alternative to ndiswrapper that offers lot of Windows drivers for free. You can use them as well with your ndiswrapper! This is the link: [http://www.driverloader.com]("http://www.driverloader.com")

Good luck!

---

### Post by ewtesterman@cox.net on 2006-03-19
Sorry wrong place

---

