---
title: "Need help finding 64-bit Windows drivers for MSI PC60G wireless card (RT61)"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by UnrealMiniMe on 2007-11-18
Hiya everyone...

**Here's the overview of my problem:**
I've been enjoying Feisty for some time now on another computer, but I had way too many issues installing it on my new computer, so I held off for Gutsy.  Now that Gutsy is out, I've been able to get past all of my major issues except one:  Wireless support in a 64-bit environment.

I have an MSI PC60G PCI card, and I believe it uses an RT2561 chipset.  The default Ubuntu driver for my card is rt61pci, and while it gives me a fast connection on boot, it quickly cuts out and leaves me without an Internet connection at all until I reboot again (since wireless is the only connection I have).  My connection can drop out at anytime, but it usually seems to happen if I "overload the driver" by loading too many webpages in quick succession (such as when restoring 5 or more firefox tabs from my last session).

**Here are my goals and what I've tried so far to figure out what's going on:**
I've done a lot of research on these forums, and it seems that the stock driver just doesn't really cut it.  Since I'm a relative Ubuntu noob and networking has never been my forte, I definitely don't want to set up my connection manually with console commands, etc; in other words, I want to be able to use Network Manager to connect to access points, roam, etc.  Because of that, the most valuable FAQ here so far has been [http://ubuntuforums.org/showthread.php?t=563547]("http://ubuntuforums.org/showthread.php?t=563547"), the conversation thread surrounding a sticky in the Networking & Wireless forum.  It seems that, since the drivers included in Gutsy and the serialmonkey RT2x00 drivers (which I've compiled and installed, though I'm not quite sure if I ever actually loaded them correctly) cause frequent dropped connections, I have to go the ndiswrapper route for a stable connection that's compatible with Network Manager, WICD, etc.  After attempting the steps in the thread I linked to, my symptoms are exactly the same as dingansich's (another poster in the thread) in his posts on pages 10 through 12, and my console command outputs are almost exactly the same as well (the only differences are due to the fact that my actual wireless card is different from his...i.e. different id's, slightly different driver names, etc.).  For instance, his post here describes my situation exactly:  [http://ubuntuforums.org/showpost.php?p=3591109&postcount=102]("http://ubuntuforums.org/showpost.php?p=3591109&postcount=102")

Now, anyway, my actual problem is the same as his:  If I use a 32-bit driver, "cat /var/log/dmesg | grep ndis" outputs just about the same thing for me as it did for him in his post here: [http://ubuntuforums.org/showpost.php?p=3597319&postcount=112]("http://ubuntuforums.org/showpost.php?p=3597319&postcount=112").  However, I DID find a 64-bit Vista driver (MSI graciously makes the Vista drivers available in a .zip file on their site, but the XP drivers are only available in an un-extractable .exe file, as mentioned in the next section), and I got some unknown symbol errors instead...after compiling my own ndiswrapper from source to see if I could get around this, I found out on the ndiswrapper website that "Windows Vista drivers are not supported (yet) - using Windows Vista driver will result in many &#8216;unknown symbol&#8217; error messages when loading ndiswrapper."

**What I apparently need and why it's so hard to get:**
In order to get my wireless card working with Network Manager (without losing my connection constantly and needing to do a full reboot - yes, /etc/init.d/networking restart doesn't help), it seems like I'm pretty much going to have to use ndiswrapper and 64-bit Windows XP drivers.  There are three places I know of where I can get the 32-bit and 64-bit drivers:
[LIST]
[*][http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=131&prod_no=1063](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=131&prod_no=1063) 
[*][http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
[*]The installation CD for my wireless card
[/LIST]
Unfortunately, all three of these sources encapsulate the 32-bit and 64-bit Windows XP drivers in an .exe file that I can't unzip or open with any archive manager I've tried...since they each include wireless connection management software for Windows, I guess they're just plain-old .exe files.  I've also tried installing each of these on my Windows XP partition (I'm dual-booting), but they automatically extract only the 32-bit drivers, so I can't get my hands on the 64-bit versions (despite the fact that the MSI site supposedly has different links for the 32-bit and 64-bit versions).

In the thread at [http://ubuntuforums.org/showthread.php?t=589119&highlight=pc60g]("http://ubuntuforums.org/showthread.php?t=589119&highlight=pc60g"), wieman01 directed another poster to driverstock.com, but unfortunately, they don't seem to actually have links to any real drivers...the only real download they seem to offer on their site is for their Windows DriverDetective software (just try clicking the supposed link to the drivers I need at [http://www.driverstock.com/MSI-PC60G-driver-download/14-28-12540/index.html]("http://www.driverstock.com/MSI-PC60G-driver-download/14-28-12540/index.html") ;)).

**Bottom line:**
I'm really strapped for 64-bit Windows XP drivers for either of the following:
[LIST]
[*]My specific card, the MSI PC60G
[*]The Ralink rt61, rt2561, or even general rt2x00 (if that's compatible...) chipsets.
[/LIST]

So. um...can anyone help me out?  Does anyone know where I can find the 64-bit Windows drivers ndiswrapper requires?

Thanks!!!

---

### Post by wieman01 on 2007-11-19
There aren't any 64-bit drivers on the CD that came with your card?

---

### Post by UnrealMiniMe on 2007-11-19
There are, but just like the drivers on the MSI and Ralink sites, they are encapsulated in a .exe file that is more than just a file archive...that is, I've been unable to unzip it or otherwise extract its contents with archive manager programs (which makes sense...it's a big, bloated install program that also forces you to install wireless connection management software for Windows when you run it).  I've tried getting the files by running the .exe on my Windows partition, but it always installs only the 32-bit versions (since I'm running 32-bit XP).  This same situation goes for the drivers stored at [http://www.ralinktech.com/ralink/Hom...t/Windows.html]("http://www.ralinktech.com/ralink/Hom...t/Windows.html") and [http://global.msi.com.tw/index.php?f...1&prod_no=1063]("http://global.msi.com.tw/index.php?f...1&prod_no=1063"), too (despite the fact that the MSI site *appears* to offer separate download links for the 32-bit and 64-bit versions).  I noticed that in the thread at [http://ubuntuforums.org/showthread.php?t=589119&highlight=pc60g]("http://ubuntuforums.org/showthread.php?t=589119&highlight=pc60g"), you linked to a page on driverstock.com, but from what I can tell, the only *real* download they offer on their site is for their Windows DriverDetective software.

By the way, thanks for creating your guide in the first place, Wieman...I definitely share your preference for Network Manager over manually setting up a wireless connection via console.  I don't know why I'm so confident, but I feel certain that your guide will work for me if only I can find usable drivers.

---

### Post by wieman01 on 2007-11-19
Yes, I am confident as well, otherwise I would not post here. :-)

Seriously, could you not contact their customer service and ask for the files? I am sure they would help you. Perhaps this is too obvious a solution, but why not give it a go?

---

### Post by UnrealMiniMe on 2007-11-19
Hehe...actually, I tried to call them up earlier tonight, but it was past their office hours.  I'll be trying again tomorrow, and I might try their online support as well.  Hopefully they will be receptive to this kind of request...

---

### Post by wieman01 on 2007-11-19
> **UnrealMiniMe said:**
> Hehe...actually, I tried to call them up earlier tonight, but it was past their office hours.  I'll be trying again tomorrow, and I might try their online support as well.  Hopefully they will be receptive to this kind of request...
The only other solution I could think of at the moment is installing your card on a 64-bit Windows system. But of course a 64-bit system will be tough to find.

---

### Post by UnrealMiniMe on 2007-11-19
Yeah, and it would really be more worthwhile to get another card than set up Win XP-64 myself...speaking of which, if I can't get the drivers from MSI, is there any widely accepted "best, most compatible wireless adapter" for Ubuntu?
The format of the Ubuntu wiki page here ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")) isn't really the best...it seems to be more geared towards finding out how compatible a specific card is than it is towards people looking for a good recommendation.  I actually bought this card because I mistook it for another MSI card that was reported to work out of the box (not sure if it was my reading ability or Newegg's writing ability that did me in, but no matter ;)).

BTW, if I am able to get the drivers from MSI (or if not them, Ralink), is there any widely-known community resource that I could submit them to for hosting?  I don't actually have my own site or anything, but it seems like 64-bit rt61 drivers may be helpful to a lot of people.  (Also, the .exe programs from MSI and Ralink are **exceedingly** similar, so I really doubt MSI made any significant changes to their drivers that would render them unusable for other rt61-based cards.)  I just noticed this entry on the Ubuntu Wiki site, and it seems to indicate that if there's no community driver repository yet, there may be soon:  [https://wiki.ubuntu.com/EasyWirelessDrivers?highlight=%28wireless%29]("https://wiki.ubuntu.com/EasyWirelessDrivers?highlight=%28wireless%29")

---

### Post by wieman01 on 2007-11-19
Apparently the **Netgear WG311T** is a good choice. See this thread for reference:

[http://ubuntuforums.org/showthread.php?t=363633&page=3]("http://ubuntuforums.org/showthread.php?t=363633&page=3")

---

### Post by jhopkins81 on 2007-12-14
I have the same problem.  I need to keep the MSI card, because I have a dual boot system, and the MSI card works for XP-64.  Did you ever figure out a solution to this problem?

---

### Post by UnrealMiniMe on 2007-12-14
Hi jhopkins,
Well, it depends...I think you may actually have my solution on your hard drive!  Have you tried ferrying your XP-64 drivers over to your Linux partition and using them with ndiswrapper?  That's what I was wanting to try, but I **still** haven't gotten my hands on the 64-bit Windows XP drivers...I called MSI's tech support and asked them to email me the drivers several times, but they never did. :-/

I'd suggest trying ndiswrapper with the XP-64 drivers, for starters...have you checked out Wieman's guide at [http://ubuntuforums.org/showthread.php?t=563547]("http://ubuntuforums.org/showthread.php?t=563547")?  Since you actually have the XP-64 drivers, I have a feeling it should work.

**As a request, do you think you could email me a copy of the XP-64 drivers?  They should be in your "C:\Program Files\MSI\MSI Wireless LAN Card\Installer\WINXP" directory, if your Windows setup is anything like mine.  The important files are the ones starting with "rt61..."**

I'd like to try Wieman's method myself, but I've been stuck at the "getting my hands on the 64-bit drivers" part, since I can't get them from my installation CD.  I dual-boot with XP-32, and the installation CD automatically installs only the 32-bit drivers...
Anyway, I'll PM you my email address in case you're willing to help out!

---

### Post by UnrealMiniMe on 2007-12-16
UPDATE:
Through a really painstaking process, I obtained the 64-bit Windows XP drivers the really, really hard way. ;)  After all of that work, I tried Wieman's guide again, and IT WORKS!  ZOMG!!!  Thank you VERY much, Wieman!!! :)

jhopkins, just for the record, I used the Windows XP x64 drivers from the installation CD for the PC60G, so Wieman's guide will work for you, too.  Just install them on your 64-bit Windows XP partition and ferry them over (via USB drive or something) to your Linux setup, then follow the guide.  (They're actually in a slightly different directory from what I mentioned in my other post...the "Program Files" part should be "Program Files x86" or something like that, and there may be a few other deviations as well.  Just try exploring around there to find the folder with rt61.inf in it.)

Getting my connection to show up in Network Manager wasn't entirely automatic though, so in case anyone else experiences similar issues, here's what I did after following Wieman's guide:
After I rebooted, I obviously had a strong connection, but it wasn't showing up in Network Manager (which had the "black computer monitor" icon).  I clicked the icon, and the only option was "Manual configuration..."  I clicked that, checked the properties of my wireless connection, unchecked roaming, manually connected to a wireless network, and clicked okay, close, or whatever button is meant to save the settings.  I forget if the connection quite worked then or not, but I wasn't satisfied with a static connection:  I wanted to be able to roam AND see my connection status.  I then turned roaming back on, and I know for sure my connection didn't work after that.  However, once I rebooted again, everything was great:  I'm now roaming, I can select my wireless network in Network Manager, and I can see my signal strength!

WHEEEEEEEEE!!!!

BTW, does anyone know of a place with free file hosting?  The raw XP-64 drivers (.inf, .cat, and .sys) for this were a real pain for me to get, and I'd like to make them more easily available to other people with the same problem.

---

### Post by martynemworks on 2008-01-01
Did you manage to make those 64 bit drivers available?

---

### Post by gnaag on 2008-01-28
Hi, after some time of searching throughout the web I have found a driver that works well for my rt61 amd64 gutsy ubuntu under ndiswrapper. So here you are

---

### Post by mwpmwjcp on 2008-03-08
Ok I had some problems with this solution to getting the pc60g to work on amd64 gutsy, but I managed to get it to work. I had to do the following.

The archive in the previous post contains 3 files 
rt61.sys
rt61.cat
wmp****.inf

I had to rename all 3 to rt61.* then follow the instructions as laid out work just fine.

Good luck,

Matthew

---

