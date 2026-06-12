---
title: "WoW+UBU8.04+WINE1.1.2"
date: 2008-07-28
forum: Wine
---

### Post by xikarrousx on 2008-07-28
hey guys... i'm not new to ubuntu... i'm not new to computers, or WoW... but im getting frustrated here lol...

i have WoW 2.4, ubuntu 8.04 and wine 1.1.2 running on 2.5 GB ram, intel embedded graphics card and 2ghz. not a shitttty computer, but not top of the line either.. 

point of the thread is: I am getting 7fps ingame with the LOWEST settings and i cant figure out why!! ive done the regedit tweak, ive configured wincfg and config.wtf, ive added the dll files to system32, compiz is turned off, and i even did the nano -w ~/launch-wow.sh thing...

am i missing something? ive had some really shitty computers run WoW better than this with XP... and that had the graphics cranked up a bit!

but, im an ubuntu user, and im not leaving... however, it would be nice if someone knows a fix :)

---

### Post by Spydr4590 on 2008-07-28
Edit: NM Saw the regedit. Nothing else I can think of.

---

### Post by xikarrousx on 2008-07-28
DAMN! well, worth a shot! im going to keep searching for answers.....

---

### Post by Mahinva on 2008-07-29
Only thing I can think of for the registry tweak applies to step 6. When I did step 6 initially, I did not put DisabledExtensions in quotations. However, after changing it to "DisabledExtensions", I noticed my fps went up better indoors.

I'm sure my fps would be better outside, but my processor is old and seems to be affecting my performance in that respect.

My CPU is a Pentium 4 2.8gig, and I get roughly 13 fps outside, but inside and in instances that can go up to 20-60 fps. I run ion 2.5gig DDR RAM, an nVidia FX 5500 card as well. I have no idea if my computer is capable of getting higher fps without replacing hardware. The only thing I could replace is my CPU chip, but I haven't found a better one for a good price.

You could try the following graphic settings tweaks found here:

[http://blog.danielgovier.com/?page_id=362](http://blog.danielgovier.com/?page_id=362)

The post is a bit outdated, so you will certainly want to add each macro value one at a time and test the macro. I know one of the values has been changed by Blizzard so that it can not be set under "3". Here is the macro I use:

/console detailDoodadAlpha 100
/console showDetailDoodads
/console showLowDetail
/console horizonfarclip 400
/console farclip 50
/console SkyCloudLOD 1
/console smallcull 0
/console groundeffectdist 140
/console maxlod 3

One click of the icon will turn settings down, but if you click again, you will notice some graphic settings increase because some of those console commands are on/off toggles.

---

### Post by xikarrousx on 2008-07-29
holy crap man... i didnt even think about the quotations... im pretty excited about trying that in a half hour when i get back home lol. 

thanks for the links and suggestions, ill keep ya posted on any progress!

---

### Post by Mahinva on 2008-07-29
I really hope it works; I've found those registry edits posted several places and sometimes they include the quotations and other times they do not.

Heck, I went and installed those DLL files (as I didn't have 3 of them) but that didn't seem to change a thing. :\

One other thing that you may want to do is make sure that your drivers are up to date.

Aside from this, I've run out of ideas.

---

### Post by flytripper on 2008-07-29
here is the one i would recommend: [https://help.ubuntu.com/community/WorldofWarcraft#Configuration]("https://help.ubuntu.com/community/WorldofWarcraft#Configuration")

---

### Post by pkl266 on 2008-07-29
It might have to do with your intel graphics. I normally don't get good performance off of them in windows, and I imagine there is some performance cut through wine. Have you thought about adding in a cheap nvidia card? newegg usually has great deals for decent cards.

Edit: Also, where is it that you are testing your FPS. If it's a main city 7 FPS may be the best you'll get. The game still might be playable in less crowded areas.

---

### Post by xikarrousx on 2008-07-29
how do you update graphics card with a laptop?

oh, and i already did the config.

---

### Post by xikarrousx on 2008-07-30
okay... so this is where i stand right now.

after installing wow, i deleted all of the files.. the files in the directx folder from disc one wouldnt delete out of the trash. i said **** it for a while until i could get wow running smooth. i did all of the tricks, tweaks and reg edits and it helped A LITTLE, but nothing significant. i liked the macro tho, that def added a few fps.

but then i noticed that something was using up 97% of my ram... which is 2.5gb running linux! i knew something was wrong... i found out that it was the directx **** that was in the trash. by this time, my laptop was running so slow... as if i was running ubuntu on a palm pilot or something lol... so i had to reinstall ubuntu because it was tooooo slow and i couldnt even get into nautilus with root permissions to delete the files...

my brothers computer had the same files in the trash, but i was able to delete his in time. same thing happened (about 97% resources used).. i started up wow with his desktop running 512mb ram and its getting like 30 fps outside! 

so yeah, im totally excited to get this computer running wow right... and i think ive got it now! now i just have to get through the 8 days of patching and updating lol.

thanks for all of your help!

---

### Post by flytripper on 2008-08-01
hehe. save all the patches on disk..

---

### Post by faceonkeyboard on 2008-08-01
I'm on the verge of killing myself. I need help so desperately I would pay someone 100 dollars, seriously! To help me get WoW+Ubuntu 8.0.464bit+Wine 1.1.2.

Im super new to Ubuntu, maybe a week old.  However im not new to computers, so its easy to read and learn for myself. However im not sure if Im missing a step or what but im following the offical Ubuntu guide on getting WoW setup and running but... big but...

I copied all the disc's to the way in the guide, I launch the install, but here is where I get confused becuase I don't understand Ubuntu's insane directory structure. I leave the default's C:\program files\world of warcraft is that ok? I thought ubuntu or linux could not read spaces.  So much contradictory and stuff, im sooo lost.

Can someone help me walk through this setup? I will make you happy if you got paypal.

I have the base OS and video card drivers installed and updated.  I just need help installing wow into the file structure and then launching.

System spec's:
AMD64 Duo core +6000, Nvidia 9600 GT.

Here is the Error I recieve in terminal

[email]fock@fock-blackbox:~/.wine[/email]/drive_c/Program_Files/World_of_Warcraft$ wine "WoW.exe"
Segmentation fault
[email]fock@fock-blackbox:~/.wine[/email]/drive_c/Program_Files/World_of_Warcraft$

---

### Post by aoanla on 2008-08-01
> **faceonkeyboard said:**
> I'm on the verge of killing myself. I need help so desperately I would pay someone 100 dollars, seriously! To help me get WoW+Ubuntu 8.0.464bit+Wine 1.1.2.

Im super new to Ubuntu, maybe a week old.  However im not new to computers, so its easy to read and learn for myself. However im not sure if Im missing a step or what but im following the offical Ubuntu guide on getting WoW setup and running but... big but...

I copied all the disc's to the way in the guide, I launch the install, but here is where I get confused becuase I don't understand Ubuntu's insane directory structure. I leave the default's C:\program files\world of warcraft is that ok? I thought ubuntu or linux could not read spaces.  So much contradictory and stuff, im sooo lost.

The linux shell is fine with spaces, but you need tell it that you mean the spaces to be part of a filename, and not indicate a gap between arguments. Normally, you either quote the argument, or you can "escape" the spaces with backslashes.
In anycase, this isn't your problem - the installer thinks that it's running in Windows, and Wine knows how to handle Windowsish paths with spaces.

> 
I have the base OS and video card drivers installed and updated.  I just need help installing wow into the file structure and then launching.


Which nVidia drivers did you install?
If you type
glxinfo | grep -i render

do you get a yes?


> 
System spec's:
AMD64 Duo core +6000, Nvidia 9600 GT.

Here is the Error I recieve in terminal

[email]fock@fock-blackbox:~/.wine[/email]/drive_c/Program_Files/World_of_Warcraft$ wine "WoW.exe"
Segmentation fault
[email]fock@fock-blackbox:~/.wine[/email]/drive_c/Program_Files/World_of_Warcraft$

This:
[http://dedors.wordpress.com/2008/07/29/howto-world-of-warcraft-wrath-of-the-lich-king-wow-wotlk-beta-running-on-wine/](http://dedors.wordpress.com/2008/07/29/howto-world-of-warcraft-wrath-of-the-lich-king-wow-wotlk-beta-running-on-wine/)
suggests that immediate segmentation faults on trying to run WoW in Wine are possibly related to iffy graphics driver installs.

---

