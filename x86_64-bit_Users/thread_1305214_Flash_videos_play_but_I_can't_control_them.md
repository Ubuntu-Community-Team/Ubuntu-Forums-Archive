---
title: "Flash videos play but I can't control them"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by samh785 on 2009-10-29
I'm using the 64-bit ubuntu 9.10 Karmic Koala. I've noticed that instances of flash are unresponsive. What I mean by this is that: I can load a youtube video or a video on hulu or whatever, but I cannot make them go fullscreen by pressing the fullscreen button with my mouse. I cannot pause the flash instance by pressing the pause button with my mouse, but curiously on youtube I can pause the video by pressing space... 

any help would be appreciated :)

---

### Post by Monotoko on 2009-10-29
Same for me...apparantly removing the flash plugin currently installed and installing swfdec-mozilla works for some people.

Makes it slow and buggy for me though

---

### Post by philinux on 2009-10-29
swfdec is useless.

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by samh785 on 2009-10-29
I just totally removed flash from my system and followed the installation of flash instruction sticky at the top of this 64-bit subforum

---

### Post by TheOneEyedMan on 2009-11-03
Same problem on 64-bit ubuntu 9.10 Karmic Koala.
I didn't find the flash installation directions in the forum to work (made flash constantly crash my browser constantly), so I'm looking for other solutions if anyone has any.

---

### Post by solsen300 on 2009-11-03
I just totally removed flash from my system and followed the installation of flash instruction sticky at the top of this 64-bit subforum...and it still doesn't work.

---

### Post by infestor on 2009-11-04
> **solsen300 said:**
> I just totally removed flash from my system and followed the installation of flash instruction sticky at the top of this 64-bit subforum...and it still doesn't work.

same here...flash is still out of control! can anyone suggest a solution to that?

---

### Post by bigbroantonio on 2009-11-04
Take a look here:

[http://ubuntuforums.org/showthread.php?t=1313806](http://ubuntuforums.org/showthread.php?t=1313806)
[http://ubuntuforums.org/showthread.php?t=1311649](http://ubuntuforums.org/showthread.php?t=1311649)
[http://ubuntuforums.org/showpost.php?p=8204310&postcount=17](http://ubuntuforums.org/showpost.php?p=8204310&postcount=17)

Read the threads carefully and if you still have no luck make sure you reboot your machine before saying "that doesn't work".

The standard method (recommended)is to move libflashplayer.so to /usr/lib/mozilla/plugins/ (after getting rid of previous flash installations.

---

### Post by bigbroantonio on 2009-11-04
I see that the tread is now [solved].

Which solution worked for you?

---

### Post by samh785 on 2009-11-04
> **samh785 said:**
> I just totally removed flash from my system and followed the installation of flash instruction sticky at the top of this 64-bit subforum
That one worked for me.

---

