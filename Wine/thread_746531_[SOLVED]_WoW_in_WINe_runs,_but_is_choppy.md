---
title: "[SOLVED] WoW in WINe runs, but is choppy"
date: 2008-04-05
forum: Wine
---

### Post by kc5hwb on 2008-04-05
I got WoW and BC installed last night and everything seems to work fine, but the frame-rate seems off.  When I move the mouse around, it kinda pages and when I run it is choppy.  Is this a setting in WoW?  or a setting somewhere in WINE?

---

### Post by rigol on 2008-04-06
Did you already try the tipps and tricks mentioned here: [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) ?
In case you did, what exactly did you try? What are your graphics card, system specs, settings and so on?

I was always able to play WoW without choppy graphics with Nvidia 7600GT, AMD X2 3800 and 1GB RAM.

---

### Post by kc5hwb on 2008-04-06
Thanks for that link, I hadn't seen that before.  I will go through today and try some of those tips.

My board is an AMD 64 (Iforget the # on it, but I can look it up later) 2.4GHz with 2GB of ram.

My video card is a GeForce 6100 nForce 405

---

### Post by kc5hwb on 2008-04-07
I ran the Registry Tweak for FPS Boost originally because it was listed in the ubuntuforums post where I got the info on how to install WoW.
This link:  [http://ubuntuforums.org/showthread.php?t=579378&highlight=wow](http://ubuntuforums.org/showthread.php?t=579378&highlight=wow)


This is the motherboard I am using:
[http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332](http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332)

---

### Post by kc5hwb on 2008-04-08
My choppy performance was fixed by adding this to the config.WTF file:

```
SET ffxDeath "0"
SET ffxGlow "0"
```

Thanks to everyone for their help

---

