---
title: "Running WINE games in their own X server?"
date: 2008-04-11
forum: Wine
---

### Post by Colro on 2008-04-11
I've seen several guides on how to do this, but all of them are outdated. Does anyone know how I'd be able to run full screen games in their own X server in order to boost performance and allow for a virtual 'minimize' (ie ctrl alt f6 for game, f7 for gnome)? Thanks in advance for any suggestions :)

---

### Post by cogadh on 2008-04-11
Click on the "Stuff I've learned about Wine" link in my sig and go to the "Advanced Stuff" section. The launch script there will let you launch games in their own X session. I'm not too sure about the "virtual minimize" part though. I've never tried to do that myself, but the only potential problem I see with it would be if the game you are playing happens to use any of those keys for some in-game function. Since the game takes keyboard focus, I can't be certain that you really would be able to switch back and forth like that.

---

### Post by SBFC on 2008-04-11
I use a separate X server for games...

From a terminal...

```
startx /usr/bin/wine war3.exe -- :1
```

The '1' at the end specifies what display to use.

And yes, you can use the CTRL+ALT+F(num) combination to switch between your primary X display and the X display the game resides on.

---

### Post by Colro on 2008-04-11
I'm an error that says my user doesn't have permission to create the X server using your command, SBFC. Do you know how to add the permissions? I'd prefer to not run it as root.

---

### Post by cogadh on 2008-04-11
Edit the Xwrapper.config file to allow normal users X access. Open the /etc/X11/Xwrapper.config file in a text editor using sudo, then change the &#8220;allowed_users=console&#8221; entry to &#8220;allowed_users=anybody&#8221;.

---

### Post by Shadyboy on 2010-02-19
Love it that I can run games trough a new X ^^

Wondering on 1 thing tough. I have no sound when I do it that way.
Any help?

---

### Post by Rody on 2010-02-20
i have used this script a while back. You have to put it in your wow folder.
#!/bin/sh

sudo -- X :3 -ac &   # Launches a new X session on display 3
nvidia-settings --load-config-only
sleep 10   # Forces the system to have a break for 2 seconds
DISPLAY=:3 wine Wow.exe  # Launches WoW
i think we may find a way to do this with more elegance from this post 

[http://ubuntuforums.org/showthread.php?t=822888](http://ubuntuforums.org/showthread.php?t=822888)

but i have not put the time and effort to make it work with wow. I would also like to get ventrilo working in the same window but lack of time and laziness have put that project on hold.

---

