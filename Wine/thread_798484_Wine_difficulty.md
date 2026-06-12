---
title: "Wine difficulty"
date: 2008-05-18
forum: Wine
---

### Post by krikuku on 2008-05-18
I have just started using wine, and so far it has been a pleasant experience. Although there is one little thing that is bugging me. Wine does not want to install programs directly from discs, I have to move the files to my hard drive in order for it to load properly. Is wine not compatible with this feature or do I navigate a mountpoint that does not exist? (I have checked with nautilus, and it should be /media)

This is the output from the terminal:
> cd /media
kristian@kristian-laptop:/media$ wine install.exe
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\install.exe": Module not found
kristian@kristian-laptop:/media$

Why does wine try to load "C:\\ .. install.exe" when I navigate into /media?

---

### Post by YokoZar on 2008-05-18
> **krikuku said:**
> I have just started using wine, and so far it has been a pleasant experience. Although there is one little thing that is bugging me. Wine does not want to install programs directly from discs, I have to move the files to my hard drive in order for it to load properly. Is wine not compatible with this feature or do I navigate a mountpoint that does not exist? (I have checked with nautilus, and it should be /media)

This is the output from the terminal:


Why does wine try to load "C:\\ .. install.exe" when I navigate into /media?The problem is that there is no "install.exe" in the current folder (/media), so Wine tries to look in the system folder for it - since it's not there either, it spits out the error.

Likely, you want to be in a folder like /media/cdrom or something.

---

### Post by happyhamster on 2008-05-18
> **krikuku said:**
> Why does wine try to load "C:\\ .. install.exe" when I navigate into /media?
- Probably because it can't find install.exe in /media. It then looks in the default wine folder for executables "C:\\windows\\system32\\" and fails to find it there as well.

- So, you'll have to navigate to the correct mount point instead (it's usually something like /media/cdrom0/).

- Also, note that when installing from *multiple* cd's, it's usually best to run the installer from somewhere else than the actual mount point. In other words, use:

wine /media/cdrom0/install.exe

- instead of: 

wine install.exe

- from within the disc's mount point. This will prevent problems that might arise when having to switch discs. In all other situations, should you run programs from within their own folders though.

Good luck.

---

### Post by Redscare on 2008-05-18
Actually it appears that your problem is solved [here]("http://wiki.winehq.org/PreloaderPageZeroProblem")

---

### Post by krikuku on 2008-05-18
I thank you people for helping out! I have successfully loaded the installation :)

I just navigated to /media/cdrom0/ as told :KS

[http://farm4.static.flickr.com/3090/2501248257_a9a07a1e89_m.jpg](http://farm4.static.flickr.com/3090/2501248257_a9a07a1e89_m.jpg)

---

