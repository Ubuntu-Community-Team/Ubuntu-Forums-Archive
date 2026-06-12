---
title: "COD4 on Wine 0.9.57"
date: 2008-03-08
forum: Wine
---

### Post by Chriis on 2008-03-08
When i run cod4 .exe file on wine.

in terminal: 
---------------------------------------------------
chris@commando:/media/sdb1/Games/CallofDuty4$ wine w3mp.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f93c,0x00000000), stub!
-----------------------------

and on screen:
----------------------------------------------------
Error during initialisation:
Video card or drivers doesn't support enough textures for DirectX 9
code path.
-----------------------------------

And when i OK the box, it exit to the desktop

I can play Cod4 on this machine with WinXP 

Any Idea?:confused:

------------------------
7800gt 
NVIDIA Driver Version:169.09
-----------------
Thanks Chriis

---

### Post by Larrxi on 2008-03-08
Did you patched Wine with the needed patch to get Cod4 working?

Did it worked for you on Wine 0.9.56?

I got Cod4 working with Wine 0.9.55, 7800GT and the patch.

---

### Post by Chriis on 2008-03-08
No I did not patch wine, 

I never get it worked , first time try

BTW what is this patch and what it does to wine exactly

Chriis

---

### Post by piratesmack on 2008-03-08
I made a .deb package for wine 0.9.57 witht the alpha glow patch here guys:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

enjoy

---

### Post by Chriis on 2008-03-08
sry but i forget to say  i' m on arch64 :roll:

why "alpha glow patch" is needed and why it is not native in wine?

Thanks 
Chriis

---

### Post by Sockerdrickan on 2008-03-08
> **piratesmack said:**
> I made a .deb package for wine 0.9.57 witht the alpha glow patch here guys:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

enjoy

omfg thanks I'll try it

---

### Post by guyx666 on 2008-03-08
> **piratesmack said:**
> I made a .deb package for wine 0.9.57 witht the alpha glow patch here guys:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

enjoy

wow tanxs it works for me. 
good job...
i hope you gonna continue to make .deb package to each version of wine.
i have try to make it my self but with no luck.
your file did the job right.
you're a half-god !!!
Now i can Play Call of duty 4 modern warfare single player on UBUNTU :)

---

### Post by Chriis on 2008-03-08
Anybody can make a .deb for arch64? or help me to do one plz??

:guitar:

---

### Post by piratesmack on 2008-03-08
> **guyx666 said:**
> wow tanxs it works for me. 
good job...
i hope you gonna continue to make .deb package to each version of wine.
i have try to make it my self but with no luck.
your file did the job right.
you're a half-god !!!
Now i can Play Call of duty 4 modern warfare single player on UBUNTU :)

Thanks
yeah I've been making debian packages for wine with the alpha glow patch since like version 0.9.55. Just keep an eye on my filefront account, I'll definitely upload more. 

Oh and also, you can play multiplayer on non-punkbuster servers

---

### Post by Chriis on 2008-03-08
> **piratesmack said:**
> Thanks
yeah I've been making debian packages for wine with the alpha glow patch since like version 0.9.55. Just keep an eye on my filefront account, I'll definitely upload more. 

Oh and also, you can play multiplayer on non-punkbuster servers

Can you help me to make one for 64bits ubuntu user too?

BTW this post was to seek help for patching a 64bits wine not 32.

---

### Post by Google Spider on 2008-03-09
> **piratesmack said:**
> I made a .deb package for wine 0.9.57 witht the alpha glow patch here guys:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

enjoy

Thanks. 
**[COLOR="Blue"]Reputation++[/COLOR]**:KS

---

### Post by ahaslam on 2008-03-09
I sometimes wonder why I bother....
[http://ubuntuforums.org/showpost.php?p=4047498&postcount=13](http://ubuntuforums.org/showpost.php?p=4047498&postcount=13)

---

### Post by Chriis on 2008-03-09
> **ahaslam said:**
> I sometimes wonder why I bother....


Just missed it.
i'm alone? Was here to seek help, not be,.. anyway is it permited to hijak a thread? if so,..i'll go do the same

---

### Post by piratesmack on 2008-03-09
> **Chriis said:**
> Can you help me to make one for 64bits ubuntu user too?

BTW this post was to seek help for patching a 64bits wine not 32.

Try this to install it on 64 bit:
-Save the debian package to your desktop
-open a terminal and run the command:
cd Desktop
(press enter)
sudo dpkg --force-architecture -i wine_0.9.57-1_i386.deb

---

### Post by thefishki345 on 2008-04-18
hi piratesmack
I am using 64 bit, and tried 
cd Desktop
(press enter)
sudo dpkg --force-architecture -i wine_0.9.57-1_i386.deb 

it worked, installed a folder and everything, but when I try and launch cod4/css/ other wine apps, nothing happens, so maybe it hasnt installed or something, please help me!

---

### Post by spacholka on 2008-06-24
Worked for me!! I'm on Ubuntu 8.04. Been pulling my hair out for weeks trying to get this to work. Came here, downloaded the .deb, forced 64bit and voila. It works!

I OWE YOU A COKE!

---

