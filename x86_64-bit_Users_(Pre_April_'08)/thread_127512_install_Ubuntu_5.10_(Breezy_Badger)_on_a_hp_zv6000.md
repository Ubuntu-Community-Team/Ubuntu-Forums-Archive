---
title: "install Ubuntu 5.10 (Breezy Badger) on a hp zv6000"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by extranatural on 2006-02-09
I am making this post in an effort to simplify and consildate the information I've found by searching the forums and googling the rest of the web. Anyways I have a HP ZV6000 and have had one hell of a time trying to install linux on it. After a lot of research I chose ubuntu linux, I dunno if they're still offering this deal but for a while ubuntu would send you a copy for free. They sent me ubuntu 5.10 (breezy badger). I've been working on getting linux tweaked just right for a while now. This is what I have so far:

1.First I installed linux, so far so good smooth sailing.

2.Than once installed I ran into some trouble: "failed to start x server" to solve this type the following:

- sudo pico /etc/X11/xorg.conf

- press ctrl + w and search for ati

-under the last line in the area labled ati add this line of code: Option  "noaccel"

-press ctrl + x to exit, save changes by pressing y than enter

-than restart the graphical user interface by typing this: sudo /etc/init.d/gdm restart

this should get you into a functioning graphical version of ubuntu, my next post will be on making the wireless card work, I also plan on posting how to get the ATI graphics card working. I made this post only with hpzv6xxx users in mind, anyone else who follows this information may be SOL. Good luck linux users!

---

### Post by ruudiculus on 2006-02-09
You may not have noticed that there are threads already about this subject, so it may be wise to help us by sharing your experiences in those threads. 

For example, setting up the wireless networking card is something already explained in my howto (click on the link below). There still are problems with the ATI video card ([http://ubuntuforums.org/showthread.php?t=106047]("http://ubuntuforums.org/showthread.php?t=106047")) so if you have any ideas ;)

---

