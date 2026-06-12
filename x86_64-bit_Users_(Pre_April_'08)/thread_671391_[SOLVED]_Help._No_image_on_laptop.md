---
title: "[SOLVED] Help. No image on laptop"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2008-01-18
I am running gutsy x64 on my dell inspiron 1501 laptop. I was trying to display my screen to my new dell 19 inch monitior. I went into the display settings and accidentally changed the default or primary monitor to be the dell 19 inch monitor. I logged off and then i couldnt see anything on either my laptop screen or my monitor. Now i am screwed and i have only me to blame. How can i fix this problem. I need to fix this if anyone would be so kind as to help me. I dual booted xp ad ubuntu but i really prefer ubuntu. thx
What i did exactly is went to system>admin>screen and graphics and changed the default screen to the secondary screen which never worked and now i cant see anything. i need to undo that at the command prompt in recovery mode but i dont know how.
__________________

---

### Post by dcstar on 2008-01-18
> **ghettosamson said:**
> I am running gutsy x64 on my dell inspiron 1501 laptop. I was trying to display my screen to my new dell 19 inch monitior. I went into the display settings and accidentally changed the default or primary monitor to be the dell 19 inch monitor. I logged off and then i couldnt see anything on either my laptop screen or my monitor. Now i am screwed and i have only me to blame. How can i fix this problem. I need to fix this if anyone would be so kind as to help me. I dual booted xp ad ubuntu but i really prefer ubuntu. thx
What i did exactly is went to system>admin>screen and graphics and changed the default screen to the secondary screen which never worked and now i cant see anything. i need to undo that at the command prompt in recovery mode but i dont know how.
__________________

Do a forum search for xorg.conf.

---

### Post by Yellow Pasque on 2008-01-19
sudo dpkg-reconfigure xserver-xorg

---

### Post by ghettosamson on 2008-01-19
@Temüjin

sudo dpkg-reconfigure xserver-xorg

That did the trick. Thanks. Not only are you a gentle man but a scholar. Now, how can I mark this as resolved or closed? Cheers

---

### Post by Yellow Pasque on 2008-01-19
Good to hear.
Right above the first post is a menu called thread tools. I think there's an option to mark it as solved.

---

