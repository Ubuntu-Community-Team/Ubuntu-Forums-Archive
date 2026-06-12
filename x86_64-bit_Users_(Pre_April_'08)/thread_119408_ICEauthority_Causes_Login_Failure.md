---
title: "ICEauthority Causes Login Failure"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-19
Ubuntu-64 Breezy, upgraded from Hoary, on Compaq R3240 AMD-64, video at 1680 x 1050. Stupid user new to Linux.

This is the second time this has happened. I am the only user of this computer, so I have root if I want to, but I normally log in as jjj and sudo when necessary. I can't remember if it was before upgrading to Breezy or before, but one day I went to log in and I got an error message that it could not find the profile for jjj. After much help from gurus on the local Linux User Group it was determined that there was something wrong with the permissions on /home/jjj. We fixed the problem, although I did not document what we did. I think we used either chown or chmod. I also created a jxj profile so if it ever happened again I could at least log in.

So yesterday I was at the university and the same damn thing happened again. Grrrr. But since I was at the university I just dragged my computer and my butt to the IT Department's student help lab. Once there a kind person who knew Linux assisted me in getting it going again. The error message was the same as last time, but he noticed that it referred to ICEauthority. He exited X-windows and discovered that I was, indeed, logged in, and could sudo as necessary from the command line. So he did "mv ICEauthority foo" n order to rename ICEauthority to foo. Then we toggled back to X and I was able to log in normally. Afterwards he showed me that if ICEauthority does not exist a new one will be created, so next time this happens I can just delete it instead of renaming it. And this time I documented what we did.

So has anyone else ever encountered this? Is this a bug? Is there a patch I can use to fix this? 'Cause it's really disconcerting to a new user to get to the university and discover that he can't use his laptop when he has homework on it that is due in a couple hours.

---

### Post by FluffyElmo on 2006-01-19
I have this happen when I use k3b. I think when you run it using sudo it changes the permissions on the .ICEauthority file in your home directory to root. I'm not in front of my machine right now, but you can run k3b without this happening depending how you run it (as sudo, as regular user, or as root using su). 

I can't remember which is the proper way right now, it may be worth a search of the general forms since this problem is present in the 32bit distro as well.

To fix it, hit *Ctrl-Alt-F2* to get to a command promt, and then type *sudo chmod 777 .ICEauthority*. You can then hit *Ctrl-Alt-F7* to go back to the GDM login screen.

---

### Post by John Jason Jordan on 2006-01-19
[QUOTE=FluffyElmo]I have this happen when I use k3b. I think when you run it using sudo it changes the permissions on the .ICEauthority file in your home directory to root. I'm not in front of my machine right now, but you can run k3b without this happening depending how you run it (as sudo, as regular user, or as root using su). 

I can't remember which is the proper way right now, it may be worth a search of the general forms since this problem is present in the 32bit distro as well.

To fix it, hit *Ctrl-Alt-F2* to get to a command promt, and then type *sudo chmod 777 .ICEauthority*. You can then hit *Ctrl-Alt-F7* to go back to the GDM login screen.[/QUOTE]

Thanks. I'll add that to the documentation I saved. It's in a OO.o Writer doc, which I can get to even if I have to log in under my alter-ego username.

I can add that there must be something else besides k3b that is triggering it. I do have k3b installed, but I haven't run it for months. In fact, I haven't even made a menu item for it on my Gnome Applications drop-down. Wonder what I did to trigger it?

Wait ... I just remembered something. I installed kivio the other day to try it out. I couldn't get it to run. It didn't install a launch item in the Gnome panel because it's a KDE app. So I tried to launch it by typing "kivio" from the command line. That gave me error messages that seemed to have to do with permissions, so I tried "sudo kivio" and that got it launched. I bet "sudo kivio" is what screwed up ICEauthority. In fact -- taking a wild guess here -- I bet that launching any KDE app via sudo while in Gnome shell will do the same thing. I don't have many KDE apps installed, plus I don't have a lot of time to experiment, but I bet it's a bug in the Gnome shell, or KDE, or Ubuntu.

Thanks for the observation. I think we're getting closer to the issue now.

---

### Post by vir1980 on 2006-01-25
[QUOTE=John Jason Jordan]
... So I tried to launch it by typing "kivio" from the command line. That gave me error messages that seemed to have to do with permissions, so I tried "**sudo kivio**" and that got it launched. I bet "sudo kivio" is what screwed up ICEauthority. In fact -- taking a wild guess here -- I bet that launching any KDE app via sudo while in Gnome shell will do the same thing. I don't have many KDE apps installed, plus I don't have a lot of time to experiment, but I bet it's a bug in the Gnome shell, or KDE, or Ubuntu.

Thanks for the observation. I think we're getting closer to the issue now.[/QUOTE]

Actually, i think the right thing to do, is **gksudo kivio** or the graphical program you want to run. The page where i readit was [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

i hope it helps, it help me:p .

---

### Post by Plastic on 2006-01-25
The same bug from k3b for me.. that "sudo rm iceauthority"- great thing for noob like me..;)

---

