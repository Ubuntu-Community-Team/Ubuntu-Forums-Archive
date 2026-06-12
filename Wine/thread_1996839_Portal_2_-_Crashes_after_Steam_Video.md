---
title: "Portal 2 - Crashes after Steam Video"
date: 2012-06-04
forum: Wine
---

### Post by swiftoid on 2012-06-04
Hi. I've been trying unsuccessfully for a while now to get Portal 2 to work under ubuntu 12.04. I wondered if anyone here has got it working and could share their setup.

Online, people recommend you use the steam download to install it, so I've tried that. At first I tried just installing it through wine natively, then using PlayOnLinux with various wine versions.

Steam installs fine and everything seems to work. But sadly portal 2 crashes after the Steam Video at the start. You normally get about 1/10th of a second of the Portal splash screen, and occasionally I've managed to get to the main menu, but it crashes if you do anything.

Any ideas?

Thanks!

Jamie

---

### Post by thatguruguy on 2012-06-04
What kind of graphics hardware do you have?

Portal 2 runds great on my kids' computer (running Ubuntu 12.04) and my HTPC (running Mythbuntu 12.04).

---

### Post by zuti on 2012-06-04
I think I may have the same problem. Every time I try to run Portal 2 from Steam, it crashes after the intro videos, when reaching the loading screen. No matter how many times I try, it just keeps crashing and Steam keeps guessing the installation is corrupt. 

But when I first run Steam, and then start Portal 2 from the terminal, it works flawlessly (except for the mouse being wonky occasionally).

---

### Post by pioughd on 2012-06-04
I have the same problem as you.  This ptrace_scope adjustment mentioned here worked for me:

[http://forum.winehq.org/viewtopic.php?t=15759&sid=ce1897b00bf294aba20b29bc82149b24](http://forum.winehq.org/viewtopic.php?t=15759&sid=ce1897b00bf294aba20b29bc82149b24)

However after today's update I'm getting some new error when trying to launch portal 2.. something with my D3D drivers.

---

### Post by swiftoid on 2012-06-06
Sorry, meant to say in my first post. I have an ATI HD PCI-E graphics card, can't remember the model off hand, has 1gb RAM. I'm currently not running the ATI drivers, as they were quite buggy. But in the past I did run them and it made no difference to portal. Sorry for the delay in replying, I'm sure I had this topic set to instant email notification, but I haven't received any emails. Oops.

I'll try the launching from terminal thing later. What command are you using? What version of wine are you using? Did you install with POL?

Thanks

Jamie

---

### Post by zuti on 2012-06-06
> **swiftoid said:**
> 
I'll try the launching from terminal thing later. What command are you using? What version of wine are you using? Did you install with POL?


Just tried launching Portal 2 from Steam with the latest 1.5.5 from the Ubuntu Wine PPA. Still not working.

I'm not using POL, just running wine normally. I run the game by going in the portal 2 directory under Steam/steamapps/common, and running wine portal2.exe.

---

