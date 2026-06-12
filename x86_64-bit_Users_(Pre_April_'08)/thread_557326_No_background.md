---
title: "No background"
date: 2007-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by jooaakim on 2007-09-22
I've got a pretty strange problem here. Searched for it but hasn't found anyone else who seem to have a similar one.

For no apparent reason nautilus has stopped working, meaning there is no background (only the default colour) and of course that the nautilus file browser doesn't work.

I've tried creating a new user, but it's the same problem.

sudo nautilus works, the file browser comes up every time and the root background is coming up sometimes.

find * -uid 0 -print in $HOME doesn't show any files. /tmp/ has also got the correct permissions.

It worked perfect on Thursday, and the only change I did that day was to upgrade libpq5.

On Friday at first boot, I had this problem.

I might have missed something I've done, but do anyone have any suggestions what I can do to sort this out?

---

### Post by jooaakim on 2007-09-22
This is one amazingly weird error.

Just booted the live cd for feisty, same thing happened there after 5 mins.

What I've got as an uninterruptible nautilus process. sudo killall nautilus doesnt kill it and neither gnome-system-monitor, as root and as the normal user, or anything else seems to work.

I would be very grateful for some help on this.

---

### Post by OwaN on 2007-10-02
I'm having the same problem. nothing i do to kill the process works and I cant shut down through the shutdown panel. i have to manually kill my computer, which isnt something i really want to be doing. I tried reinstalling nautilus to no avail

---

### Post by John.Michael.Kane on 2007-10-02
You might want to check in /var/log/crash to see if there is a report listed, and if it shows what crashed. This will allow you to file bug reports. 

Also you might take note of what files you upgraded, As well as what programs you installed etc. Also any file modifications you may have done.


When I ran Gnome I never experience the issues you describe, and the system I'm currently running does not have nautilus installed so I can't try reproducing the issue.

---

### Post by OwaN on 2007-10-02
I didnt add any files or anything, but before it happened i opened up the trash file in windows to see if something i deleted a while ago was still there without having to go back into linux to get it. when i got back it asked me if i wanted to delete some kind of applet and without thinking i said yes. Now i cant get anything to work

---

