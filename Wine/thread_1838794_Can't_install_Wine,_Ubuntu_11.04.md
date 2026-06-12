---
title: "Can't install Wine, Ubuntu 11.04"
date: 2011-09-04
forum: Wine
---

### Post by Schtenne on 2011-09-04
I was about to install **playonlinux 4.0.11**, the first attempt was via the terminal with following commands according to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) (choosing ubuntu in the distribution list of course):

```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

Suddenly a damn M$ Software end user licence agreement-window pops up within the Terminal-window, interupting the installation, leaving me unable to close it. So I had to close the Terminal, aborting the installation completely,

I downloaded the .deb-package file, but the installation stops, saying "Waiting fot apt-get to exit":

[[IMG]http://s3.postimage.org/2fmvf3klg/Screenshot_Ubuntu_Software_Center.jpg[/IMG]]("http://postimage.org/image/2fmvf3klg/")

So how do I exit apt-get, uninstalling the incomplete install and reinstall it ???

---

### Post by dino99 on 2011-09-04
sudo apt-get install synaptic
sudo apt-get install playonlinux

but instead of playonlinux you can simply install wine1.3
sudo apt-get install wine1.3

---

### Post by dino99 on 2011-09-04
> **Schtenne said:**
> 

So how do I exit apt-get, uninstalling the incomplete install and reinstall it ???

close the terminal, or file->exit

---

### Post by howefield on 2011-09-04
Thread moved to the "*Wine*" forum.

---

