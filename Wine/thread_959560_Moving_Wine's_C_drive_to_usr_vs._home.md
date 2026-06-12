---
title: "Moving Wine's C drive to /usr vs. /home"
date: 2008-10-26
forum: Wine
---

### Post by mcimo88 on 2008-10-26
Hi, I apologize if this has been posted already, but I searched and could not find any information regarding my specific problem. First, here is some info on my setup:

Ubuntu 8.04
Wine 1.1.7
/usr is its own partition, with about 50 Gb available
/ is another partition, with only about 3.5 Gb available

Currently the .wine folder is in /home, which ordinarily wouldn't be a problem, but since I have /usr set up for all my programs, there is barely any room to put anything in my /home folder.

What I would like to do is put the .wine folder in /usr, so that I can actually install programs on it.

Also, before anyone says anything, I already looked and found this: [http://ph.ubuntuforums.com/showthread.php?t=917422](http://ph.ubuntuforums.com/showthread.php?t=917422)

Unfortunately, that is just a bit over the top for what I am trying to do. I am not interested in having multiple users, as I am the only one who uses this laptop.

I wouldn't mind merging the /usr partition back with the / partiton if it can be done without loosing all my current programs.

Please help me out, since I am trying to get as far away from windows as I can. (p.s. I don't hate windows, but Linux is soo much cooler! :) )

---

### Post by YokoZar on 2008-10-26
The proper solution is resizing your /usr partition (or just using the same partition for /home, /usr, and /), not trying some sort of kludge like this.

---

### Post by mcimo88 on 2008-10-27
I know, now that I think about it, I wish I hadn't made /usr into it's own partition...

So, is it possible for me to merge /usr back into / without loosing all my programs, or will I just have to start over again?

If it is the latter of the two, I will probably wait until 8.10 comes out (which isn't much longer, right?)

But, if it can be done without loosing all my apps, would you mind elaborating on how I could do it, please?

Thank you very much for your help! The support on these boards is phenomenal!

---

### Post by DaVince21 on 2008-10-27
A way to do it could be:

- Move .wine to /usr/share/wine/disk or something similar.
- Set permissions for this directory to read+write for the current user.
```
sudo chmod u+rw /usr/share/wine/disk
```
- Create a symbolic link in ~/.wine that links to that directory.
```
cd ~; ln -s /usr/share/wine/disk .wine
```

That should work. Above commands are untested and the chmod command might even be incorrect as I don't use it much.

Also, as mentioned above, it's not really recommended. Keep your user data in /home, /usr/share is intended for extra application data that doesn't change, like a game's sound and graphics or a random application's extra icons.

---

### Post by mcimo88 on 2008-10-28
Hmmm, thats interesting. I appreciate it! Although what I will probably do is just swipe it and re-do the partitions when 8.10 comes out. Luckily I don't have too much installed already!

Again the support on these boards is excellent.

---

### Post by YokoZar on 2008-10-29
> **mcimo88 said:**
> Hmmm, thats interesting. I appreciate it! Although what I will probably do is just swipe it and re-do the partitions when 8.10 comes out. Luckily I don't have too much installed already!

Again the support on these boards is excellent.
I will note that having a separate /home partition is often a good idea - it makes upgrading or migrating substantially easier as you can easily wipe the whole OS while keeping your data.

That said, /home should be where most of the space on your drive goes - I only keep about 8 GB for / and then 4 for swap; the rest is /home.

---

