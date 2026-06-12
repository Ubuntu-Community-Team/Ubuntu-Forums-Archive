---
title: "Team Fortress 2 doesn't load maps"
date: 2007-12-18
forum: Wine
---

### Post by chumchum on 2007-12-18
Hello all
I am using Feisty with dual boot with Windows XP. I can run most games very well on windows but not on Ubuntu, everything installed fine (via download, not disc) and I'm using Wine version: 0.9.33-0ubuntu1 all seems well until I finally try to join a game, or start one or play in anyway what so ever, it loads, but JUST before it launches, like 1 progress bar division away, it just won't load anymore, and the HDD activity L.E.D dies too. I also have HORRIBLY poor perfomrance on CSS (Kinda off topic, sorry :() and have roughly 4fps on stress test and with all on minimum settings I have an improvement to...13 fps -.-'. Yet on Windows all is well :S I have a ATI radeon X1650 using drivers installed through Envy (I try to use as many automatic installers, since I'm still new to Ubuntu and have to do stuff like that orscript kiddie style, moronicly copying and pasting ;), though am learning...slowly

---

### Post by The Noble on 2007-12-18
You are using a pretty old version of wine that will not have all of the recent improvements in graphics that recently been added. There are two ways to get the latest wine version:

1. Put this command into your web browser:

```

http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb

```

It is the latest version from their official repositories, so it is a legit binary. Double click the file to install it.

2. Follow the guide on their main site to add the repositories. This will auto update wine, which is both good and bad. Some version have some problems with games, so if you find that the latest version works perfectly, turn off the repository or follow option 1 to make sure your game install doesn't get borked.

---

### Post by chumchum on 2007-12-19
Well I now have version: 0.9.50~winehq0~ubuntu~7.04-1 but it still won't work, all loads, I hear the music I see the Valve logo, source logo but when I finally come to the main menu, I just have a black screen, but it's still playing music :S.
Any ideas?

---

### Post by aoanla on 2007-12-20
Before you launch Team Fortress 2 from Steam, use the Properties button to set the Launch Options to

-dxlevel 81 -heapsize 512000

This should fix your problem (which is an issue with DX9 shaders).

---

### Post by chumchum on 2007-12-20
Didn't work :(
Is it realy a shader problem if it didn't even draw the options menu after updating wine? :S

---

### Post by upbeat.linux on 2007-12-20
In your wine config make sure that Windows emulation mode is set to XP.

---

### Post by chumchum on 2007-12-20
Done... still won't work, at least I won't get booring Windows 2000 themed windows, thanks for that, but TF2 still won't work :(

---

### Post by wretchedmage on 2007-12-20
does anyone else have a problem trying to connect to for the past 2 days?

[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb)

---

### Post by Tadock on 2007-12-20
There are a few tweaks to boost FPS in games. One of which is running the games in OpenGL to start the game in opengl simply add -opengl at the end.
I.E. wine /Where.ever.game.is/game -opengl

I hope this helps. I don't think I can help you much with your other problems.

---

### Post by SoulSmasher on 2008-02-04
i'm using wine .9.5.4 and same here, too :(

(btw i'm using mobility radeon x1300, drivers updated with envy)

will try adding -opengl to end and post result again..

edit: same again :(

anyone managed to fix this issue?
thanks..

---

### Post by SoulSmasher on 2008-02-04
okay i managed, now it opens :D

i added this option to shotcut at the end of launcher

-dxlevel 81 -heapsize 1512000

1512000, because ive 2 gigs of ram on my machine,

it's a bit laggy, but works at last, maybe it'd be more better if we add -opengl command also,  :) thanks aoanla & tadock :)

---

### Post by aoanla on 2008-02-05
Unfortunately, -opengl doesn't do anything with Source engine games, at present (they don't have an OpenGL render path, so they just silently ignore the option).

When you say "laggy", do you mean that you're getting low frame rates? Have you tried playing with the graphics settings - turning off or down some options (especially advanced features) might help.

---

### Post by SoulSmasher on 2008-02-05
within laggy, i was meaning low frames yup,
ok, thanks, i lowered the shader and detals, now it works fine.. except one thing..

after most 10 minutes, game crashes down, i mean freezes inside game, cannot change desktop, or kill app. laptop's power button is only solution..

t's even worse when i delete heapsize option. as soon as game opens, it freezes..

do i have to keep low the heapsize ?

by the way, i'm using this registry data on my wine..
```
REGEDIT4



[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"OffScreenRenderingMode"="fbo"

"PixelShaderMode"="Enabled"

"UseGLSL"="Enabled"

"VideoMemorySize"="134217728"

```

(i got these options from an other thread, not sure if i typed videomemorysize right though (does it have to be in bytes or kbytes like heapsize?) )

thanks for any avices :)

---

