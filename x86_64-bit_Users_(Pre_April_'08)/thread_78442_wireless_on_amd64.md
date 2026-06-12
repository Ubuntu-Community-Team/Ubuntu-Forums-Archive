---
title: "wireless on amd64"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by vehyla on 2005-10-18
Has anyone gotten wireless to work in 64 bit mode?  I have a:

0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I can not get it to work.  I tried to manually compile ndiswrappers but it fails saying it can not compile 32 bit app for 64 bit system.  I have asked uncle google repeatedly but have gotten no response.  If you have any hints or ideas please let me know.  If you don't know how you got it to work but it DOES work also let me know so I will know it at least CAN be done.  Thanks.

Here is my current ndiswrapper (isntalled through apt-get) read out.
babylon:~ $ ndiswrapper -l                                        [5:02]
Installed ndis drivers:
bcmwl5  driver present, hardware present

---

### Post by vehyla on 2005-10-18
Okay so 14 minutes after posting this a co-worker showed me a sight he found which linked back to here.   I downloaded my drivers from there and it still didn't work.  So I reinstalled ndiswrapper through apt-get and it worked.  So for anyone else having this problem get your drivers from here:

[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

---

### Post by cadash on 2005-10-18
i have a compaq presario v2000z don't remember right now the broadcomm version it has, I dunno if i was doing sth wrong of anything but well been trying different things and after a while i got thins working as they were supposed to, i am also using ndiswrapper and well one thing taht calls my attention is that while windows shows different signal levels  inside the apartment, sometimes incredibly low ones, in Ubuntu the bar is always showing the signal strentgh at 100%, i really hope it is linux :) but that sounds just too good, myabe the strength bar is not working correctly

---

### Post by Shaun32 on 2005-10-18
I think I know the thread you are talking about from early 2005.  I followed the instructions on that too and was unsuccessful but I was going off of a how-to for the previous version 5.04 so I think maybe that was why I'm having problems?  The thing is when I do lspci and everything my comp knows what my broadcom wireless card is and it even lists the correct name with 34xx whatever.  However, when I go to System -> Administration -> Networking, wlan0 is not there AND I don't have any Add button as the help file says there is.!?  I'm kinda confused and wondering if it was a bad idea in the first place to look at the how-to I looked at.  

This was the thread: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

Could someone point me to a different how-to or something?  I know this can work and I feel I am close now but I'm getting a bit frustrated with the time it's taking to do it.

Thnx,

Shaun

---

### Post by vehyla on 2005-10-19
I followed the steps in that forum you were refering to however I used the file in the forum link I posted and it worked.  A very important thing which messed me up was after you get niswrappers to say "driver found,. hardware found" you have to rmmod  the ndiswrapper then modprobe the ndiswrapper to have it reload with the drivers.  Otherwise it will keep the old information.  
I was using a comap presario R4000

---

### Post by Shaun32 on 2005-10-19
Ok, thanks, that's great news b/c I am using an r4000 too!  Just one thing I need to confirm.  You are running ubuntu 5.10 right?

I will clean my current ndiswrapper driver out and try to do the process again with "your" file then.  Another question though: Will wlan0 show up in the "Network" window in GNOME when it is working?  Mine isn't showing up and I can't find a place to add it.  I just have eth0 and that's it, but I know wlan0 is recognized, it's just not starting properly.  Also, were you saying that you need to modprobe the ndiswrapper before you reboot (although the thread says to do it after)?

One more thing...does your wireless light light up on your r4000 laptop when your card is working?

Thanks in advance,

Shaun

---

### Post by Shaun32 on 2005-10-19
Ok thanks a million on your advice, I finally just got it working!!!!!!!!!!!!  I did it with your files like you said and yes, wlan0 did pop up in the menu.  Finally hours of work (probably shouldn't have been hours but yeah, I'm still a noob despite years of playing around lol) have paid off.

Now the next thing is my graphics card...does your r4000 have a ATI Radeon Xpress 200M in it too and have you gotten it to work?

Thanks again,

Shaun

---

### Post by HankB on 2005-10-19
I've got the same wireless card (built into an HP special edition L2000) and nearly had it working. On the train to work, I installed the drivers downloaded from the ACER site along with ndiswrapper and when I did an "iwlist wlan0 scan" I could see access points that were within range. At that point, all I had to do was set up the SSID and WEP key and I figured I'd be in business.

Or so I thought. When I got home and tried to bring up the interface, I could no longer scan access points. (I should see three at home, mine and two neighbors.) I've studied logs, iwconfig output and removed and reinstalled the drivers several times without further success. I also tried the drivers listed earlier in this thread and they did not work. (ndiswrapper -l listed driver but no hardware.)

So, I'm at a loss to know what's wrong. The WiFi interface on this laptop has a on/off button and I wonder if the problem has something to do with that.

Suggestions for help would be appreciated.

thanks,
hank

---

### Post by HankB on 2005-12-11
I finally got this working. I uninstalled the ndiswrapper-tools package, renamed the ndiswrapper kernel module (to avoid confusion) and installed v1.5 of the ndiswrapper tools from Sourceforge. The newer version of the module and tools seem to handle my laptop without difficulty. (I do manually stop the interface and rmmod the ndiswrapper module before suspending.)

thanks,
hank

---

