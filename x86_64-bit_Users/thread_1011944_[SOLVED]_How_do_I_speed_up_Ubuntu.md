---
title: "[SOLVED] How do I speed up Ubuntu?"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2008-12-15
Are there ways to speed up Ubuntu, for example speed up the login process?

---

### Post by Kilz on 2008-12-15
Yes, install bum the Boot Up Manager. You can disable things you dont need in the hardware detection. For instance if you have ati graphics you can disable checking for nvidia .

---

### Post by philinux on 2008-12-15
> **Linux user 66 said:**
> Are there ways to speed up Ubuntu, for example speed up the login process?

If you mean the hang before the desktop becomes fully functional and you're running compiz then yes.

System>prefs>sessions. Scroll to bottom and untick Window Manager. Add a new one with compiz as the command. Login time nearly halves.

---

### Post by Linux user 66 on 2008-12-15
> **philinux said:**
> If you mean the hang before the desktop becomes fully functional and you're running compiz then yes.

System>prefs>sessions. Scroll to bottom and untick Window Manager. Add a new one with compiz as the command. Login time nearly halves.

Just *compiz*?

---

### Post by zika on 2008-12-15
> **philinux said:**
> If you mean the hang before the desktop becomes fully functional and you're running compiz then yes.

System>prefs>sessions. Scroll to bottom and untick Window Manager. Add a new one with compiz as the command. Login time nearly halves.

would this work with "metacity"?

---

### Post by Linux user 66 on 2008-12-15
> **Kilz said:**
> Yes, install bum the Boot Up Manager. You can disable things you dont need in the hardware detection. For instance if you have ati graphics you can disable checking for nvidia .

Thanks! =)

---

### Post by wd5gnr on 2008-12-15
[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)  (disk performance)

[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/) (scheduler, etc)

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_) (swappy)

[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) (speed up log in with preload/readahead)

---

### Post by Linux user 66 on 2008-12-15
> **philinux said:**
> If you mean the hang before the desktop becomes fully functional and you're running compiz then yes.

System>prefs>sessions. Scroll to bottom and untick Window Manager. Add a new one with compiz as the command. Login time nearly halves.

I assume that there would be more to the command than *compiz*, right?

---

### Post by philinux on 2008-12-15
No just compiz works a treat, stops the hang. I've gone from 30 second wait for the desktop down to about 17.

---

### Post by Linux user 66 on 2008-12-15
> **philinux said:**
> No just compiz works a treat, stops the hang. I've gone from 30 second wait for the desktop down to about 17.

I tried what you said; I removed the tick next to Window Manager and added a new start up I called Compiz, with the command "*compiz*", but when I restarted the computer I couldn't log in and I lost audio. I had to boot in rescue mode to undo it.

Are you sure the command is just *compiz*?

---

### Post by philinux on 2008-12-16
Working ok here. Dont forget it needs to be all lower case for the command.
Have you got compiz on?

---

### Post by Linux user 66 on 2008-12-16
> **philinux said:**
> Working ok here. Dont forget it needs to be all lower case for the command.
Have you got compiz on?

Got it working now.

Thanks a lot! =)

---

### Post by aheckler on 2008-12-16
Wow! That compiz trick rocks! I can't believe I've never heard of it before now...

---

### Post by zika on 2008-12-16
Yes, with compiz it works but the gain in time is not so noticable, let alone halved.

I do not have courage to try "metacity" so I will wait for some with more time to get it up again if it doesn't work. :)

UPDATE:

If You want speed metacity is the word! It works! You should try it!

---

### Post by Arup on 2008-12-16
Due to the login bugs with compiz and Intel graphic chips, I am on Metacity and use Murrine based theme, the speed gain is quite significant and the eye candy is not missed, in fact never used eye candy in Windows either. Metacity is easy to enable and works good.

---

### Post by zika on 2008-12-16
> **Arup said:**
> Due to the login bugs with compiz and Intel graphic chips, I am on Metacity and use Murrine based theme, the speed gain is quite significant and the eye candy is not missed, in fact never used eye candy in Windows either. Metacity is easy to enable and works good.

did You enable composite in metacity? that's the cream on the cake ... ;)

---

### Post by Arup on 2008-12-16
> **zika said:**
> did You enable composite in metacity? that's the cream on the cake ... ;)

But of course, thats the default method to turn on metacity. Actually I am very satisfied with this as its a good tradeoff between aesthetics and speed and I won't be needed compiz again.

---

### Post by zika on 2008-12-16
> **Arup said:**
> But of course, thats the default method to turn on metacity. Actually I am very satisfied with this as its a good tradeoff between aesthetics and speed and I won't be needed compiz again.

ditto. that's why I've insisted on metacity ... ;)

thread "how do I speed up Ubuntu" is marked "solved" ... ;))

---

### Post by em4r1z on 2008-12-16
Why the *compiz* instead of *gnome-wm* trick didn't work for me. In fact, the desktop took a bit longer to load than it did before (I restarted the system various times to test this.) This is an AMD64 with Nvidia GeForce Go 6100, updated 8.10 system with Compiz enabled.

---

### Post by Arup on 2008-12-16
Only problem is that turning off compiz will turn off desktop switching as well, a minor glitch.

---

