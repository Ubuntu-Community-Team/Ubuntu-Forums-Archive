---
title: "Warcraft III Frozen Throne - Terribly Slow!"
date: 2008-05-18
forum: Wine
---

### Post by fluxy on 2008-05-18
Hello.
I've Ubuntu Hardy with wine 0.9.59 installed. I'm try to run Warcraft III Frozen throne using it - it works and the game itself loads and all but it is terribly sluggish(even with -opengl or -window), with the cursor barely moving (despite a new game being able to load). 

I've an oldish laptop with integrated intel graphics, but Warcraft III Frozen Throne used to run pretty well on Windows. So could there be a way I to cure this sluggishness please? Thanks

---

### Post by benzyl_chloride on 2008-06-25
Mine is doing the exact same thing. I've just been tinkering around with it. Nothing so far has had any effect. It ran perfectly back when I had Windows so I'm pretty sure it's not a hardware problem. If I get mine working, I'll post how to fix. By the way, how old is your laptop?

---

### Post by amba on 2008-06-25
I play on ROC, it runs fine.
Latest wine in repos, 
```

:~$ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.59

```
using -opengl option.
I've only the bad bug which doesn't allow me to host games *sigh*

---

### Post by fluxy on 2008-06-25
> **benzyl_chloride said:**
> Mine is doing the exact same thing. I've just been tinkering around with it. Nothing so far has had any effect. It ran perfectly back when I had Windows so I'm pretty sure it's not a hardware problem. If I get mine working, I'll post how to fix. By the way, how old is your laptop?
Well it's a single-core AMD Acer Aspire 3000 with shared graphics memory. I've noticed that OpenGL runs very poorly on it which may explain why Warcraft 3 on wine (and other OpenGL games) don't work well...

Solution (for now): I've (re-)installed windows xp to play my games.

---

### Post by B61zz13 on 2008-06-26
Have you guys tried this?

REGEDIT4

[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
"Gfx OpenGL"=dword:00000001

---

### Post by shae on 2008-06-27
> **amba said:**
> I play on ROC, it runs fine.
Latest wine in repos, 
```

:~$ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.59

```
using -opengl option.
I've only the bad bug which doesn't allow me to host games *sigh*

Try out my wine PPA patched for use with warcraft 3.  It supports Hardy and Gutsy!  Also I have snoopy, a program that pings and custom kicks when hosting.

---

### Post by Hairy_Palms on 2008-06-27
well what i do is have two versions of wine installed, i run wc3 TFT with wine 0.9.46, every version since has made it worse for me, but i have wine version 1.0 for eveeything else. 0.9.46 is installed to /usr/local
oh and i can host games too.

---

### Post by Tapas Pain on 2008-10-12
Hello - I have Warcraft TFT on Hardy.  At first I used the -opengl and -window switch - gameplay was slow and awkward (like what you have described above).  I found deleting the -window switch and keeping the -opengl switch only greatly improved the speed of gameplay.  It's not perfect, but it's liveable.  Hope this helps you.

Cheers.

---

### Post by Tapas Pain on 2009-06-15
Gentlemen - I don't know if you have all lost interest in this thread, but I thought I would share some recent insight with you.  I had some Warcraft TFT "slow" problems.  Shortly after my last post, my computer died.  I dusted off an old computer from my basement, re-installed Ubuntu, and of course installed TFT.  It runs as fast or faster than when I had it on that *other* operating system.  Why?  I think it's the graphics card - even the introduction screen comes out with much more vibrant colours and graphics than ever before.  I've been comparing it side-by-side with my Microsoft PC laptop, and Ubuntu is really rocking it.  So, if you're copy is running slow, my humble suggestion is, look into your graphics card.  Cheers, and happy killing.  My blade thirsts.

---

### Post by Arceux on 2009-10-03
If you run it in a terminal and type "-opengl" after the directory it should work just fine.

---

### Post by bcboybuzz on 2010-01-27
> **B61zz13 said:**
> Have you guys tried this?

REGEDIT4

[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
"Gfx OpenGL"=dword:00000001


Worked for me. FPS was so bad I could barely navigate the menu at 800x600 all settings low or off. After modding registry, FPS was great at 1280x1024 all settings high.

Note: couldn't test -opengl switch, since I'm using PlayOnLinux and can't figure out how to mod the command to start the program...

Cheers

---

### Post by R.tz on 2010-02-03
I managed to get to [HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
but I can`t find : "Gfx OpenGL"=dword:00000001

Any indications?

---

### Post by vaab on 2010-08-01
I played a lot war3 on my computer under wine some years a go. Now on the same computer, I have sluggish results (I'm on wine 1.2)... No idea why this is really worse now (menu naviguation is painfull).

Several other games are really slow (aquaria) and I had to use LIBGL_ALWAYS_INDIRECT=1 to run aquaria at playable speed. This option seem to force software rendering and do not work for warcraft.

I guess my issue might not be wine fault but I suspect opengl intel drivers. I'm digging into this.

---

### Post by pressko on 2011-05-23
I have the same problem. When i start playing fps is pretty good , some like 90-100 fps.  But after 5 minutes it's dropping it to 20 -30 fps :( I'm running WC3 with -opengl mode. My machine is with Ubuntu 11.04 and Nvidia 9500m GS.

Also i got those errors : 

presian@presian-Aspire-6920:~$ wine war3.exe
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f300,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f60c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x146958,0x1468a0): stub

---

### Post by Krajanoff on 2011-08-14
Hello I know this is old thread but I install today Lubuntu and want play W3 and it was laggy but advice from B61zz13 solve it.

@R.tz I create in register dword and name it "Gfx OpenGL" and data I set to "00000001" and it was work for me.

I hope it would helped somebody.

---

### Post by Mahdi D on 2012-09-03
> **B61zz13 said:**
> Have you guys tried this?

REGEDIT4

[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
"Gfx OpenGL"=dword:00000001

Thank you very much! it worked for me!

> **R.tz said:**
> I managed to get to [HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
but I can`t find : "Gfx OpenGL"=dword:00000001

Any indications?

I created it myself... a DWORD named " Gfx OpenGL " and  value " 1 "

---

