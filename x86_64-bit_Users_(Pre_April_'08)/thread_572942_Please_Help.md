---
title: "Please Help"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Starjun23 on 2007-10-11
Hey...im pretty new to Linux and Ubuntu so go easy on me.

Trying to modify my touchpad sensitivity I went against the warnings and edited xorg.conf. The system worked fine until I restarted. Then it refused to start the ubuntu shell. The blue screen came up and the diagnosis was a faulty xorg.conf file. So I followed typed in the command to reset xorg.conf (sudo dpkg-reconfigure....). After that the Ubuntu loads to the point where I enter my user name and password. Then there is a blank screen with the orange background, and I can move my mouse around. However it doesn't complete loading.

If anyone knows whats going on, please help me out.

THanks

---

### Post by Kilz on 2007-10-11
> **Starjun23 said:**
> Hey...im pretty new to Linux and Ubuntu so go easy on me.

Trying to modify my touchpad sensitivity I went against the warnings and edited xorg.conf. The system worked fine until I restarted. Then it refused to start the ubuntu shell. The blue screen came up and the diagnosis was a faulty xorg.conf file. So I followed typed in the command to reset xorg.conf (sudo dpkg-reconfigure....). After that the Ubuntu loads to the point where I enter my user name and password. Then there is a blank screen with the orange background, and I can move my mouse around. However it doesn't complete loading.

If anyone knows whats going on, please help me out.

THanks

I think the resolution you allowed is wrong during the reconfigure. You are going to have to do it again and select lower resolutions. Try something safe like 1024x768. You can always make the resolution higher if this works.

---

