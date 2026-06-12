---
title: "Running World of warcraft on Ubuntu using Wine (but it doesn't work)"
date: 2007-04-13
forum: Wine
---

### Post by MarchelV on 2007-04-13
Hello.

I am quite new to the Linux environment so my problem might be solved quite easy (don't yell at me if I ask completely noob questions) :)

Anyway, my problem:
I installed Ubuntu on a PC (800Mhz, 768Mb mem, Radeon9200SE videocard) and want to run World of Warcraft on it (by using Windows2000 it works with the setup)
I installed "wine" as described in "https://help.ubuntu.com/community/WorldofWarcraft", when I run WoW the game starts but stays in the background, the desktop becomes a few shades lighter but nothing else happens. I cannot Alt-Tab to the game but all other applications are accessible by using Alt-Tab.

As said before, I am a complete noob so if you know the answer don't immediately talk binary to me ok :)


Cheers!
Marchel.

---

### Post by x64Jimbo on 2007-04-13
Have you tried it in Windows XP compatibility mode?

---

### Post by MarchelV on 2007-04-13
What binary language are you speaking my friend?

Lol, I think I can guess where I can set that (winecfg isn't it?). I'll give it a try tomorrowmorning and let you know the result.

Thanks!
Marchel.

---

### Post by jordman2001 on 2007-04-14
If u want you can try running it with opengl

> wine wow.exe -opengl

---

### Post by Big_Rog on 2007-04-19
I'm in a similar boat, except that I have wow swimming along nicely in OpenGL (fullscreen, same rez as desktop) and can't alt-tab out.  I can get the list to pop over, scroll through the running windows, but when selecting anything other than WoW, it shows the border of the window then goes right back to the WoW screen.  The suggestions I've seen on some other forums is to try toggling vsync.  I can't find anything other than Sync to VBlank on the XVideo settings section.  I'm using version 1.0-9746 on a NF4 motherboard, athlon64 cpu, and a 7600 nVidia graphics card.

Thanks in advance for your suggestions!

---

### Post by Venoseth on 2007-12-31
Big_Rog, as a workaround for your problem, have you tried setting or using keyboard shortcuts to access another panel (workspace)? If you could do that (I have mine set to shift+F1 for workspace 1 and shift+F2 for workspace 2) without any trouble it's as easy as just keeping WoW in one workspace (definitely don't ever set it to be active in all workspaces XD). At least, until you get a more astute answer. XD

---

### Post by OOOPPPs on 2007-12-31
I had the same problem when i tried to set up WoW,

You gotta add an option something like "SET M2UseShaders "0"" in your Config.wtf

also gotta disable some of the death glow options .

---

### Post by TolTime on 2007-12-31
> **OOOPPPs said:**
> I had the same problem when i tried to set up WoW,

You gotta add an option something like "SET M2UseShaders "0"" in your Config.wtf

also gotta disable some of the death glow options .

you said something like "SET M2UseShader "0" 
is that it or what else would it be

and how do you disable the death glow options?

---

