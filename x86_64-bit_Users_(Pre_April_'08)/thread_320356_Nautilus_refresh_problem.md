---
title: "Nautilus refresh problem"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.f on 2006-12-17
Hi,

I have a problem with Nautilus on my 64-bit dapper install. I've noticed this for a while, but not gotten around to look for a fix so far.

For instance, if I have a Nautilus window open with my home directory, and I unpack an archive, or save a file from another program, or change something from a terminal, Nautilus sometimes won't refresh. Sometimes it refreshes if I just change directory and go back, but on some occations I haven't been able to see the correct contents in Nautilus until after I logged off and on again. I must use a terminal to see that the changes have actually occured.

Anyone familiar with this? Any solution? I tried to search the forums but did not find anything about the problem.

---

### Post by maxamillion on 2006-12-17
sudo aptitude install thunar

Thunar is an alternate file manager, its default for xfce (and inherently xubuntu) but I have many friends who use it under Gnome because it too is written in GTK and thus matches their desktop but also is much faster than Nautilus and doesn't face its problematic tendencies. I will warn though, the current version is still young in development so if you use your machine for accessing windows shares, you will still have to access those through Nautilus.

More info can be found here: [http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)

This might not be exactly the fix you were looking for, but it my best recommendation. There has been talk of a complete rewrite for Nautilus floating around the net for some time and it has shown little results and I assume its little follies like the one you encountered will continue to plague users until they do so.

/me

---

### Post by mr.f on 2006-12-17
Thanks maxamillion. You are right is wasn't the answer I expected, but hey, a working file manager is what I really need, so it's definitely worth a look.

I've just installed it and will give it a try. I do have some windows shares as well, but still.

---

### Post by maxamillion on 2006-12-17
Windows shares can be accessed via Thunar, but I will not lie ... it requires a little wizardry and I don't recommend it.

If the Nautilus refresh isn't unbearable then you can still use it for access to windows shares but I think you will find Thunar to be a refreshing delight for every day file management on the local hdd.

---

### Post by mr.f on 2006-12-17
Hmm, thunar seems to suffer from the opposite problem, too many refreshes :confused: 

Actually, I'm not sure if that's what it is doing, but the "working" icon blips about every second, and "top" shows thunar using about 5% of the processor continuously while running.

Maybe my computer is just allergic against file managers...

---

### Post by brokenladder on 2006-12-20
Yeah, I get this exact same weird "constant refresh" problem with thulan or whatever it's called...oh..."thunar" I mean.

As for Nautilus, I thought that it had been, for some time, relying on some push-based kernel mechanism to know when a directory had been updated, so it wouldn't have to poll.  It worked beautifully in Breezy, but not doing it for me in Edgy.  Any changes only show up if I manually refresh the directory view.  LAME.  BeOS had push-based always live directory views about a decade ago.  This is disappointing.  However I'm assuming this is just some glitch happened since I upgraded from Breezy instead of doing a fresh install.  If that's the case, I'm all ears if anyone knows how to fix this.

Thanks!

---

### Post by jjgalvez on 2006-12-27
Hi!

I had the same problem a few weeks ago, not on my Ubuntu system but on my Gentoo system. So I did a little research and found out that Gnome used to rely on fam to notify all the changes, then I read that they upgraded to "gamin" for doing that.

I would say that maybe if you reinstall gamin you can fix it (check first if you have fam installed because you have to remove it first before you install gamin), but for me it didn't, so I did a little more research and found out that gamin uses a kernel feature called "inotify" so I moved to the kernel directory, typed ```
make menuconfig
``` and under File Systems I found "inotify". I just added support for that and recompiled the kernel ```
make && make modules_install
``` then copied the new Image to the boot partition ```
cp arch/i386/boot/bzImage /boot/Kernel
``` and after I restarted the system my refresh problem was gone.

I am not sure if that is a solution you can try on Ubuntu, but at least I hope I can point you in the right direction ;)

---

### Post by mr.f on 2006-12-28
Thanks for the information jjgalvez. I'll try to just reinstall gamin. If that doesn't work, I'll add "digging aound to see if gamin works" on my todo list. But truth to be told, nowadays I just don't have much time hunting down odd problems like this... I can live with it for now, it's just a bit annoying that a basic thing like this doesn't just work.

---

