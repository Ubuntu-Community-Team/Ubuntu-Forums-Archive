---
title: "Graphics problem running WOW"
date: 2008-06-30
forum: Wine
---

### Post by KRAKALACKIN on 2008-06-30
I am running ubuntu 8.04 on a Toshiba Satellite 1135-S1554 Laptop. It has an integrated 32mg video card and I know that’s not the best for performance but I was running WOW in XP on this laptop and it worked fine. Using wine and running in openGL, Inside/enclosed environment run fine, but the outside/open world environments have graphic glitches and the fps drop and runs ready slow. The ground texture has no detail and some multicolor graphic glitches. I have changed the performance settings and still no change.  Any ideas???

---

### Post by BlackSwordD2 on 2008-06-30
[http://ubuntuforums.org/showthread.php?t=579378]("http://ubuntuforums.org/showthread.php?t=579378")

try that forum, it has ways to fix some of your issues (such as the graphics for the floors) to up your fps, turn your vivual effects in preferences to none before you run WoW and it solved all those problems for me

---

### Post by KRAKALACKIN on 2008-06-30
turn down the visual effects in WOW or wine? I already did in WOW.

---

### Post by KRAKALACKIN on 2008-06-30
I see no change with tweak#1. Here is what my registry editor looks like.

---

### Post by KRAKALACKIN on 2008-06-30
Now I have changed WOW to full screen mode and now i cant use the keyboard in wow ( I CANT LOG IN ) WTF?! PLEASE HELP!!!

---

### Post by Ptero-4 on 2008-06-30
What he meant is to turn off compiz-fusion (go to system>preferences>appearance, go to the desktop effects tab and select "none") before starting WoW and turning it back on when you close WoW.

---

### Post by BlackSwordD2 on 2008-07-01
> **KRAKALACKIN said:**
> Now I have changed WOW to full screen mode and now i cant use the keyboard in wow ( I CANT LOG IN ) WTF?! PLEASE HELP!!!

post the output of 

```
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wtf/Config.wtf
```

and i'll see what matches mine and what doesn't. and yes i did mean turn off compiz-fusion stuff i have my WoW settings at normal to high settings so maybe that will help the keyboard issue?

---

### Post by BlackSwordD2 on 2008-07-01
you know what, are you using the -openGL at the end of your script to run WoW?

such as 
```
$ cd /home/"user"/.wine/Program\ Files/drive_c/World \ of\ Warcraft/ wine Wow.exe -openGL 
```

thats the method on how to get it to work, linux does co-op well with directX so we must use openGL to bend it to our will

---

### Post by thisismalhotra on 2008-07-01
I have followed these guides for WoW.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

Please give us spec of your system specially your video card cause if you have an Intel or an Ati buddy you are in for a rough ride. Both of them are hit and missed it works for some absolute disaster for others.

Anyways Make sure you run wine in windows XP mode. 
Add lines given in the above first link for opnegl and other stuff plus add the lines to config file in the post below..

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

All in all add following to your config.wtf

```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
```

GL

---

### Post by KRAKALACKIN on 2008-07-01
I do turn off Compiz-Fusion before I play. Last night when I got off I unistalled WOW and wine. Tonight I'm going to reinstall and try the fixes that all you have recommended. I had made so many changes that i could remember how many or which ones I had already done. All I know is none of them worked. I'm new to linux(been using it for 4 days) so the whole concept is new to me. The file system and using command lines. I'm experimenting with ubuntu on my laptop in hopes of converting my media pc to linux, but I would like to run wow on both. Thanks for all of your help and I will keep you posted! Let me know if you have anymore ideas!

---

### Post by BlackSwordD2 on 2008-07-01
> **thisismalhotra said:**
> I have followed these guides for WoW.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

Please give us spec of your system specially your video card cause if you have an Intel or an Ati buddy you are in for a rough ride. Both of them are hit and missed it works for some absolute disaster for others.

Anyways Make sure you run wine in windows XP mode. 
Add lines given in the above first link for opnegl and other stuff plus add the lines to config file in the post below..

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)


All in all add following to your config.wtf

```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
```

GL


these are the same tutorials i used to get mine to work, only i didn't have to change the last two sound options (SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150") and also to give you hope for your lappy, im running it on both an intel processor and an ATI card

---

### Post by KRAKALACKIN on 2008-07-01
> **thisismalhotra said:**
> 
Please give us spec of your system specially your video card cause if you have an Intel or an Ati buddy you are in for a rough ride. Both of them are hit and missed it works for some absolute disaster for others.

Anyways Make sure you run wine in windows XP mode. 
Add lines given in the above first link for opnegl and other stuff plus add the lines to config file in the post below..
GL

Laptop Specs
P4 2.2ghz
512 Ram
30gb hd
32mg video (think it's ati but not sure)

HTPC Specs
AMD939 2.2ghz
2gb ddr ram
320gb hd
256mb nvidia6600 video
realtek 7.1 audio

---

### Post by KRAKALACKIN on 2008-07-01
Reloaded wine and WOW and this is the result:

First picture is before any fixes and second picture is after on applied fixes. I have followed all suggested fixes. Anymore ideas? PLEASE!!! :)

---

### Post by BlackSwordD2 on 2008-07-02
maybe i'm crazy...but what is still wrong?

can it run?

---

### Post by thisismalhotra on 2008-07-02
> **BlackSwordD2 said:**
> maybe i'm crazy...but what is still wrong?

can it run?

LOL you are partially right but there is some blurring on the top left side of the screen. 

To KRAKALACKIN: can you log in a see what happens, specially check that if the graphics go blurry when you mov from out door to indoor and vice versa. Did you do the registry tweak for FPS??

Also, pls post xorg.conf file and you config.wtf.

*Note: Man have been playing TBC so long that I did not remember the original wow login screen .. thanks for the screenshots ... this is som much better than the dark portal*

FTW

---

### Post by thisismalhotra on 2008-07-02
> **BlackSwordD2 said:**
> these are the same tutorials i used to get mine to work, only i didn't have to change the last two sound options (SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150") and also to give you hope for your lappy, im running it on both an intel processor and an ATI card

Not picking on you but I meant Intetl video cards/graphics adapters, and Ati video card. I have a laptop with xpress radeon 200m and could not get wow to work on it for last 6 months now.

Anyways I am happy you are tranformed to linux eve with WoW, Why not blizzard just support it they have a mac client, which is unix based I dont think it will be a lot of work to make a linux client :(

---

### Post by KRAKALACKIN on 2008-07-02
> **thisismalhotra said:**
>  

Also, pls post xorg.conf file and you config.wtf.



I'm sorry, I don't understand what you are saying. Could you give me more detail? Thanks!

I did do the registry tweak(see post on page 1 for the screen shot of the registry).

I'm still updating the new install so I can't play it yet. The first time I installed it though, the frame rate indoor and textures were great! The texture quality when to crap when I went outdoor and the frame rate dropped 200%. What causes this?

---

### Post by BlackSwordD2 on 2008-07-02
> **KRAKALACKIN said:**
> I'm sorry, I don't understand what you are saying. Could you give me more detail? Thanks!

I did do the registry tweak(see post on page 1 for the screen shot of the registry).

I'm still updating the new install so I can't play it yet. The first time I installed it though, the frame rate indoor and textures were great! The texture quality when to crap when I went outdoor and the frame rate dropped 200%. What causes this?

i know the config.wtf is in your WoW program folder in the WTF folder but i forget how to get to the xorg...i think its in ect?

---

### Post by KRAKALACKIN on 2008-07-02
What is xorg? Do I need to change it?

---

### Post by BlackSwordD2 on 2008-07-02
> **KRAKALACKIN said:**
> What is xorg? Do I need to change it?

ok i found it slap this into your terminal

```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by KRAKALACKIN on 2008-07-02
> **BlackSwordD2 said:**
> ok i found it slap this into your terminal

```

gksudo gedit /etc/X11/xorg.conf

```

I got open, but what do I need to do in it? Sorry if this a stupid question!:)

---

### Post by KRAKALACKIN on 2008-07-02
I looked up the specs on my laptop and it has the following vga:

32MB internal Integrated Intel® 852GM video memory

How or can I install drivers for this?

---

### Post by KRAKALACKIN on 2008-07-02
UPDATE!!! IN GAME SCREENSHOTS!!!

OUTSIDE GRAPHICS 
poor graphics and 5+/-fps
INSIDE GRAPHICS
quality graphics and perfect fps
Please let me know your thoughts and suggestions on what may be causing this. I will try and retry anything!!! :KS

---

### Post by BlackSwordD2 on 2008-07-02
> **KRAKALACKIN said:**
> I got open, but what do I need to do in it? Sorry if this a stupid question!:)

he wanted you to copy and paste, and unfortunatly the computer at work cant read those images you posted  so ill check those in an hour or two when im off

---

### Post by BlackSwordD2 on 2008-07-03
[WoW Troubleshooting]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting")

thy that out and see if any of those problems can be fixed by it

---

### Post by pferpaddy on 2008-07-03
ugh iv seen this problem before when i was running mandriva its driver related and can be fixed with a better one its simply the opengl or directx having promblems because of lack of reousrce prob

---

### Post by thisismalhotra on 2008-07-03
> **KRAKALACKIN said:**
> I looked up the specs on my laptop and it has the following vga:

32MB internal Integrated Intel® 852GM video memory

How or can I install drivers for this?

Can you post the output of this command

```
lspci -v
```


To install driver go to Hardware Managers/Restricted Driver Manager(depends on your version) in ubuntu and install drivers for Intel GMA(here is a link which shows nvidia but the same should work for you  [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)). Most likely you will need all the repositories enabled for this.(this link will tell you how to enbale the repos - WARNING only use the gui option dont touch the command line plz   [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources))

If the above driver install way does not work for you, here is how somebody else did it [http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)


Also When I said post the output of config.wtf and xorg.xonf I meant open those to files and copy and paste the content to a text file and attach in forums or just copy and paste it dirctly in forums.

config.wtf can be found in your WoW folder under dierctory WTF.

You can use the follwing code for your xorg.conf -thanks BlackSwordD2

```
gksudo gedit /etc/X11/xorg.conf
```

You donot have to do anything with these files now as we just need to look at them to see if there are any errors on those.

Also since you are I just want to make sure are you running wow in opengl mode??
Also did you try to use windowed mode and see if that helps??

GL

---

### Post by KRAKALACKIN on 2008-07-07
I am running in opengl mode and the game is windowed.
I'm having trouble installing the graphics driver. The driver manager doesnt see it. How can I install driver? I downloaded the straight linux driver.

---

### Post by thisismalhotra on 2008-07-08
> **KRAKALACKIN said:**
> I am running in opengl mode and the game is windowed.
I'm having trouble installing the graphics driver. The driver manager doesnt see it. How can I install driver? I downloaded the straight linux driver.

Please post the link from where you downloaded the driver I can than give you instruction how to install it.:)

---

### Post by KRAKALACKIN on 2008-07-08
> **thisismalhotra said:**
> Please post the link from where you downloaded the driver I can than give you instruction how to install it.:)

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=939&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=939&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

I downloaded driver 2 ( embedded for developers )

Thanks for all your help :)

---

### Post by thisismalhotra on 2008-07-09
This might be your issue with this driver...

```
Linux* support for the following distributions:
&#8212; Damn Small Linux*
&#8212; Fedora Core 5*, 6 & 7
&#8212; SUSE Enterprise Server (SLES) 10 and 10+ Linux
&#8212; Novel Linux Point of Service (NLPOS) 9 service pack 3
- Note: New Intel Kernel Module provides a Linux agnostic solution to add IEGD to ammost any distribution.
```

Pls post output of this command

```
lspci -v
```

What the make and model of your PC??

EDIT: This might be answer to your troubles mate

[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

---

