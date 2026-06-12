---
title: "Portal"
date: 2007-11-26
forum: Wine
---

### Post by adamweyant on 2007-11-26
Hi. I have a small problem that I've been goolgeing for about an hour now and I've been getting no where. This is what's happening.
I downloaded Portal. To start it up from the portal directory I use the command:

```
wine hl2.exe -steam -game portal

```

The game starts, the video of the guy with the valve plays, and the loading screen comes up. Right after it's done loading, before it shows the menu, everything crashes and I get the following error in the terminal:

```
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x158f90) : Only 1 render targets are supported.
Mesa 7.0.1 implementation error: i915_program_error: Exceeded max nr indirect texture lookups

```

I tried running the game using -dxlevel 80. This didn't help.

I have a Intel 945GM integrated graphics card (I know it's weak, don't tell me about it), which reportedly doesn't like OpenGl, so maybe if I knew the switch to start the game with direct3d, that would work? If not, anyone have any ideas? Thanks.

---

### Post by adamweyant on 2007-11-26
Update: It just crashed one more time sending x into 640x480 mode. I can't change this in Screens and Graphics anymore. The only option is 640x480. How can I get the other options back? (Was 1280x800)

---

### Post by MickLionheart on 2007-11-26
To get your resolution back try "xrandr -s 0" in terminal and if that doesn't work, then try typing just "xrandr" back into the screen.

Also, do you have any other source based games, such as Half Life 2 or Counter-Strike:Source, if so, test them and post your results.

Finally, try upgrading your version of wine to the one from [winehq.org]("http://winehq.org"), I used to get that crash but when I upgraded wine all just instantly started working.

(Also, sorry about this but... w00t! 1st Post) (No really, this is my first post in the Ubuntu forums)

---

### Post by adamweyant on 2007-11-27
I got the normal resolution back. But I have the newest version of wine already 0.9.49. And, I don't have any other source games that I can try at the moment.

---

### Post by MickLionheart on 2007-11-28
Do you have anything installed in wine other than portal, and also, do you use steam?

You might want to try making a new wine prefix, because source based games tend to be very unstable under wine, where a DLL off by one version can stop them from starting up.

Also, do you use desktop effects (or plain beryl of compiz/-fusion)
What version of ubuntu do you use.
And do you have GLSL enabled in winecfg.

---

### Post by phun-ky on 2008-01-14
i am trying to run World of Warcraft on my ubuntu install on my d620. originally (with no tweaks that is), i get crap fps, but the game works. after a tweak guide recommended by some fellow guildie, i get this error aswell:

Mesa 7.0.1 implementation error: i915_program_error: Exceeded max nr indirect texture lookups

the only thin that's changed is  a key under "HKEY_CURRENT_USER/Wine" named Direct3D witha string name: UseGLSL and "enabled".

anyone have an idea? i have compiz switched off, i use ubuntu gutsy (7.10)

---

