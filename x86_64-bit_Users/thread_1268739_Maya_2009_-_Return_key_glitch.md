---
title: "Maya 2009 - Return key glitch"
date: 2009-09-17
forum: x86 64-bit Users
---

### Post by Saxcore on 2009-09-17
Hiya. I have an odd problem with a new install of Autodesk Maya 2009 (64-bit version). After a few minutes of use, it seems to act as though i have the return key held down; this makes it impossible to click on fields within Maya etc, and causes the computer to bleep when ever i click or interact with the UI, inside or outside of Maya.

One way to stop this is to simply open any other application, and interact with it in some way, preferably bashing the return key until it stops. However, this can sometimes also prove difficult, as anything selected is opened/executed multiple times. I'm unsure if this is a problem with Linux or Maya, however, due to the fact that it carries on outside of Maya, I thought it suitable to post in a Linux forum.

One thing i have noticed is that the pointer changes when this happens, to the black cross, which often appears when there are problems with X or the window manager....

Anyway, thanks in advance for any help!

---

### Post by jlindbergh on 2009-09-24
I've experienced the same thing in Maya 8.5 (and/or 2008, not sure), but with keys like "<-" or "d" or whatever sticking. It's really annoying. Don't remember having the problem in Hardy or Gutsy, but it's definately here in Jaunty. I can get it to stop by carefully navigating into a textbox somewhere in the interface (attribute editor usually) and press a key. That works most of the time.. 

I have no idea what's causing this!

---

### Post by Saxcore on 2009-09-25
Ah, good to hear I'm not alone on this issue!

---

### Post by james_mcl on 2009-09-28
Although I'm using the 32-bit versions of Ubuntu, I have also been having this problem.

In my case, I'm usually using gedit when it happens, and after a few minutes of use it will act as though one of the keys I've pressed is being held down.

It affected Intrepid when I tried to install it at Christmas. I don't remember there being any way to stop it acting as if the key was being held down, I just had to close everything (as soon as I closed one window, the next one would be affected) and restart - and if the key in question was the return key, it caused all the damage done to my files to be saved by automatically pressing Enter at the Save? dialogue.

After erasing the partition and reinstalling a few times, I put Hardy on there instead, and it's completely unaffected by the problem.

I installed Jaunty yesterday on my other partition, and it is affected, however unlike on Intrepid pressing another key will stop it acting like the first one is being held down. Though I *may* have had to press that other key rather hard, or more than once. I've installed all the updates to Jaunty, but this hasn't fixed it.

I'm using a Compaq Presario laptop, but I did once notice the problem affecting a desktop which I *think* was running Slackware.

Finally, it didn't affect my previous Gutsy install, until (some months after installing Hardy I think) I booted into it and was shocked when it occurred.

My guess is that some component of something common to all of these was broken by a dodgy update at some point, and that Hardy might have been using a more stable earlier version of the component in question due to its LTS nature.

I would be really grateful if someone could shed some light on this as I can't reasonably switch to using Jaunty while it continues.

---

### Post by james_mcl on 2009-09-28
I've just done some more research. Unlike at Christmas when I couldn't find anything on this, I seem to have unearthed quite a lot.

The bad news is that there seem to be several different bugs and issues which can result in this. A lot of them seem to be possible to work around by uninstalling plptools and/or disabling certain power management features.

This also means that different versions are affected for different people. I've found someone whose Hardy install was affected, someone for whom Intrepid was fine and Jaunty wasn't, and a bug report going as far back as 2006.

See [http://ubuntuforums.org/showthread.php?t=1048476](http://ubuntuforums.org/showthread.php?t=1048476)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315)

Also, one of the first things I did after getting Gutsy was to follow the advice in this article to disable advanced power management:

[http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/](http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/)

I may (don't remember) have re-enabled these round about the time of the Hardy install because I thought the issue had been fixed. Perhaps this is related to my lack of Gutsy problems.

I'll try some of the more common workarounds when I boot into Jaunty tomorrow, but there are far too many things recommended for it to be worth trying them all if the problem persists - if it does then I'll just wipe Jaunty and install Karmic at Christmas.

---

### Post by Saxcore on 2009-10-02
Hi James. Well researched, some interesting links. Sounds like you have pretty much the same problem. My problem only differs from those in that it only occurs within Maya.

I'm not sure if mine is due to a dodgy install of Ubuntu, either, as this same problem happend on an older install of 9.04 that i installed this same version of Maya on this summer (this version was removed for unrelated reasons, however).

---

### Post by Saxcore on 2009-10-07
Ok, I think I've sorted it! I spoke to the tech guys at uni, and it turns out it's a GNOME bug. They had the very same problem running 32-bit Maya 2008, and allowed me to use their script.

While I haven't rigorously tested it yet, append the following line to your .bashrc file:

```
gconftool-2 --set /apps/gnome_settings_daemon/plugins/a11y-keyboard/active --type boolean False
```

...it basically turns off the "accessibility" keys. Enjoy!

---

