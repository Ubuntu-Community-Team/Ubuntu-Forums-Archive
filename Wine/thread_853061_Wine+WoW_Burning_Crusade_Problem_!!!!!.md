---
title: "Wine+WoW Burning Crusade Problem !!!!!"
date: 2008-07-08
forum: Wine
---

### Post by daniel7860 on 2008-07-08
When i start the game only the areas where you have buttons show. for example when i choose a character only the stuff on the sides shows but where the character is supposed to be, that whole space is black. 

plus it registers my mouse clicks very bad, i have to click and hold it for over 5seconds maybe for it to select.

---

### Post by daniel7860 on 2008-07-08
oh and i am using: ATI Mobility Radeon X300
Direct rendering: Yes
Restricted Driver: Not Enabled

---

### Post by daniel7860 on 2008-07-08
weird.........now when i launch the game my whole screen just turns "HOT PINK" and alt-f4 doesnt work not even  ctrl-alt-backspace,
all i can do iss hold my power button for 6 seconds to turn off my pc.:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by daniel7860 on 2008-07-08
well i got the pink screen fixed,  enabled the wrong audio drivers:)

---

### Post by jerome1232 on 2008-07-08
Glad to see you got it fixed, editing your config.wtf file to have
```
SET gxApi "opengl"
``` may help with the slowness (i get pink screens with out this set)

---

### Post by daniel7860 on 2008-07-08
i still have my major problem with the game, almost everything is black and when i finally start the game it exits.

---

### Post by piousp on 2008-07-08
Try setting this on your config.wtf

```
SET M2UseShaders "0"

```

That will hopefully fix your bacl screen problem.

Now, for the crashing bug, here is one solution:

Edit your /etc/X11/xorg.config, and add this into your "Device" section:

```

Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"

```

Also, you may want to check out [this]("http://www.wowwiki.com/Linux/Wine/Troubleshooting") site

---

### Post by daniel7860 on 2008-07-08
now i get an upside down portal  and it it very very very incredibly slow.
:confused:

---

### Post by piousp on 2008-07-08
Can you post a screenshot?

---

### Post by daniel7860 on 2008-07-08
here

---

### Post by thisismalhotra on 2008-07-08
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

All Black

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by daniel7860 on 2008-07-08
ok i got the upside down portal fixed by adding this to the end of config.wtf

SET ffxDeath "0"
SET ffxGlow "0"

but it is still super slow, its like the whole thing is frozen, then every 30 seconds or so, it changes. so if i click something i have to wait very long for it to change.

---

### Post by daniel7860 on 2008-07-08
:confused: :confused: :( im stuck

---

### Post by aliayaz on 2008-07-08
Well you just said the problem Restricted driver isn't Enabled did you try enabling it ?

---

### Post by thisismalhotra on 2008-07-09
Did you do the registry edit??

---

### Post by piousp on 2008-07-09
Try erasing your config.wtf and the play wow for a couple of minutes. It will create a default config.wtf. After that, start modifying it.
Also, remember to add the registry fix.

---

### Post by daniel7860 on 2008-07-09
no enabeling the restricted drivers will not do it,

yes i did the registry thing.

---

### Post by daniel7860 on 2008-07-09
ok piousp, i deleted the config.wtf 
but now when i start the game, after i click to accept the terms of use, the music keeps going but the whole thing just freezes and all i can do is shut down  my computer by holding the power button for a long time. :mad: :mad: :mad: :mad: :mad: :confused:

---

### Post by daniel7860 on 2008-07-10
so this thread seems pretty much dead.....i guess ill delete that game, its still using 8GB  on my 60GB drive.  :-({|=

---

### Post by merlyn on 2008-07-10
Hi,

I have WoW BC working perfectly on my system, and all I needed to do was follow the guide from [this thread]("http://ubuntuforums.org/showthread.php?t=579378").

This is about all the advice that I can offer as I did not experience any of the technical issues that you have.

However, there are lots of useful tips throughout the thread, to help overcome all sorts of problems.

Hopefully you'll find a solution there.

Cheers.

---

### Post by Anatashinu on 2008-08-13
I'm having the exact same problem. Whenever I click the game freezes =(
HEEELP

---

### Post by Anatashinu on 2008-08-13
I Solved it! I Solved It!!!
It's because we use WoWscape. Stupid WoWScape... :)

The Solution:

Have your realmlist in config.wtf be the same as in realmlist.wtf

---

### Post by thumper13 on 2008-08-19
TO THE OP:

I have installed Warcrack on my ubuntu install about 40 times now, i've learned a thing or two... the links provided in this thread will make a functional working wow, provided you do exactly as they say.

One thing i will note, is that one of the pages has a config.wtf file attached to it you can download and insert into your WoW install. It's basically a default config.wtf, with some extras added for running it in linux.

Also, there is an addon called ApplyToForehead on one of the posts linked in this thread. (you can also get it from wowinterface.com i THINK. i've seen it around a few times, i just get it from the posts)

Another tidbit i'd like to add is that the x series ati cards (i know, i have x200 in my machine) are not the greatest cards for linux + gaming. If you have the money, i'd think about investing in almost any nvidia card. My other pc, which is 2 years older than my good one, runs wow a lot better, and i believe it is only the nvidia card thats different, i have a geforce 5200 in it, whereas this is the x200. 

Oh, and also check your wine configuration to check for which audio drivers it uses (Alsa, OSS, etc.)... i had a problem once, somehow 2 of them got checked off, and the computer got confused. My machine runs it in alsa, or oss, but not both at once.

I hope this helps a bit... Just know that it IS possible to run warcraft perfectly clean. (in fact, my pc runs it better in any Linux distro than any version of Windows, I tried xp and vista, as well as Debian, Ubuntu, and OpenSUSE. i get +10-15 fps in linux)

Thumper,
Thumperox of Thunderlord, Rexxar or Blackrock.

---

### Post by piousp on 2008-08-19
I know its kinda late now, but in a last attempt to fix your problem, i can give you my config.wtf file, so you can try it out.

---

