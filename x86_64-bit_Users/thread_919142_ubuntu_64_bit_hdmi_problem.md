---
title: "ubuntu 64 bit hdmi problem"
date: 2008-09-13
forum: x86 64-bit Users
---

### Post by tommegunns on 2008-09-13
Hello all, first off i am as green as it gets when it comes to linux. I have a better than average understanding of computers and am or was very knowledgeable about windows. I am making the switch to linux, because it is free and seems to be the way of the future. Well i just installed ubuntu 64 bit, fairly easily. I have a 8600gt which i run two monitors on (a princeton 17" and a 27" flat panel hdtv via hdmi). After installation completed i restarted and my crt (analog) worked fine but my hdtv has only a center strip which is surrounded by black on top and bottom with the desktop in the very center and continually rotating. It sort of looks like a very small widescreen desktop. My first thought was to find some drivers from nvidia to remedy this, well the drivers do not install, so second i turned off and unplugged the crt 17" and kept the hdtv plugged in but (and i even swapped slots also) when restarted still same picture. So this leads me to believe that it is probably a hdmi problem since dvi and analog (vga) seems to work just fine. If anybody can help, it will be greatly appreciated. i really do not want to go back to windows and without my 27", that unfortunately what i will have to do. Thank you.

---

### Post by soxs on 2008-09-14
Good news: It's not hdmi related (at lesat I don't think so), it's related to your grpahics driver being malconfigured (or not yet being installed correctly), in fact /etc/X11/xorg.conf is malconfigured / not configured and thus the driver will  detect the hdmi tv as generic TV and adds oversan black borders to it plus some other nasty things.

Bad news: I am an ATI/AMD user from the beginning and I have no clue what options your xorg.conf requires to be set to make it detect hdmi as hdmi and not as generic TV "gadget"

---

### Post by StormPCs on 2008-09-14
I use an AMD Phenom 9850 and an nVidia 8600GTS.  How did you install the driver?  If you just clicked enable in System> Administration> Hardware Drivers you will not get the NVIDIA X Server Settings GUI console.  You need to install EnvyNG and reinstall the latest drivers through Envy.

In the NVIDIA X Server Settings console you will find all the options to make the HDMI work properly.  Cheers.

---

### Post by lronclawbigun on 2008-09-15
Now today we discuss the game of warhammer online. Warhammer online is the full name of this game ,warhammer always abbreviation of war ,so [warhammer power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) often called war power leveling, and in fact. All war power leveling , [war power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling), [warhammer online power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) is the same meaning ,so here not to puzzle with this.firstly ,when you want  [Warhammer cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey),i suggest you go to gamevive.com. They sell the lowest price for warhammer gold and other [warhammer online cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey) .and their delivery  is fastest.it is worth to try.

---

### Post by tribaal on 2008-09-15
I just set up HDMI on my own set up this weekend.
While I have a different graphics card it should work the same way (since it's an nVidia too).

Here's how you d (on top of my head, I'm at work):
- Install the latest driver, using envyNG preferably.
- Run nvidia-settings as root. most of the problems with this happend when you don't run the program as root (you can't write an xorg.conf when you're not root). Easy enough: "gksudo /usr/bin/nvidia-settings" in a terminal will fix this.
- Go to "Xserver display Configuration (the second item in the menu).
- You should see you HDMI screen reported as "Disabled". Click it.
- Choose "Configure..."
- You have two options: using twinview (one and only desktop spread on both of your screens), or a separate X port (my favorite).
- Once you chose your poison, click "Save to X configuration file" (that's where the root credentials is important).
- Restart your X session (logout, or press ctrl-alt-backspace).
- That should work :)

Remember that unfotunately since the graphics card does not process sound (it's not designed to), you won't have sound with your HDMI output. :(

Hope this helps!

- Trib'

---

### Post by soxs on 2008-09-15
> **tribaal said:**
> 
Remember that unfotunately since the graphics card does not process sound (it's not designed to), you won't have sound with your HDMI output. :(

Is there really no way getting hdmi to give me sound via my graphics adapter?

---

### Post by tribaal on 2008-09-15
Nope, unfortunately not (as far as I know).
It's quite logical when you think about it really, your graphics card does not process sound.

What I did is run a synch cable from my laptop, plus the HDMI, to my TV/home cinema amplifier.
It's not that bad, but it means that you have no surround (which is fine with me), and that you need a second cable running between both systems.

Maybe I'm wrong on the sound output, but I would be quite amazed if it was possible. Does anybody know if such a setup would include sound on, say, a windows system? I don't have a windows machine, so I can't test it myself.

Cheers

- Trib'

---

### Post by philinux on 2008-09-15
[http://www.engadget.com/2007/03/20/nvidia-shows-off-new-mid-range-8300-8500gt-and-8600gt-dx10-gra/](http://www.engadget.com/2007/03/20/nvidia-shows-off-new-mid-range-8300-8500gt-and-8600gt-dx10-gra/)

```
All feature HDCP supported HDMI ports (with sound routed to the cards through S/PDIF)
```

---

### Post by tribaal on 2008-09-24
Good news :)

I'll investigate and try to make sound work on my HDMI output then.
Did anybody find how to make it work yet?

- Trib'

---

### Post by soxs on 2008-09-24
> **tribaal said:**
> Good news :)

I'll investigate and try to make sound work on my HDMI output then.
Did anybody find how to make it work yet?

- Trib'

Well.. I get rather less sound, but I get a static noise from my integrated speakers in my HP w2408h Monitor, though that shouldn't mean anything and I didn't try it with 8.9 fglrx, yet.. (in case this is the limiting point)
But I guess you donÄt really care as you are nvidia user...

---

