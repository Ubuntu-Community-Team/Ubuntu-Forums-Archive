---
title: "Guild Wars/ATI"
date: 2008-07-24
forum: Wine
---

### Post by Vakman on 2008-07-24
Okay I have had this problem for a while now. Nobody seems to respond. Guild Wars either will give me unrecoverable graphics error or screen will be scrambled lines or it will just not open it seems. I did a fresh install of Ubuntu since things may have been messed up with all the things I have tried. The 8.7 Catalyst drivers, Envy drivers etc. Now I just have whatever I have from System > Administration > Hardware Drivers. When I open Guild Wars normally I get an unrecoverable graphics error.
Please someone fix this. I have an ATI graphics card (ATI Radeon Xpress 1200), works on my Windows side so clearly the card will work. I use Ubuntu 8.04. I suppose there is a problem with the ATI drivers in Ubuntu 8.04. Anything helps. Please and thank you.

---

### Post by Vakman on 2008-07-25
Hello? Anyone please?

---

### Post by herteljt on 2008-07-25
I have not been able to get GW working at all on Hardy.  It seems that this is a problem shared by a lot of folks.  There is some discussion at the end of this thread.

[http://ubuntuforums.org/showthread.php?t=283122&page=88](http://ubuntuforums.org/showthread.php?t=283122&page=88)

---

### Post by herteljt on 2008-07-25
Have you looked at?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194&iTestingId=28730](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194&iTestingId=28730)

---

### Post by Logical Dream on 2008-07-26
same problem here ... the screen just get freezd or I see GW coursor and thats It ... I guess I will try 12sky till we dont get some solution for ATI

---

### Post by Vakman on 2008-07-26
I have looked at those already herteljt, thanks though. I did it with the 
```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed

```
I got a unrecoverable graphics error, I also got this a while ago as well. I wish ATI drivers worked. I don't like having to be in Windows. But there will always be Guild Wars to keep me here. I am actually getting really angry with this.

---

### Post by Vakman on 2008-07-30
I am willing to do a fresh install of Ubuntu. Just tell me what I need to do to get it to work.

---

### Post by Vakman on 2008-07-31
Someone out there must have a solution.

---

### Post by Logical Dream on 2008-08-02
hehe , IM not sure ... we need to wait for some new update of drivers . 

I have kind of a same feeling , but Im not going back to WIN

---

### Post by Vakman on 2008-08-02
> **Logical Dream said:**
> hehe , IM not sure ... we need to wait for some new update of drivers . 

I have kind of a same feeling , but Im not going back to WIN

I am dual booted with Windows Vista. I would like to have Linux only. But as it seems that is impossible as long as I play Guild Wars...

---

### Post by Logical Dream on 2008-08-02
Im on GW for 2 years , and decide to make brake , but this seams to be a long break :) 

I hope something will come out soon to solve this issue.

---

### Post by Vakman on 2008-08-02
> **Logical Dream said:**
> Im on GW for 2 years , and decide to make brake , but this seams to be a long break :) 

I hope something will come out soon to solve this issue.
I also hope something will solve this issue. I suppose we will see in time :)

---

### Post by Ferrat on 2008-08-03
Ati drivers have some problems with GW, I'm using nVIDIA and GW works out of the box for me with WINE at a steady 50+ FPS with most stuff turned on but at medium (if I max it all out I get about 15-20FPS+) so the problem lies with ATi and nothing else =/

AFAIK ATi has had some real problems, specially with the Xpress cards when it comes to Linux

---

### Post by Vakman on 2008-08-03
> **Ferrat said:**
> Ati drivers have some problems with GW, I'm using nVIDIA and GW works out of the box for me with WINE at a steady 50+ FPS with most stuff turned on but at medium (if I max it all out I get about 15-20FPS+) so the problem lies with ATi and nothing else =/
All the more reason to get an nVIDIA card, which I still lack the money for :P. Which card do you have?

---

### Post by Ferrat on 2008-08-03
I have a GeForce 8600GT 512MB, they are pretty cheap and can handle anything on the market AFAIK, maybe not the best graphics on the latest games but still playable (besides the real problem on the latest games ain't the cards, it's the OS) :P 

but works great under Ubuntu :)

---

### Post by Vakman on 2008-08-03
I have tried the Envy drivers now. Screen becomes scrambled. Screenshot is below, sorry about the quality.
[ATTACH]80096[/ATTACH]

---

### Post by Vakman on 2008-08-04
Well I have Catalyst 8.5 drivers now. Screen does not become scrambled anymore but now I have an unrecoverable graphics error. I have now added the registry keys it said to on the Guild Wars AppDB page and still did not help. Anything else I could do?

---

### Post by Logical Dream on 2008-08-06
:/

---

### Post by Ferrat on 2008-08-07
> **Thisislaw said:**
> Well I have Catalyst 8.5 drivers now. Screen does not become scrambled anymore but now I have an unrecoverable graphics error. I have now added the registry keys it said to on the Guild Wars AppDB page and still did not help. Anything else I could do?


Only thing I can think of is to use earlier drivers but that's not really a good solution and the Xpress cards might work even worst with them =( 

I know the feeling you got, I had a x800 before, worked but most stuff was messed up so as soon as I could afford it I got a new system with a nVIDIA card, since then I've had no problems what so ever with graphics (just shows how far behind ATi still is on Linux, sad really, I like ATi otherwise)

---

### Post by Ferrat on 2008-08-07
Just to show the diffrence, with some tweaking of my system I'm now running with max on everything everywhere without any dips below 25FPS :)

EDIT:
BTW any Ubuntu Guild still active? :)

---

### Post by Vakman on 2008-08-08
> **Ferrat said:**
> Just to show the diffrence, with some tweaking of my system I'm now running with max on everything everywhere without any dips below 25FPS :)

EDIT:
BTW any Ubuntu Guild still active? :)
Well, as soon as I get a nVIDIA card or a new system and am able to run Guild Wars on Ubuntu or another distro, I am going to try to make my guild have a majority of Linux users. Currently, my guild is about 90 people with 250k faction or so. But I do want to have many Linux users in it but only after I get mine to work. But no I do not think any Ubuntu/Linux guilds are still active.

---

### Post by Vakman on 2008-08-08
P.S. I am looking at a few cards (EVGA e-GeForce 9600GT 512MB, XFX GeForce 8600 GT 512MB, and Geforce 8600 GTS 256MB). e-GeForce 9600GT and Geforce 8600 GTS are $100. GeForce 8600 GT $130. I don't want to to buy that one because the GeForce 8800 GT is only $149.99 on sale right now. $100 off. I guess I will see, I don't need amazing graphics, it is only Guild Wars. Only reason I am even considering buying a new card is because mine is ATI, not because I can't live with the graphics.

---

### Post by Ferrat on 2008-08-08
a 8600 or 8800 card will do more than fine with Guild Wars and maybe even more than ok with GW2, unless the rumors about it only supporting DX10 is true (wine needs more dx10 ^^) but since DX10 has been a real bust mostly and it has been really quite about it since the anouncement they might have reconsidered that :) 

Closed BETA was suppost to have started and alot of people have pre-ordered but not a word in a long time, so who knows. 

But as I said for guild wars on Linux any GeForce 8600 or 8800 will do the trick, I buy the 512 MB version, helps pretty much and as you said the diff. is $20 so I would go with a GF 8800 GT on that one, the drivers for the 8 series are stable and good.


EDIT:
Well figured more or less that there wasn't one active but never hurts to ask, looked up the e-ubun clan/guild but that since hasn't been updated for a year or more ^^ 

Don't play super actively and mostly PvE and most of that you can do with henchmen and heroes but still would be fun with some players on some missions, specially once with a lot of AoE dmg, henchmen really don't work well with that and sometimes they go bananas and pull more or less every mob on the map ^^

---

### Post by Vakman on 2008-08-09
Well you say I should go with the 8800 GT and it is a great card but I don't think I have enough power to support it.

---

### Post by aoanla on 2008-08-09
Hrm. What's your power supply rated for? I've had no problems with a 600W PSU and an 8800GT, and I know someone who claims to be okay with a 550W PSU...

---

### Post by Ferrat on 2008-08-09
> **aoanla said:**
> Hrm. What's your power supply rated for? I've had no problems with a 600W PSU and an 8800GT, and I know someone who claims to be okay with a 550W PSU...

I have a GF 8600 and a 530W PSU, depends on the quality of that PSU aswell but I have no problems what so ever in powering my system :)

---

### Post by Vakman on 2008-08-09
Well, I have posted another thread about how much I would need and what I actually have. I have googled my computer's model and it says I have a 250W which is what I read on the side of the power supply when I opened it up. Acer Aspire AST671-EP820A would be my computer, only difference is it is running with 2GB of memory now instead of the 1GB.

---

### Post by aoanla on 2008-08-09
250W is a bit underspecced for a modern power supply.
However, you can get new ones for surprisingly little expense - think of it as futureproofing (and lifetime proofing - bigger PSUs can age more before you notice the loss in efficiency, as you have more surplus capacity) your PC.

---

### Post by Vakman on 2008-08-09
The cheapest at Futureshop for example is $79, I won't be buying a new one soon.

---

### Post by Ferrat on 2008-08-10
If you got a second PSU you can use you could make a ghetto mod and have enough power, I did that once when my real PSU fried :D

---

### Post by Vakman on 2008-08-11
No idea how to go about doing that. If and when I get a laptop, I am making sure the graphics chipset is nVIDIA or Intel even... anything over ATI. Unless it improves somehow.

---

### Post by Ferrat on 2008-08-11
> **Thisislaw said:**
> No idea how to go about doing that. If and when I get a laptop, I am making sure the graphics chipset is nVIDIA or Intel even... anything over ATI. Unless it improves somehow.

Intel AFAIK is even worse on linux than ATi, well there is one easy way, connect one PSU to the motherboard but power all the other stuff that needs power from the other PSU, no modding needed then :) 

only drawback is that you prolly have to have your side open since most chassis ain't designed to use two PSUs :D

---

### Post by Vakman on 2008-08-11
The side of my computer is open anyway :P
And really Intel has more issues than ATI?

---

### Post by aoanla on 2008-08-11
Actually, Intel is pretty okay - the main problem is that Intel graphics solutions have historically been pretty useless compared to the hardware that ATI and nVidia produce. The most recent Intel graphics chipset looks pretty good, however, and, of course, there's always Larrabee to wait for...

---

### Post by Vakman on 2008-08-11
> **aoanla said:**
> Actually, Intel is pretty okay - the main problem is that Intel graphics solutions have historically been pretty useless compared to the hardware that ATI and nVidia produce. The most recent Intel graphics chipset looks pretty good, however, and, of course, there's always Larrabee to wait for...
Yes, that was my only concern. The actual performance of it. I know it is poor but at least they work... hope to maybe get a nVIDIA card soon.

---

### Post by Ferrat on 2008-08-12
oh, I just remember seeing all the Intel guys not being able to play anything but if that's just the hardware not drivers :) you learn something new every day :d

---

### Post by Spydr4590 on 2008-08-12
Nvidia isn't flawless on Ubuntu but it's the best solution out there right now.

---

### Post by aoanla on 2008-08-12
> **Ferrat said:**
> oh, I just remember seeing all the Intel guys not being able to play anything but if that's just the hardware not drivers :) you learn something new every day :d

Well, the intel 3d drivers aren't perfect, but they're not awful. The main issue is that the Intel 900 and 950 chipsets (which are the 915 and 945 graphics chips) are totally useless and are only borderline capable at gaming, even running games natively on Windows. A lot of laptops, in particular, get bundled with those for onboard graphics, which is why a lot of people who (for example) want to play WoW on their lappys have issues...

---

### Post by Ferrat on 2008-08-13
> **Spydr4590 said:**
> Nvidia isn't flawless on Ubuntu but it's the best solution out there right now.

I haven't run in to one single problem with them :) 



aoanla >> Ah ok :)

---

### Post by herteljt on 2008-08-16
Well I have another option for you, but it is just a workaround.  Instead of buying a new video card you can install an older different version of Ubuntu on your harddrive for the sole purpose of playing GW.

I installed 7.10 on a separate partition, installed the restricted drivers for the video card, downloaded wine and installed GW without issue.  It works best in the 98 compatibility mode on my machine.

This was easy for me because I have my /home on a different partition then root.

If you want more info let me know.

---

### Post by Vakman on 2008-08-16
> **herteljt said:**
> Well I have another option for you, but it is just a workaround.  Instead of buying a new video card you can install an older different version of Ubuntu on your harddrive for the sole purpose of playing GW.

I installed 7.10 on a separate partition, installed the restricted drivers for the video card, downloaded wine and installed GW without issue.  It works best in the 98 compatibility mode on my machine.

This was easy for me because I have my /home on a different partition then root.

If you want more info let me know.
That sounds great. I have no problems doing that or shouldn't. I have 7.10 on a CD but it always says Input Not Supported across my screen so I just used 8.04. How will it help to have 7.10 though? Would I not be using the same drivers?

---

### Post by herteljt on 2008-08-16
> **Thisislaw said:**
> That sounds great. I have no problems doing that or shouldn't. I have 7.10 on a CD but it always says Input Not Supported across my screen so I just used 8.04. How will it help to have 7.10 though? Would I not be using the same drivers?

I am a little fuzzy on where the "input not supported" error occurs.  Does this happen when you try to install 7.10 using a liveCD? 

As for your question on drivers, I'm not expert on what happens between distribution upgrades, but I know from experience that many different things are changed.   This is part of the reason I am a little hesitant when I upgrade from one version to the next as I will have everything working just the way I want it and then KABOOM new problems.  For instance from 6.10 to 7.04 I had major problems with graphics and from 7.10 to 8.04 I had to make some modifications to get sound working correctly.

In reading a bunch of different posts on the threads it seemed that people with ati cards had GW working in 7.10 so I downloaded the alternate install cd and installed it.  I also downloaded wine 1.0 from winehq.org  

After my usual install tweaks (I have to do a little work to get direct rendering [http://ubuntuforums.org/showthread.php?t=776607](http://ubuntuforums.org/showthread.php?t=776607) ) I downloaded GwSetup.exe and ran
```
wine GwSetup.exe
```

If you need any help on how to install on a separate partition feel free to ask.

---

### Post by Vakman on 2008-08-16
Input Not Supported bounces across the screen before it boots into the LiveCD (I have also tried using safe graphics mode). I am downloading the alternate install CD as I type this, well before you posted I had started it.

---

### Post by Vakman on 2008-08-17
Great news is I have Ubuntu 7.10 running. Updating with the security updates and what not. Do for the drivers, did you just use the ones in System > Administration > Restricted Drivers Manager? Or did you download the Catalyst drivers, if so which ones. And lastly, which version of Wine would be best, newest?

---

### Post by Vakman on 2008-08-17
Well I went ahead and installed the ones in the Restricted Driver Manager. I am about to install Wine 1.0 now, I guess I can always remove it for Wine 0.5.9 or whichever it is if I need to. Let me know if you have it working with an ATI card, which Wine version, what tweaks, and what drivers. Thanks.

---

### Post by herteljt on 2008-08-17
> **Thisislaw said:**
> Great news is I have Ubuntu 7.10 running. Updating with the security updates and what not. Do for the drivers, did you just use the ones in System > Administration > Restricted Drivers Manager? Or did you download the Catalyst drivers, if so which ones. And lastly, which version of Wine would be best, newest?


Here is what I did.

1) Go to System > Administration > Restricted Drivers Manager and install the ati accelerated graphics driver

2) Install wine 1.0 for Ubuntu 7.10 using the debian package:
[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_i386.deb)

3) Download the guild wars client:
[http://www.guildwars.com/downloads/gwsetup.zip](http://www.guildwars.com/downloads/gwsetup.zip)

4) Unzip the gwsetup.zip (just double click on it) and extract GwSetup.exe.  Make sure you know the location where you extract the file.  

5) Open a terminal and navigate to the directory of GwSetup.exe  then type:

```
wine GwSetup.exe
```

My AIM screen name is darkbeerm if you need any help :)

---

### Post by Vakman on 2008-08-17
That is exactly what I am doing now. Which is good I hope :)
I also did that on Ubuntu 8.04, also tried 8.7, 8.6, 8.5, 8.3 Catalyst drivers. Used Envy as well and that was 8.6 drivers. None worked. Currently installing GW as usual.

---

### Post by Vakman on 2008-08-17
Guild Wars keeps closing after I get to the login screen. There was a keyboard problem and if I do not run with WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" then there are a lot of fixme keyboard errors. But main problem is the closing. I was able to make the keyboard work by making it use a virtual desktop in wine config. Any ideas?

---

### Post by herteljt on 2008-08-17
> **Thisislaw said:**
> That is exactly what I am doing now. Which is good I hope :)
I also did that on Ubuntu 8.04, also tried 8.7, 8.6, 8.5, 8.3 Catalyst drivers. Used Envy as well and that was 8.6 drivers. None worked. Currently installing GW as usual.

Make sure you have desktop effects set to none.  System > Preferences > Appearance > Visual Effects Tab 

Also check to make sure you have direct rendering.  

Open a terminal and type:

```
glxinfo | grep rendering
```

It should return:
> direct rendering: yes

---

### Post by Vakman on 2008-08-17
Desktop Effects are set to none and the output was yes
```
thisislaw@ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes

```

---

### Post by herteljt on 2008-08-17
> **Thisislaw said:**
> Desktop Effects are set to none and the output was yes
```
thisislaw@ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes

```


Maybe try some registry editing?  There are instructions on appdb.winehq.org 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Other than that I am out of ideas right now.  I will keep looking.

---

### Post by Vakman on 2008-08-17
So far everything works except it keeps closing... rather a huge issue :(
I am going to try some reg keys again... they didn't help me in 8.04 maybe they will help me here.

---

### Post by Vakman on 2008-08-17
> **herteljt said:**
> Maybe try some registry editing?  There are instructions on appdb.winehq.org 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Other than that I am out of ideas right now.  I will keep looking.
Oh I didn't see this post, I must have been posting... meaning my last post was the right idea :) We will see, thanks. Also I notice that it has been downgraded to Gold... still to high in my opinion.

---

### Post by Vakman on 2008-08-17
None of those keys helped. Maybe I should try the Catalyst drivers again... but now on 7.10. ell if I got this far with 7.10, maybe I should use 7.04. or 6.10. Downgrade is starting to feel like and upgrade. Maybe I should try another version of Wine... an older one.

---

### Post by herteljt on 2008-08-17
I also found that it runs best in windows 98 compatibility, but you might want to try windows xp and windows 98 (in winecfg).

---

### Post by Vakman on 2008-08-17
> **herteljt said:**
> I also found that it runs best in windows 98 compatibility, but you might want to try windows xp and windows 98 (in winecfg).
I have tried every compatibility mode there is in there. All the way down to one of the Windows NT versions and up. Only works with Windows 98 and below, works to login screen and continues to work until it decides to close. Anyway I am going to Windows side now to play. As long as I do not have Guild Wars, I do not have Ubuntu or any other Linux distro for that matter. I probably will come back on this side later today. Thanks, if anyone knows about thsi problem, let me know even in game if I am not on here. My IGN is Paragon Law Law. Thank you.

---

### Post by lswest on 2008-08-17
just thought I'd post here about the Geforce and PSU issue:  my PC has a 500W PSU, a dual core CPU (intel), a Gigabyte Geforce 8600GT 512MB with passive cooling (Gigabyte SilentPipe II) and no issues. Also have 2GB of RAM, wireless card, etc. etc.  GPUs with fans usually need more power though.  I find the passive cooling fine (never more than 62 degrees where the threshold is 115 degrees).  It depends on the other hardware in the box I guess, but the card itself doesn't seem to need much.  Also, the motherboard, an asus P5KPL, offers the usual audio and USB ports, as well as two other USB ports.  So most likely the issue with the other cards are the fans.

My card:
[http://www.gigabyte.com.tw/products/VGA/Products_Overview.aspx?ProductID=2604](http://www.gigabyte.com.tw/products/VGA/Products_Overview.aspx?ProductID=2604)

---

### Post by Vakman on 2008-08-17
> **lswest said:**
> just thought I'd post here about the Geforce and PSU issue:  my PC has a 500W PSU, a dual core CPU (intel), a Gigabyte Geforce 8600GT 512MB with passive cooling (Gigabyte SilentPipe II) and no issues. Also have 2GB of RAM, wireless card, etc. etc.  GPUs with fans usually need more power though.  I find the passive cooling fine (never more than 62 degrees where the threshold is 115 degrees).  It depends on the other hardware in the box I guess, but the card itself doesn't seem to need much.  Also, the motherboard, an asus P5KPL, offers the usual audio and USB ports, as well as two other USB ports.  So most likely the issue with the other cards are the fans.

My card:
[http://www.gigabyte.com.tw/products/VGA/Products_Overview.aspx?ProductID=2604](http://www.gigabyte.com.tw/products/VGA/Products_Overview.aspx?ProductID=2604)
500W, I do not. Nor do I have enough money to buy another card... anyone have an idea about the ATI card?

---

### Post by Vakman on 2008-08-18
Remember, it is opening and closing. I can login but when it sits there. I can only login if I am quick. Point is it closes. Any ideas?

---

### Post by Vakman on 2008-08-21
It opens and closes. Without the debug code there are a lot of fixme things. If I have it in full screen and also not in Virtual environment then it will not crash but the keyboard doesn't work. If I put it in virtual environment, then the keyboard works. I will post two outputs of without the debug run and with.
Without:
```
thisislaw@ubuntu:~$ wine "C:/Program Files/Guild Wars/Gw.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec58,0x00000000), stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x133960,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e58c,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x13a2b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a2c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a2e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13a9b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13ada8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13b390)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13b7b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13bbe0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c008)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c430)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a2b0, 1, 0x13c888)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13a088)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a088, 1, 0x13a0a0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x13a050)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a050, 1, 0x13a068)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x13a080)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x13a080)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a080, 1, 0x13d9e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13a080, 1, 0x13da00)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x13e868,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e628,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x143758)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143770)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143788)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x143c00)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144230)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144810)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x144c38)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145060)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145488)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x1458b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143758, 1, 0x145d08)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143730)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143730)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143738)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143738, 1, 0x143750)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x143710)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x143710, 1, 0x143728)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x1460d8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1436e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1436e0, 1, 0x1436f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1436e0, 1, 0x146e80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
dontfixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x151a40) : stub

```
And when it has the debug run and closes, it says nothing at all. No output in terminal.

---

### Post by Naiki Muliaina on 2008-08-21
I should apologize for a late reply, i thought id replied to this a few days ago. Anywhos, the problem is an frglx problem. Wine devs wont help at all with this problem, as far as they are concerned its a driver problem not a wine problem. Fair dos i guess, its ATI's problem realy. Anywhos! Something possible to try. The very newest ATI drivers are meant to be a huge improvement. The newest drivers arnt in the repos. So you have to install them manually. 

Follow the guide for method 2 (method 2 only, method 1 is just for the repos) in the following link.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Have no idea if it will help, but they are meant to be a huge improvement.

---

### Post by Vakman on 2008-08-21
Well I will try that later. I know about the fglrx problem. But someone with simply the restricted drivers got it working and they have an ATI card. But I will those later. And by new you mean 8.7 or 8.8? If 8.7, then I have tried and they were the worst.

---

### Post by Naiki Muliaina on 2008-08-22
8.8 i think, good luck!

---

### Post by Vakman on 2008-08-22
Okay no... it seems the drivers are not installed. I have the control center and such but not the drivers. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Tells me how to install the drivers. But two steps I do not understand.]
> sudo dpkg -i fglrx-kernel-source_<version>.deb
sudo dpkg -i xorg-driver-fglrx_<version>.deb
It could not do either of those. File was not found I think it was. I tried entering stuff for the <version> and it also didn't help. So far my best so far has been the ones in the restricted drivers manager. Oh and your setup for the drivers before (your link) was for Hardy Heron 8.04, I now use Ubuntu 7.10 because it has shown the best results so far. So anyone?

---

### Post by herteljt on 2008-08-22
> **Thisislaw said:**
> Okay no... it seems the drivers are not installed. I have the control center and such but not the drivers. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Tells me how to install the drivers. But two steps I do not understand.]

It could not do either of those. File was not found I think it was. I tried entering stuff for the <version> and it also didn't help. So far my best so far has been the ones in the restricted drivers manager. Oh and your setup for the drivers before (your link) was for Hardy Heron 8.04, I now use Ubuntu 7.10 because it has shown the best results so far. So anyone?


I'm still looking for a solution to your problem, but nothing big has turned up.  

Have you looked at this thread?
[http://ubuntuforums.org/showthread.php?t=765565](http://ubuntuforums.org/showthread.php?t=765565)

It discusses fglrx issues.  Also, I read somewhere that people were having success using Envy to install the restricted drivers.  Just another couple of suggestions.  Best of luck!

---

### Post by Vakman on 2008-08-22
Envy drivers have always forced me to do a fresh install. I have used EnvyNGG when I had 8.04 and Linux Mint 5. This time I tried Envy Legacy or whatever it is. Envy has never solved any problems. If anything it has always made it worse. Also that thread is regarding problems with Hardy Heron, the person did not have the problems with 7.10, which I still do. I also tried the 8.8 Catalyst drivers, which didn't seem to work.

---

### Post by Naiki Muliaina on 2008-08-23
2nd post from bottom: [http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)

> 
I can play Guild Wars again!

This seems to have to do with Bug 12929, directx problems with fglrx drivers.

Here is what I have to do.

Goto [http://bugs.winehq.org/show_bug.cgi?id=12929](http://bugs.winehq.org/show_bug.cgi?id=12929).

First, if you get libGL drmMap errors, you need to get the reverse_preloader
patch I put there.  That fixes that error for me.

Secondly, comment out the two lines mentioned in that bug report that are found
in dlls/wined3d/directx.c.

Now I can run Guild Wars with -nosound.  I just have to find out how to fix the
stack overflow error I get when I try and play it with sound.

Other than that, Guild Wars works! 

I am running Ubuntu 8.04, Catalyst 8.6, with an HD2600 Mobility.

Tell me if it works for you!


[http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)

---

### Post by Vakman on 2008-08-23
> **Naiki Muliaina said:**
> 2nd post from bottom: [http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)



[http://bugs.winehq.org/show_bug.cgi?id=12870](http://bugs.winehq.org/show_bug.cgi?id=12870)
I have seen this. I believe I am the last post on that 12870 page (Lawrence) asking Forest Loomis or something to explain what he did. I went to that page and didn't quite understand? Can you explain it. How to use this attachment and where to download it etc? It seems I have to install from source... and I have no idea how to. I will try to figure it out I guess. So I guess I am stuck with Windows Vista for now.

---

### Post by Naiki Muliaina on 2008-08-23
Ill have a go at that post tommorow (bit late for me now), post my results, and see if i can explain it clearer if i get it to work. Im currently using an x1950, 256ram, just so you know :)

---

### Post by Vakman on 2008-08-23
Okay. If anyone knows before tomorrow, that is great as well. I am working pretty much all of tomorrow. Currently, I am just using Windows. Chances are as long as this is an issue that will not be solved (it has been over 1 month now...) I can't use any Linux distro. Getting very angry as well as impatient.

---

### Post by marsmissionaries on 2008-08-24
The 8.8 driver does not work either. You will need to downgrade to a driver that does work (8.4 apparently)

---

### Post by Vakman on 2008-08-24
> **marsmissionaries said:**
> The 8.8 driver does not work either. You will need to downgrade to a driver that does work (8.4 apparently)
I have tried 8.8, 8.7, 8.6, I think also 8.5, and maybe 8.3. The Catalyst drivers always mess up my system somehow. 8.7 worked fine as did 8.3 but still problems with Guild Wars. I suppose I will also try 8.4 since that is the current suggestion.

---

### Post by Vakman on 2008-08-25
So it seems that the Catalyst 8.4 drivers did not install correctly? When I open the Control Centre for it, it says ''No ATI driver detected'' or something like that. Sorry, do not remember fully. On Windows right now, obviously seeing how Guild Wars does not work, so I will check again after but basically that is what it said.

---

### Post by Vakman on 2008-08-25
Well now, I have done something. It no longer gives me the error when I try to open the Catalyst Control Centre. But now it doesn't say anything or open when I try to. And when I enter
```
glxinfo | grep rendering
```
to check it gives me
```
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
So far my best has been with whatever drivers are in the restricted driver manager but it kept closing when I had those.

---

### Post by Vakman on 2008-08-28
So nobody has any more ideas?

---

### Post by Extreme Coder on 2008-08-28
> **Thisislaw said:**
> So nobody has any more ideas?
Your ATI driver has not been installed correctly, hence the errors.
I'm in the same boat you are(actually, I'm not trying to run Guild Wars(hopefully will buy it soon), but other 3D games), and a lot of 3D games don't work with wine.

I suggest you to use Catalyst 8.4. (Try the installer, without building any package). It works like Catalyst 8.5(last version without 3d corruption), and no performance problem like 8.5.
Suggestions are:
1) Use Cedega. The whole 3D games not working with Wine was caused by a recent patch to wine that messed up everything. Cedega was built from a much older version of Wine, without the troublesome patch, which means 3D should work fine. This was proved when my friend wanted to install WoW on my PC. I had a lot of 3D issues with it on Wine, not working and stuff, but it worked without a hitch on Cedega. (I use Mandriva PWP, and Cedega comes for free with it :P . If you want it, let me know.)
2) Compile Wine without the troublesome patch. According to the bug page in WineHQ, lot of people had success when recompiling without the patch. Personally, I haven't tried this, but I do plan on doing so soon.

Good luck, let me know how it goes.

Ahmad Yasser.

---

### Post by Vakman on 2008-08-28
Well. 8.4 is the only one that was not installed correctly. Every other time I have installed a Catalyst driver, they installed correctly. But all right. And no I will not compile Wine. Which version should I use? 0.59 is that old enough, I think that is the version number. Why does it seem like a downgrade is always an upgrade...

---

### Post by Extreme Coder on 2008-08-28
> And no I will not compile Wine.
Why not? :/

Actually, I'm compiling ATM, if you want, do you want to send me a deb with the patch removed?

---

### Post by handy on 2008-08-28
You could try the fully functional demo of Crossover Games?

They are the primary contributors to Wine also.

***_[http://www.codeweavers.com/products/cxgames/download_trial/](http://www.codeweavers.com/products/cxgames/download_trial/)_***

I use their Crossover Games to play Guild Wars on my iMac under Leopard.  Primarily because it looks much better than it does under either Cedega or Crossover under the Linux ATi drivers, on the same machine.

This whole problem is due to ATi's poor Linux (& Mac) drivers.

---

### Post by Vakman on 2008-08-29
> **Extreme Coder said:**
> Why not? :/

Actually, I'm compiling ATM, if you want, do you want to send me a deb with the patch removed?
Sure... I think. Thanks. And I have used Crossover Games and Crossover before but it does not help seeing how the main problem is with the ATI drivers as you said.

---

### Post by Extreme Coder on 2008-08-29
> **Thisislaw said:**
> Sure... I think. Thanks. And I have used Crossover Games and Crossover before but it does not help seeing how the main problem is with the ATI drivers as you said.
So you tried both, and they didn't work still?

---

### Post by handy on 2008-08-29
> **Thisislaw said:**
> Sure... I think. Thanks. And I have used Crossover Games and Crossover before but it does not help seeing how the main problem is with the ATI drivers as you said.

Crossover Games is easy to install & run Guild Wars with; if I were you I'd test with it just to get another verification on the driver issue.  You never know your luck, CxGame might even work!?

The demo' is fully functional.

---

### Post by Vakman on 2008-08-29
> **Extreme Coder said:**
> So you tried both, and they didn't work still?
I have tried both. With Crossover I got 1 FPS at one time... so then I started wondering about the drivers about a month ago and found that ATI drivers do not work well. And all right I suppose I can try again.

---

### Post by lawentzel on 2008-08-29
Just been playing with Guild Wars trying to get it up and running.  Just going into the initial interface was very problematic.  I tried configuring Wine to run as a virtual desktop and this resolved my problems.  The speed increased.  The interface became usable.  So, I would give that a try.  Good luck.

Lee

---

### Post by Naiki Muliaina on 2008-08-31
Sorry for the very late re reply. It was my first time doing such a thing on Ubuntu. I got GW working. But...

> **Thisislaw said:**
>  And no I will not compile Wine.

Afraid for the moment then thats the end of the line for you then. Sorry but thats the only way anyone seems to know of getting GW going on Wine with ATI cards. :(

From what i understand, Crossover is based on Wine, so that will be a no go too. Cadega however is meant to work differently. Anyone know anyone with an ATI card and a Cadega sub who could spare us a few minutes? :)

---

### Post by handy on 2008-08-31
> **Naiki Muliaina said:**
> Sorry for the very late re reply. It was my first time doing such a thing on Ubuntu. I got GW working. But...



Afraid for the moment then thats the end of the line for you then. Sorry but thats the only way anyone seems to know of getting GW going on Wine. :(

From what i understand, Crossover is based on Wine, so that will be a no go too. Cadega however is meant to work differently. Anyone know anyone with an ATI card and a Cadega sub who could spare us a few minutes? :)

Compiling may have been what you needed to do for your hardware setup, someone else with different hardware will get it to work without compiling.

I use Crossover to run GW, it does a vastly superior job than Cedega on the same hardware, & it is easier to set up.  The Crossover forums are watched carefully by the dev's who happen to be the primary contributors to the Wine project.  Also, I might add they are really nice people, as opposed to the opposite reality that I have experienced with the Cedega forums & their administration.

Crossover & Cedega can both work when Wine won't.  I prefer to use Crossover for everything except to play Oblivion, due to the simple fact that it won't work with Crossover at this stage.  Even though it will with both Wine & Cedega, running it via Wine being a lot more complicated than doing the same via Cedega.

---

### Post by Naiki Muliaina on 2008-09-01
Did just edit in the ATI at the end of the secound scentence, your right, and im not very clear on the ATI bit.

Hmm buts thats intresting Handy, so GW works in crossover now with ATI cards? That realy is fantastic, might pick up a sub again for it have a go. Missing a lot of my old mates from GW. 

I hear ya on Cadega being less nice. I didnt have a very good time when i first tried  Cadega so never tried it again. I dont like giving money/support to companys im not keen on heh.

---

### Post by handy on 2008-09-01
*@**Naiki Muliaina**:* Give the free Crossover Games demo' a try before you buy, it's there so people can verify if CX Games will do the job for them.

All the best. :-)

---

### Post by Naiki Muliaina on 2008-09-01
No luck :( Im using an ATI PCI-E x1950. Worth a try, although ive gotten Wine working, sounds a nono. Im certainly not skilled enough with linux to fix that on me own heh. Theres a couple of insta crash areas too (eotn only, might just be the low spec pc im running atm).

What graphics card are you using Handy?

---

### Post by handy on 2008-09-01
I use an AGP XFX GeForce 7950GT / 512Mb, which is a card from hell to set up under all distro's except the Sabayon 3.4a e & f versions (3.5 won't have a bar of it!).  I spent a LOT of time getting that card to work with Arch, eventually discovering that even though it is an AGP card, it needs to have AGP turned OFF in xorg.conf.  My theory on that is due to the 79** chipset having been designed for PCI-E, & with XFX building an AGP card out of it, it confuses the hell out of X.

The other machine has a PCI-E ATi RadeonHD2600 / 256Mb, which is an inferior card spec wise to the nVidia card, though it plays GW beautifully via CX-Games under Leopard.  It displayed GW under Ubuntu, more poorly, due to the inferior ATi Linux drivers.

GW, does still have some issues under CX-Games on Leopard; there is a lights on / off problems in certain parts of the ice country in GW, (Ice Tooth Cave is the easiest place to experience this problem) & on the iMac's at least, the mouse pointer occasionally disappears, which is a game breaker. Apart from that, with DX-9 functioning it looks so incredibly good, GW under Cedega looks very poor by comparison, from my experience.

So I don't use GW under Linux anymore due to CX-Games doing such a good job on my large screen iMac. As previously mentioned in this thread, I have to play Oblivion under Sabayon/Cedega, because it CX doesn't handle it at this point.  It could be due to copy protection issues that Transgaming license their way around, I don't know.

As far as your GW sound & Wine is concerned; I know you are aware of [***_the huge GW thread started by Jarn_***]("http://ubuntuforums.org/showthread.php?t=283122&highlight=guild+wars"), is there no help in there for you?

---

### Post by Naiki Muliaina on 2008-09-02
Afraid not, either the awnsers not there or im not looking hard enough. It could just be my PC. Ive found with linux there are some times when everything just works for you. Other times things just dont. Sound on this PC could just be one of the 'donts'.

---

### Post by Vakman on 2008-09-02
So I have tried Crossover Games again. The game opens and does not seem to crash soon after. But the game is, trying to think of a word... slow I suppose until I think of a better one, that it is unplayable.
Should I be doing anything special with Crossover Games as I would with Wine?

---

### Post by handy on 2008-09-02
> **Thisislaw said:**
> So I have tried Crossover Games again. The game opens and does not seem to crash soon after. But the game is, trying to think of a word... slow I suppose until I think of a better one, that it is unplayable.
Should I be doing anything special with Crossover Games as I would with Wine?

Have you worked with the GW Options Menu/Dialogue?

You will need to cut back on graphics options quite a bit, to suit your graphics card, you may very well find that it makes a world of difference.  Unless of course you already have, under those circumstances, you will most likely need to replace your gfx card. :-(

---

### Post by Vakman on 2008-09-02
> **handy said:**
> Have you worked with the GW Options Menu/Dialogue?

You will need to cut back on graphics options quite a bit, to suit your graphics card, you may very well find that it makes a world of difference.  Unless of course you already have, under those circumstances, you will most likely need to replace your gfx card. :-(
I don't think I need to replace my card... I get anywhere from 20-50 FPS while running it on Windows. Things would be so much easier if companies would step up and have the programs also made for Linux. Like at Login Screen it is so laggy. I had trouble switching the options to lowest. By the way, already had done that, did not help.

---

### Post by Vakman on 2008-09-02
So I changed some of the setting in the winecfg for Crossover Games and it is no longer laggy but I have the same problem that I had with Wine, it crashes.

---

### Post by handy on 2008-09-02
> **Thisislaw said:**
> I don't think I need to replace my card... I get anywhere from 20-50 FPS while running it on Windows. Things would be so much easier if companies would step up and have the programs also made for Linux. Like at Login Screen it is so laggy. I had trouble switching the options to lowest. By the way, already had done that, did not help.

Sorry, I should have been more descriptive:  My thoughts are that to get around your problem with that ATi gfx card & its poor Linux drivers, you will need to get another card.  Which is a shotgun call when in reality I have not seen your computer.

All the best.

---

### Post by handy on 2008-09-05
*@**ThisisLaw**:* I am in a similar boat to you, in that I choose to play GW via Crossover Games under Leopard, on my dual booting iMac, because the ATi Linux drivers are that much poorer than the ATi Mac drivers.

Also, I must play Oblivion on my 2nd machine that has an nVidia 7950GT 512Mb card in it, as the ATi Linux drivers won't cut on the iMac, Oblivion is just unplayable.  (Unfortunately Crossover Games doesn't support Oblivion at this stage.)

The quality of drivers is a critical factor, most especially with regard to GPU's as they can be more complex pieces of hardware than CPU's.

---

### Post by Ferrat on 2008-09-07
shocking really that ATi still haven't produced better linux graphic drivers, sure nVIDIA still has some issues but works with most things without any major troubble and ATi's promise of better linux drivers, sure they improved them a bit then it's as if they just gave up. 
And with the linux market exponentially growing every year the "boom" isn't that far of while ATi is slipping behind =/

---

