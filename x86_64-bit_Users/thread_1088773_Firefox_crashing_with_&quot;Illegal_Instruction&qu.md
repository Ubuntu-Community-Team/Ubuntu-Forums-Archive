---
title: "Firefox crashing with &quot;Illegal Instruction&quot;"
date: 2009-03-06
forum: x86 64-bit Users
---

### Post by Kareeser on 2009-03-06
That's all that the terminal outputs when it crashes... argh

Can anyone here visit [http://www.watchtheguild.com](http://www.watchtheguild.com), and see whether the site crashes firefox?

I even tried running it in safe-mode, but the same crash kept happenning...

If not, then it must be my computer... somehow.

---

### Post by vandorjw on 2009-03-06
Visited.
Firefox didn't Crash.

---

### Post by jwbrase on 2009-03-06
Visited.

Opera, which I have found to be much more stable than Firefox, didn't crash on loading the page, but did crash when I closed the tab. 
/var/log/syslog gives the following error: ```
Mar  6 14:34:21 ubuntu kernel: [14774.896272] opera[7233]: segfault at 0 ip 0000000000d205f8 sp 00007fff589dc9b8 error 4 in opera[400000+d16000]
```

I tried loading the page again, and then closed it out, and got no crash.

---

### Post by Kareeser on 2009-03-28
So, after much testing (by that, I mean basic usage)... I've determined that my liblashplayer.so crashes every so often whenever there are flash elements on a page.

It might even be an ad of a forum that triggers it, but it'll happen eventually.

In the meantime, I've had to disable flash temporarily (or go with npwrapping the 32-bit driver)...

Hopefully, they'll fix it on a new release.

(Using the Adobe labs alpha)

---

### Post by 3Miro on 2009-03-28
With Konqueror:
Visited - No Crash in or out

Firefox:
Visited - No Crash in or out

I win :)

(Didn't stay and watch, video plays, but it didn't look like something I would like)

It is a Flash page so crashes would be due to flash. Did you guys used the repos to install, have you updated your installation ....

---

### Post by Kareeser on 2009-04-03
Oh, it's a hilarious web series. You should check it out.

Anyhow, I installed it from the Adobe labs website... just copied libflashplayer.so to /usr/share/libs/flash/ and symlinked it to the mozilla plugins folder...

---

