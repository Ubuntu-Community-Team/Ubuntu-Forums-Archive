---
title: "Copy over WOW from windows and play using wine?"
date: 2007-12-01
forum: Wine
---

### Post by Melhisedek on 2007-12-01
Well I've read that it is possible to copy over games from windows and play them using wine. Sadly I haven't been able to find out more about this noble technique ;) What I wonder is where should I copy the wow folder? Than after I copy it over to Linux partition do I need to do some additional stuff in wine? 
I would like to do this with WoW and Baldurs Gate 2, than I'm stocked until I get an nvidia card :)

Thank you for your time!

---

### Post by Beren Camlost on 2007-12-01
First of all, check out [this]("http://ubuntuforums.org/showthread.php?t=624170") post.

Then have a look in the [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") subforum, you'll undoubtfully find dozens of WoW related threads around :)

---

### Post by Melhisedek on 2007-12-02
Bump, someone must have copied their game in order to get it to work with wine...

---

### Post by FiatLux on 2007-12-02
I've done with WoW and it works :) !!! Don't forget to do the registry tweaks described at [http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine") (scroll down to the "Configuration" part).

---

### Post by Melhisedek on 2007-12-02
So where do you copy WoW to ? Any directory will go? Like into Home directory or?

---

### Post by werewolfzx8 on 2007-12-02
> **Melhisedek said:**
> So where do you copy WoW to ? Any directory will go? Like into Home directory or?

I copied mine to the /home/user/.wine/drive_c/Program Files/ directory.

Remember .wine is hidden.

---

### Post by Wiebelhaus on 2007-12-02
> **werewolfzx8 said:**
> I copied mine to the /home/user/.wine/drive_c/Program Files/ directory.

Remember .wine is hidden.

yep , same here but I use Codeweavers which by the way works 100% flawlessly without any user intervention.

---

### Post by Sammi on 2007-12-02
Any ol folder that you have read and write privileges will do, I have it in /home/user/games/ ATM, but as /home/user/.wine/drive_c/Program Files/ is where WoW would install itself by default if you were to run the installer in Wine, I would recommend that if you are unsure.

Anyway here's the Ubuntu community Wine/WoW guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Melhisedek on 2007-12-03
It worked, I got it running but there are quite a few graphical glitches, corrupt icons/skills, map is white and I can't stop running :)
So far unplayable :/

---

### Post by Sammi on 2007-12-03
If you have a ATI graphics then you should try this: [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-afc7fbedbf5a0a378f35eb09d4c6534aec2854e4](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-afc7fbedbf5a0a378f35eb09d4c6534aec2854e4)

---

