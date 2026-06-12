---
title: "gnome wont load???!!!"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by caseyaberhart on 2006-07-24
hi, i have an imac Rev d 333mhz, i installed breezy badger on it, the install went perfectly and boots fine, however after the login screen it plays the startup sound and just sits at a brown screen, no disk activity.
i cane move the mouse pointer thats it.
 
i can get back to the login screen by ctrl-alt-backspace, log in again but the same thing happens, i can get to terminal, failsafe doesn't make a difference. i tried dapper on this computer, but there's a known bug in the kernel that wont let it run on my apple.
 
i was hoping to have this thing running by now.
 
any help is most appreciated. thanks

---

### Post by john_spiral on 2006-07-24
check this thread out:

[http://www.ubuntuforums.org/showthread.php?t=219532&highlight=imac](http://www.ubuntuforums.org/showthread.php?t=219532&highlight=imac)

might be some xorg.conf settings you can use.

---

### Post by caseyaberhart on 2006-07-24
no good... fixes the live cd problem but..... the settings in my hard drive install appear to work... i believe something in gnome may not be loading, but it shows no error messages, i let it sit for 2 hrs but it still just sits there. i'm tempted to start removing the on board hardware and see what that does....:-k  (maybe not).
 
okay.... the live cd does exactly the same thing... i'm not having a lot of luck with ubuntu people](*,) .... i had warty warthog on pc once... didnt run really well on a 200mhz original pentium. i liked it though. i want it on my apple.
 
well like i said i get a brown screen with a mouse pointer i can move around, no errors there or in terminal....
HELP!!!!

---

### Post by linear on 2006-07-24
Check for the [Ubuntu Date Bug]("https://help.ubuntu.com/community/UbuntuDateBug"). Also, make sure you disable dri in xorg.conf.

---

### Post by john_spiral on 2006-07-24
have a look at the last post on

[http://www.ubuntuforums.org/showthread.php?t=212723](http://www.ubuntuforums.org/showthread.php?t=212723)

any good?

---

### Post by caseyaberhart on 2006-07-27
problem solved... it was the date bug... thanks all

---

### Post by john_spiral on 2006-07-28
share more info on how you solved the problem?

---

### Post by caseyaberhart on 2006-07-28
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug) 
 
this link gave me the instructions on how to resolve the problem.

---

