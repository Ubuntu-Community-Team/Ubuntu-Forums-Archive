---
title: "Desktop Randomly locking up"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by xdemo on 2009-11-10
This is my issue:
Basically, every now and then, the whole desktop will lock up. Literally, the mouse will be unmovable and all graphics will freeze. Sound still plays while this happens though.

I first noticed this on a 32bit version of jaunty. However it was less frequent.
I have been watching some movie's lately, and its quite frustrating when the screen locks up, but the sounds still plays, then resumes as normal after 15-20 seconds.

I'm not sure why this happens.
Sometimes it will occur while simply browsing the web on firefox using little resources. Things like watching a film with VLC media player make it happen more often.

At the moment im using 64bit karmic. Aswell, i noticed the same issue with the 32bit karmic. I first thought it could be my computers processor wasting ram while using the 32bit version, but there seems to be no difference.

I'm also wondering if this is a GNOME issue. As i am using the standard ubuntu karmic x86_64 version... whether to switch to xubuntu may fix this issue?

I'm lost to be honest, and can't find whats causing it, i have tried closing down every un-needed application etc, reinstalling certain items.

Any suggestions?

---

### Post by irishbreakfast on 2009-11-10
I too have lock up issues on karmic 32bit. I have not noticed that it is related to the usage of resources. I normally have the same applications up (Firefox/tbird/oo/gnu backgammon). 

I do have 4 horizontal workspaces, other than that I don't think I changed any default settings.

Fortunately, I have been consistently able to unlock it by clicking using the touchpad, whereas my USB mouse will move but not click.

---

### Post by pato101 on 2009-11-10
> **xdemo said:**
>  the mouse will be unmovable and all graphics will freeze. Sound still plays while this happens though.
[...]
Any suggestions?

Looks like a problem with the X-server. The fact that sound is playing means that the processes are alive. What it is just hung is the graphic system.

I would blame the videocard driver. Which card is it?

Disable desktop effects and see if it keeps happening.

If you have lan, install openssh-server package and do try to login with ssh from another machine when this happens and look which is the process which is consuming CPU (I guess Xorg), take a look at the logs (dmesg, /var/log/messages, /var/log/Xorg.0.log ... )

---

