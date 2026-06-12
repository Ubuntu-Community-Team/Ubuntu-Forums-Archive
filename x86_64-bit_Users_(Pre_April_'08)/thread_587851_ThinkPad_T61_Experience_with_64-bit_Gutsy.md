---
title: "ThinkPad T61 Experience with 64-bit Gutsy"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tim T on 2007-10-23
I just installed Kubuntu Gutsy x64 on my brand spankin new Lenovo ThinkPad T61 15.4" notebook.  For those interested, below are the specs.

  	42V8190 	 SBB INTEL CORE 2 DUO T7300   	  	  	 
  	42V8287 	 SBB 15.4 WSXGA+ TFT  	  	  	 
  	42X0817 	 SBB INT GMAX3100 GM965W  	  	  	 
  	41W2060 	 VBB 1GB PC2-5300 667MHZ 1DIMM  	  	  	 
  	42V8195 	 SBB KEYBOARD US ENGLISH  	  	  	 
  	42V8295 	 SBB UN(TRACKPOINT TOUCHPAD)  	  	  	 
  	42V8169 	 SBB 100GB HDD,7200RPM  	  	  	 
  	42V8171 	 SBB CD-RW/DVD-R24X24X24X8XUB-S  	  	  	 
  	42X0805 	 VBB PC CARDSLOT EX CARDSLOT  	  	  	 
  	41W1501 	 SBB INTELPRO/WL3945ABGUSCNLAAP  	  	  	 
  	62P6054 	 VBB INTEGR.BLUETOOTH PAN  	  	  	 
  	39T6651 	 SBB 9 CELL LI-ION BATTERY  	  	  	 
  	41W1787 	 SBB CPK NORTH AMERICA  	  	  	 
  	42V8339 	 SBB LPACK US ENGLISH  	  	  	 
  	42V8063 	 SBB MS WAU ENGLISH NA-U MODELS  	  	  	 
  	42X1482 	 SBB BLUETOOTH W/ ANTENNA  	  	  	 
  	42X1483 	 SBB BLUETOOTH SCREW  	  	  	 
  	42V8631 	 SBB 15WSXGAW/BTW/OWWANW/OUWB  	  	  	 
  	39T6440 	 SBB 56K V.92 DESIGNED MODEM  	  	  	 
  	42V8654 	 SBB CL.PLATE T61WLAN BLTOOTH  	  	  	 
  	42V8607 	 SBB INT.WLAN ANTENNA 15.4"  	  	  	   	  	 
  	42V8601 	 SBB NO UWB ANTENNA  	  	  	 
  	42X0995 	 SBB PC CARD SLOT EXP.CARD SLOT  	  	  	 
  	42V8612 	 SBB ST LCD COVER/BEZEL 15.4"  	  	  	 
 1  	 40Y8725   	 THINKPAD SERIAL ATA HARD DRIVE BAY ADAPTER  
 1  	 41N3013   	 THINKPAD 100GB 7200 RPM SERIAL ATA HARD DRIVE 

So that should get any questions about hardware out of the way.
I installed XP Pro on one hard disk, and kubuntu 7.10 x64 on the other. To do it though, I had to use the net installer I found from here: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora) .

Install
The install took 2 days because I couldn't get the files downloaded without them corrupting.  I eventually had to get the files from archives.ubuntu.com in the UK. When I finally got them, the whole process went smoothly. I was worried about partitioning errors, but it detected both drives instantly, and formatted my second drive perfectly. The bootloader didn't corrupt my windows os like it did when I installed 7.04 before. I am able to dual boot with ease! 

Video
Works like a charm out of the box. No problems running default resolution of 1680 x 1050.

Audio
It works ok, but the hardware buttons don't work properly. The mute button works, and the volume up button will take you out of mute, but you cannot raise or lower the volume with the buttons.

Networking
Ethernet works like a charm, as does wireless. No problems connecting to a wpa2 encrypted network (FINALLY!!!). I haven't tested bluetooth yet, but plan on it in the future. I haven't tested the modem either (anyone still use dialup?)

Keyboard
the lock button doesn't work, the battery button shows you your current charge status. sleep and radio both work, brightness doesn't work at all. I'll get to that later. The LED light button works. The page back and forward buttons located on either side of the up arrow don't work. The thinkvantage button isn't assigned to anything. The play, pause, next and back buttons work.

Mouse
I disabled the touch pad, so I can't speak about it, however the touchpoint works ok. My big issue is that the middle button doesn't work properly. I'm not sure what it does, but it messes things up every time it's pushed. It REALLY needs fixing.

Battery
I have the 9 cell battery, and it was money well spent. In xp, I can get over 6 hours of video play with the wireless off. Kubuntu lets me select what power mode I want, and can adjust automatically between power plans between ac and battery. And something i really like is that kubuntu shows you your current processor speed (2001 mhz x2 in performance mode, and 800 mhz x2 in power save mode ). One thing to note, I had to tell the laptop to go into suspend mode when i close the lid from the power options list.



OS reactions
I don't notice much of a visual difference between 7.10 and 7.04 . That's good. What I did notice was that the 64-bit platform is finally on par with the 32 bit platform. Nearly everything works out of the box. My only problems circle around the brightness, the sound buttons, and the middle button. For this to be my primary OS, I need my brightness to be adjustable, which from everything I have read says it should be. Adjusting it via the battery program or hardware does nothing. The brightness always stays at 100%. The sound button issue needs to be sorted out. I hear it's a known issue and is being worked on, and besides, the sound can be manually adjusted inside the volume settings. I think the trackpoint issue is the easiest thing to sort out, but I'm still pretty new to linux (just now hitting the 1 year mark) and am not sure how to go about fixing this. Any ideas?

---

### Post by John Jason Jordan on 2007-10-23
> **Tim T said:**
> I just installed Kubuntu Gutsy x64 on my brand spankin new Lenovo ThinkPad T61 15.4" notebook. 
Video
Works like a charm out of the box. No problems running default resolution of 1680 x 1050.
Audio
It works ok, but the hardware buttons don't work properly. The mute button works, and the volume up button will take you out of mute, but you cannot raise or lower the volume with the buttons.
Networking
Ethernet works like a charm, as does wireless. No problems connecting to a wpa2 encrypted network (FINALLY!!!). I haven't tested bluetooth yet, but plan on it in the future. I haven't tested the modem either (anyone still use dialup?)
Keyboard
the lock button doesn't work, the battery button shows you your current charge status. sleep and radio both work, brightness doesn't work at all. I'll get to that later. The LED light button works. The page back and forward buttons located on either side of the up arrow don't work. The thinkvantage button isn't assigned to anything. The play, pause, next and back buttons work.
Mouse
I disabled the touch pad, so I can't speak about it, however the touchpoint works ok. My big issue is that the middle button doesn't work properly. I'm not sure what it does, but it messes things up every time it's pushed. It REALLY needs fixing.
Battery
I have the 9 cell battery, and it was money well spent. In xp, I can get over 6 hours of video play with the wireless off. Kubuntu lets me select what power mode I want, and can adjust automatically between power plans between ac and battery. And something i really like is that kubuntu shows you your current processor speed (2001 mhz x2 in performance mode, and 800 mhz x2 in power save mode ). One thing to note, I had to tell the laptop to go into suspend mode when i close the lid from the power options list.
OS reactions
I don't notice much of a visual difference between 7.10 and 7.04 . That's good. What I did notice was that the 64-bit platform is finally on par with the 32 bit platform. Nearly everything works out of the box. My only problems circle around the brightness, the sound buttons, and the middle button. For this to be my primary OS, I need my brightness to be adjustable, which from everything I have read says it should be. Adjusting it via the battery program or hardware does nothing. The brightness always stays at 100%. The sound button issue needs to be sorted out. I hear it's a known issue and is being worked on, and besides, the sound can be manually adjusted inside the volume settings. I think the trackpoint issue is the easiest thing to sort out, but I'm still pretty new to linux (just now hitting the 1 year mark) and am not sure how to go about fixing this. Any ideas?
I just bought a T61 similar to yours and installed Gutsy amd64 as the only OS yesterday. Mine has the 160 GB 5400 rpm SATA drive (can't find out from anyone if it is SATA I or SATA II). However, I do not have the drive bay adapter, as the 160 GB should hold me a very long time. I also added 1 GB RAM. 

I disabled the touchpad in the BIOS because they drive me nuts. I use an external USB wireless optical mouse instead, although I did leave the trackpoint enabled. I just tried it and it appears to work fine. I move it around and when I want to click on something I use the buttons on the touchpad, which still work. 

I also have the nVidia video and I had a lot of trouble with it. I think I finally have it working, but it was not autodetected by Ubuntu. And there is no boot splash screen. 

I have the 6-cell battery, and I'm going to test it at the university tomorrow. According to the specs I'm supposed to be able to get 3.8 hours out of it. We'll see. Lenovo is in China, so I bet they stated the time in Celsius hours. Each of those is worth only ten minutes English, so the battery probably lasts 38 minutes. :)

I've been having problems with Nautilus too. Every once in a while I'll notice the CPU meter (which works on only one CPU at a time) goes to 2000 and sticks there. Then I go into System Monitor and notice several copies of Nautilus running, all sleeping except one that is pegged at 49-50%. I kill them all and relaunch Nautilus and things go back to normal. Still, it sounds like there's a bug somewhere.

I haven't tested the bluetooth yet, but I plan to soon.

I hadn't tried the volume buttons, but after reading your experience I just did. The mute button works, but the volume up and down do not. 

I also just tried the brightness buttons and you're right. A little window pops up and it looks like it is going up and down, but the brightness does not change. However, the camera comes on and off as it should.

I don't know what the other buttons do. Also, I'm especially curious about the light with the lightning bolt in it, between the battery and the hard disk light.

So far I really love this computer. Feels solid, like good quality workmanship.

---

### Post by John Jason Jordan on 2007-10-27
I have been using my T61 for over a week now and I have pretty much everything working except wireless. I have done a lot of poking around and have come to the conclusion that there is a bug in the Network GUI in Gutsy.

From a command line "iwlist wlan0 scan" lists all the available networks. At the same time if I open System > Administration > Network it sees no wireless networks. It does see the wireless card, and I can uncheck the Roaming box. But when I do the drop-down should list all available wireless networks; however, it displays nothing and won't even drop down. Note that "iwlist wlan0 scan" displays available networks, but the GUI does not.

The wireless on this computer is the Intel 4965. 

I am wondering if any other users if 64-bit Gutsy have wireless working on this wireless chip. And also, does anyone have any other ideas for me to try?

---

### Post by Tim T on 2007-10-28
> **John Jason Jordan said:**
> I have been using my T61 for over a week now and I have pretty much everything working except wireless. I have done a lot of poking around and have come to the conclusion that there is a bug in the Network GUI in Gutsy.

From a command line "iwlist wlan0 scan" lists all the available networks. At the same time if I open System > Administration > Network it sees no wireless networks. It does see the wireless card, and I can uncheck the Roaming box. But when I do the drop-down should list all available wireless networks; however, it displays nothing and won't even drop down. Note that "iwlist wlan0 scan" displays available networks, but the GUI does not.

The wireless on this computer is the Intel 4965. 

I am wondering if any other users if 64-bit Gutsy have wireless working on this wireless chip. And also, does anyone have any other ideas for me to try?

I'm not of much use here, but I have an idea that might point you in the right direction. Since the command line will let you see all the available networks, why not try connecting to a network using the command line. I don't know which commands to tell you, but I am positive someone here must.

---

### Post by John Jason Jordan on 2007-10-28
> **Tim T said:**
> I'm not of much use here, but I have an idea that might point you in the right direction. Since the command line will let you see all the available networks, why not try connecting to a network using the command line. I don't know which commands to tell you, but I am positive someone here must.
I could see the networks from the command line, but could not get a DHCP address for any of them. However, this morning I installed wifi-radar and afterward I was able to connect. Unfortunately, I did not have an opportunity to try it at more than one location (a coffee shop), so it may not be completely fixed. The specific issue of wireless on a Thinkpad T61 is being discussed in another thread in the networking forum here:

[http://ubuntuforums.org/showthread.php?t=587922&highlight=Thinkpad+T61](http://ubuntuforums.org/showthread.php?t=587922&highlight=Thinkpad+T61)

---

### Post by Buzzdee on 2007-10-28
How to *properly* install Gutsy on your (and my, btw) laptop: 
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p")
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61)
I got my 3d-acceleration, sound control buttons and even the fingerprint scanner (!) working. Hibernate works fine as well. I hope this works for you, too.

---

### Post by syxbit on 2007-10-28
is there a solution to no usplash?
i'd like it :)
i remember 2 days ago the stupif FSCK came on, and my comp was stuck with a blank screen before bootup for 20 mins (i guessed it was FSCK and left it)

---

### Post by John Jason Jordan on 2007-10-29
> **syxbit said:**
> is there a solution to no usplash?
i'd like it :)
i remember 2 days ago the stupif FSCK came on, and my comp was stuck with a blank screen before bootup for 20 mins (i guessed it was FSCK and left it)
Some people have managed to get the usplash working, but the fixes for some don't work for others. Search the forums for "thinkpad" and "t61" and you should find the threads. 

I tried all the fixes except that last one by orange2, and none of them got my usplash working. However, I also have unstable video in general. For the past week, through about a dozen restarts, I have had 1680 x 1050. Today I came back from the airport, booted up the computer, and was stuck at 1440 x 800. The resolution settings still said 1680 x 1050. I am using the nVidia glx-new driver that the Restricted Drivers Manager installed. Today I didn't touch a thing when I was at the airport, but it still came up wrong, and this is not the first time that it has suddenly decided to boot at a 1440 x 800 (with part of the screen off the sides). 

I tried everything to get it back from the GUI, but eventually decided it was so screwed up that I might as well do dpkg-reconfigure xserver-xorg. I made a copy of xorg.conf first, though. If anyone else has problems with the nVidia Quadro NVS 140M, I'd appreciate hearing of them. 

There are others who have had problems with the Intel 4965 AGN wireless, although I sort of have that part working. There is another thread where that has been discussed.

---

### Post by syxbit on 2007-10-29
but usplash always worked with x86, just not x64

---

### Post by Tim T on 2007-11-03
> **Buzzdee said:**
> How to *properly* install Gutsy on your (and my, btw) laptop: 
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p")
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61)
I got my 3d-acceleration, sound control buttons and even the fingerprint scanner (!) working. Hibernate works fine as well. I hope this works for you, too.

I followed thinkwiki for the install. I could not get the sound working with the hardware buttons on kubuntu. The brightness is supposed to be adjustable out of the box for my chipset, but it is not. It stays at 100% all the time.

---

### Post by Tim T on 2007-11-06
So I reinstalled linux. This time the brightness works. The sound doesn't, nor does the 3945 abg wifi. It shows me the available networks, and even detects the correct type of encryption, but won't accept the wifi key... whether it be wep pass phrase, wep hex, wpa tkip, or wpa2 aes. I'm able to connect fine on my windows boxes with all of the above settings, and i was able to connect fine the last time i installed x64 7.10, so I am wondering what's changed... For the record, I also tried connecting with wpa on our work wifi without any success. It worked fine in vista. The volume and mute keys work, although they change the mic volume instead of the master volume. It seems like a different bag of problems with each install. I remember seeing a fix or something atleast acknowledging the issue somewhere (thinkwiki i think). A BIOS update from Lenovo was supposed to fix the hardware sound key issue, and it was released recently. I haven't been able to get the BIOS updated, so it's still running the 1.22 version. This means that there must have been a patch released to fix the issue.

---

### Post by John Jason Jordan on 2007-11-07
> **Tim T said:**
> So I reinstalled linux. This time the brightness works. The sound doesn't, nor does the 3945 abg wifi. It shows me the available networks, and even detects the correct type of encryption, but won't accept the wifi key... whether it be wep pass phrase, wep hex, wpa tkip, or wpa2 aes. I'm able to connect fine on my windows boxes with all of the above settings, and i was able to connect fine the last time i installed x64 7.10, so I am wondering what's changed... For the record, I also tried connecting with wpa on our work wifi without any success. It worked fine in vista. The volume and mute keys work, although they change the mic volume instead of the master volume. It seems like a different bag of problems with each install. I remember seeing a fix or something atleast acknowledging the issue somewhere (thinkwiki i think). A BIOS update from Lenovo was supposed to fix the hardware sound key issue, and it was released recently. I haven't been able to get the BIOS updated, so it's still running the 1.22 version. This means that there must have been a patch released to fix the issue.
First, I flashed the BIOS to the latest and it fixed the sound buttons. Warning: The sound buttons may appear not to work but that may be because (like me) you misunderstand how they are supposed to work. The mute button is not a toggle. If the sound is muted, pressing the mute button will do nothing. All the mute button will do is mute the sound if it is not already muted. To enable sound when the sound is muted you use the up button. 
Regarding the BIOS update, burn it to a bootable CD with K3b or Gnomebaker or something, then boot to the CD. Follow the online instructions. I held my breath, but it worked.
Regarding the wireless, I installed WifiRadar (from Synaptic) and ever since have had no problem connecting. But the Ubuntu network manager GUI is broken. You can select the wireless, click on properties, turn off Roaming Mode, and it won't drop down a list of available networks. At the same time WifiRadar shows the available networks. I'd rather use WifiRadar anyway - it's faster and simpler and you can set it up not to require root to run.

---

### Post by Tim T on 2007-11-07
> **John Jason Jordan said:**
> First, I flashed the BIOS to the latest and it fixed the sound buttons. Warning: The sound buttons may appear not to work but that may be because (like me) you misunderstand how they are supposed to work. The mute button is not a toggle. If the sound is muted, pressing the mute button will do nothing. All the mute button will do is mute the sound if it is not already muted. To enable sound when the sound is muted you use the up button. 
Regarding the BIOS update, burn it to a bootable CD with K3b or Gnomebaker or something, then boot to the CD. Follow the online instructions. I held my breath, but it worked.
Regarding the wireless, I installed WifiRadar (from Synaptic) and ever since have had no problem connecting. But the Ubuntu network manager GUI is broken. You can select the wireless, click on properties, turn off Roaming Mode, and it won't drop down a list of available networks. At the same time WifiRadar shows the available networks. I'd rather use WifiRadar anyway - it's faster and simpler and you can set it up not to require root to run.

I got the sound to work by folowing thinkwiki's sound article: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61#Enabling_Audio_controls](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61#Enabling_Audio_controls)

I still haven't gotten the BIOS to update, I have burned 2 cd's so far, with different things happening both times. First time, the disc was corrupted. Second time, the disc showed me a blinking cursor (corrupted again I think), and sat there for 40 or so minutes before i gave up. I'll try again later. I wish Lenovo would have posted md3 numbers for their files... . And thanks for the WifiRadar tip! I have heard of that before, but haven't tried it. I'll give it a try now

EDIT: I can't burn cd's in Linux because I installed it to my second HD (ultra bay slot). If I can fix all the bugs (wifi and the middle button for the trackpoint) I will switch to Linux fulltime. I am also mildly concerned with battery life in linux vs vista with battery stretch...

---

### Post by syxbit on 2007-11-17
i just did the bios update, but sound buttons still don't work
i did, however compil alsa 1.15 myself though, so maybe that's why

---

### Post by John Jason Jordan on 2007-11-17
> **John Jason Jordan said:**
> Regarding the wireless, I installed WifiRadar (from Synaptic) and ever since have had no problem connecting. But the Ubuntu network manager GUI is broken. You can select the wireless, click on properties, turn off Roaming Mode, and it won't drop down a list of available networks. At the same time WifiRadar shows the available networks. I'd rather use WifiRadar anyway - it's faster and simpler and you can set it up not to require root to run.
Just an update on the wireless. I have had continuing problems with it. It is being discussed in the general networking forum - here is the thread:

[http://ubuntuforums.org/showthread.php?t=587922&highlight=Thinkpad+T61](http://ubuntuforums.org/showthread.php?t=587922&highlight=Thinkpad+T61)

Like Nigel in the above thread, it works most of the time, but I cannot stay connected. It may be five or ten minutes or it might be an hour or more, but eventually I will get disconnected. After being disconnected the device is still there, appears to be still working, but I can't get a DHCP address. Rebooting sometimes helps, sometimes not. According to Nigel Lenovo is making new drivers constantly, so evidently it is a bug in the iwl4965 module.

---

### Post by syxbit on 2007-11-17
lenovo has nothing to do with those drivers.
it's intel

---

### Post by dknig1b on 2008-02-08
I just installed ubuntu x64 (gutsy) on a T61 with the nvidia option.  It is now Feb 7, some time after the first in this post, and everything went smoothly (including the nvs140 and the wireless)

I had to fiddle a little to get the t61 sound buttons to actually drive the sound using the thinkwiki ubuntu help.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

this  also discusses the fact that the screen brightness buttons don't work (you see the brightness bar on the screen and can move it, but it doesn't really affect the brightness).

Best luck to others who try.  I think things are relatively smooth by now.

---

### Post by John Jason Jordan on 2008-02-08
> **dknig1b said:**
> I just installed ubuntu x64 (gutsy) on a T61 with the nvidia option.  It is now Feb 7, some time after the first in this post, and everything went smoothly (including the nvs140 and the wireless)
I had to fiddle a little to get the t61 sound buttons to actually drive the sound using the thinkwiki ubuntu help.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)
this  also discusses the fact that the screen brightness buttons don't work (you see the brightness bar on the screen and can move it, but it doesn't really affect the brightness).
Best luck to others who try.  I think things are relatively smooth by now.
Mine is working fine too, except for the wireless. From reading here and elsewhere I determined that the sudden hangup problems of the wireless are not going to be fixed until there is a later kernel. There are people who claim to have fixed it by upgrading their kernel, but I am not going to do that. Everything but the wireless works fine and I need this computer for school. So I borrowed a Netgear WG511T from a friend and disabled the 4965AGN in the Thinkpad BIOS. I think Hardy Heron will come with a new kernel that will fix the wireless. Until them I'll just use the borrowed Netgear card.

---

### Post by lamborghiniwang on 2008-02-25
I am having a T61p with Nvidia 570M video card running Gutsy 64-bit. Everything works fine except the video out. I can not get video out work unless I restart the X, it is very annoying when you are in a meeting, which gives you only 20 minutes for the talk, and you have to spend 2-3 minutes just to get a signal for the projector. 
  Has anyone figured out a way for this? The video-out is pretty much the only reason that I am still keeping the Windows partition.
PS: I am running the restricted Nvidia driver

---

