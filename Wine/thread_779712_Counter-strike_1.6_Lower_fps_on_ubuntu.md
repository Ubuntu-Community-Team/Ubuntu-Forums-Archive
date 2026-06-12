---
title: "Counter-strike 1.6 Lower fps on ubuntu"
date: 2008-05-02
forum: Wine
---

### Post by Joshgo on 2008-05-02
Hi, I was wondering if anyone knows what's wrong with my settings. On counter-strike 1.6, I usually get 99 fps constant in the small map ka_knife (even with 10 people in map) when I was running windows xp. I was playing on low settings (AA/AF off, vsync off, 640x480 res, block models) and the graphics card I use is a Nvidia GeForce 5200 Fx. Now that I use ubuntu, I get lower fps in counter-strike. For example, I get fps drops when there are only 4 people in the small map ka_knife. I am using nvidia-glx-new and it is up to date, turned off vsync and aa af settings on the nvidia x server settings, and I am using the same config and models as I was on windows xp (config is the ingame settings). Does anyone know what might be the problem? Because I thought I was supposed to get better performance on ubuntu rather than xp.

---

### Post by tamoneya on 2008-05-02
you should turn off compiz and switch to metacity when ever you are playing a game.  Since compiz uses 3d rendering it seriously impacts the playability of 3d games like CS.

---

### Post by Joshgo on 2008-05-02
And how do I do that? I completely uninstalled compiz from source packages

---

### Post by tamoneya on 2008-05-02
that isnt the best way to go if you like to use compiz during normal use but take a look at this forum post.  Basically you want to get metacity enabled.  If you want metacity 24/7 you dont have to worry about the scripting part.  If you want to be able to switch between metacity and compiz you should complete the scripting steps.

[http://ubuntuforums.org/showthread.php?t=778602&highlight=switching+metacity](http://ubuntuforums.org/showthread.php?t=778602&highlight=switching+metacity)

---

### Post by Joshgo on 2008-05-02
I don't want to use anything special, I'm all about performance. How do I check whether I'm using metacity or what not ( I am a noob, I don't know what your talking about ). As for the uninstallation of compiz, I did it before I read this thread, not when you told me that it might be the problem. 

Question: Do I type this in terminal (I saw in the link to the thread you posted)

metacity --replace &

---

### Post by tamoneya on 2008-05-02
yeah try typing that into terminal.  You should get higher frame rates afterwards.

---

### Post by Joshgo on 2008-05-03
Thanks a lot, I am getting higher fps as you said.

P.S: I officially thanked you

---

### Post by tamoneya on 2008-05-03
I noticed.  Glad I could be of assistance.

---

### Post by Joshgo on 2008-05-03
One question, how do I mark my thread as "SOLVED"? And can you help me with my other problem? :D

If you can, here is my other thread

[http://ubuntuforums.org/showthread.php?p=4866446#post4866446](http://ubuntuforums.org/showthread.php?p=4866446#post4866446)

Also, turns out im still getting low fps. At first i got 99 constant with 2 people on the map, but more then that it lowers. But the metacity thing helped. Any other ideas?

---

### Post by Joshgo on 2008-05-04
Does anyone know the problem???:confused::confused::confused:

---

### Post by smrdelj on 2008-05-04
Hello. Excuse me for asking something out of topic, but I have problems running Steam and Cs 1.6 and perhaps yo have already dealed and solved them.
Steam doesn't allow me to install Cs. Did you come with something similar?

Thanks, here's my thread just in case you know anything: [http://ubuntuforums.org/showthread.php?t=777484](http://ubuntuforums.org/showthread.php?t=777484)

Bye

---

### Post by tamoneya on 2008-05-04
mark threads as solved is not still being added since the forum upgrade.  Normally it would be in thread tools.  Hopefully it will be reimplemented soon.

---

### Post by Joshgo on 2008-05-04
I still need help so it's not going to be marked solved.

---

### Post by tamoneya on 2008-05-04
you dont need to mark it solved yet I was just letting you know.  As for how to get the frame rate higher im not sure.  At this point it is probably something to do with wine.  Take a look on the wine forums to see what optimizations there are for CS.

---

### Post by Joshgo on 2008-05-05
Ok thanks. I did that before except I googled it instead of looking on the forums. I found out about this pixel shader that should not be checked.

---

