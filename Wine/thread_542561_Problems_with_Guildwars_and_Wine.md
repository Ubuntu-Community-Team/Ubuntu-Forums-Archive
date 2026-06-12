---
title: "Problems with Guildwars and Wine"
date: 2007-09-04
forum: Wine
---

### Post by gavinjb on 2007-09-04
Hi,

I have just installed Guildwars under Wine and all seemed to go ok, I have't had the problem with no mouse, like then I tried to install peviously, but I have encountered a couple other issues, not sure if anyone has any ideas.

1. The FPS is at 6 (much too slow), I am running Xgl with Compiz, bu I cant think of any reason why this could be the cause of the slow FPS

2. The Game was in the process of downloading (after logon and selection to play with character), and it suddenly just crashed, or at least the game window vanished

3. After this happening Guildwars wont startup again (I have run wine Gw.exe -dx8), and if I click on the desktop icon X just restarts

Can anyone help.


Thanks,


Gavin,

---

### Post by MonkeyBoy on 2007-09-04
XGL can mess badly with games presumably because of the resources required.  I reckon you should switch back to regular Gnome and see if your fps improves.  I seem to get an average of about 15-30 fps which, while not great, is at least playable.

I run the following arguaments:
```
-dsound -noshaders -dx8 flags -repair -image
```
I don't know if they are all strictly required but it seems to work for me.

Good luck.  And if you get it working join my guild.:)

---

### Post by gavinjb on 2007-09-04
Thanks, 

That has at least sorted the FPS (or better at any rate 15-20), but now I have another issue

When GuildWars open everything is ok, but then after a few seconds the mouse pointer vanishes and nothing seems to be able to get it back (I have tried the right click I have heard about).

In the end I do Alt+F2 xkill on guildwars, and then for some reason if I try to start GuildWars again it hangs on the update screen and the main logon screen never loads again (or not until I reboot anyway)



Gavin,

---

### Post by Ferrat on 2007-09-04
You can try ALT + ENTER when the pointer goes, can help, or try looking down in to the ground if in game and klick some more. 

if you can't restart it prolly it's cause you have a ghost, open the system monitor and see if you can find it

---

### Post by gavinjb on 2007-09-04
Thanks,

I found a script on this forum, to install Wine and Guildwars, and it seems to have solved most of my problems except I have no sound, any ideas

The link to the Script is here [http://ubuntuforums.org/showthread.php?t=283122&highlight=guildwars](http://ubuntuforums.org/showthread.php?t=283122&highlight=guildwars)

Thanks,


Gavin,

---

### Post by Ferrat on 2007-09-04
> **gavinjb said:**
> Thanks,

I found a script on this forum, to install Wine and Guildwars, and it seems to have solved most of my problems except I have no sound, any ideas

The link to the Script is here [http://ubuntuforums.org/showthread.php?t=283122&highlight=guildwars](http://ubuntuforums.org/showthread.php?t=283122&highlight=guildwars)

Thanks,


Gavin,

[http://ubuntuforums.org/showpost.php?p=3301605&postcount=659](http://ubuntuforums.org/showpost.php?p=3301605&postcount=659)

---

### Post by gavinjb on 2007-09-05
Thanks,

I have now applied the settings, but when I start GuildWars still no sound on the Intro Screen.

I have also noticed that when I goto the Options Screen and click on Sound, that the Use 3D Audio Hardware option is greyout, even though in the topic it mentions ticking this.

Also when I first ran Winecfg and went to Audio the 3 Drivers at the top were all deselected (EsounD Driver, OSS Driver & NAS Driver), I have currently ticket them all.


Thanks,



Gavin,

---

### Post by Ferrat on 2007-09-05
> **gavinjb said:**
> Thanks,

I have now applied the settings, but when I start GuildWars still no sound on the Intro Screen.

I have also noticed that when I goto the Options Screen and click on Sound, that the Use 3D Audio Hardware option is greyout, even though in the topic it mentions ticking this.

Also when I first ran Winecfg and went to Audio the 3 Drivers at the top were all deselected (EsounD Driver, OSS Driver & NAS Driver), I have currently ticket them all.


Thanks,



Gavin,

Try just checking the OSS

---

### Post by gavinjb on 2007-09-05
Thanks,

But it made no difference, this is strange, if I install wine through the repo, then I get slow FPS but sound, I install through the GuildWars + Wine install script and I get much better FPS (definately playable with ATI Card), but no sound.

Gavin,

---

