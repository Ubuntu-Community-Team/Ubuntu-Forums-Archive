---
title: "Ubuntu won't fully boot up"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by system60 on 2009-02-06
Installed 8.10 on my computer 2 weeks ago and I'm dual booting with XP. As of yesterday Ubuntu wont boot up, it will get to the splash screen and then the screen just stays black. I tried booting off the CD which was fine and I am able to see both my XP and Ubuntu installs fine. 

Thoughts on what to try, this is my first stab at ubuntu/linux

---

### Post by Yashiro on 2009-02-06
Have you tried to boot up in recovery mode?

---

### Post by system60 on 2009-02-06
I tried it and ran file system check and the other option (forget the exact names) but both checked out fine.

---

### Post by Yashiro on 2009-02-06
You ran the xfix option? Make sure you have tried that.

What video card do you have?

---

### Post by system60 on 2009-02-06
Fx5500, works fine when I boot into windows, was working fine in ubuntu as of tuesday.

I don't remember what it was called, I'll try again when I get home tonight. 

Full specs of my computer are

AMD64 3200+
1.5gb ram pc3200
FX5500 video card
DFI Lanparty 250gb MB
320gb WD HDD w/ XP and Ubuntu 
1gb WD for data.

---

### Post by Yashiro on 2009-02-06
You probably need to install(re) your nvidia drivers. Loads of threads on here about it.

It's a bit of a pain for a new guy I know. We had a small kernel update recently. 'Restricted' drivers that interact with the kernel need to rebuild their interface to work properly. It should be automatic but it seems someone broke it.
I don't use nvidia so I can't walk you through it from experience. I'd only be paraphrasing what I know works.

---

### Post by system60 on 2009-02-06
like this [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)  ?

---

### Post by Yashiro on 2009-02-07
> 
Note: Please print these instructions. After step 6 you will be dropped to a shell and not longer be able to read this page.
> 
   1. Open a terminal and type sudo su
   2. Type apt-get install build-essential linux-headers-$(uname -r)
   3. Type cd /usr/src
   4. Type ln -s linux-headers-$(uname -r) linux
   5. Type wget ***[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.23/NVIDIA-Linux-x86-100.14.23-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.23/NVIDIA-Linux-x86-100.14.23-pkg1.run)***
   6. Type /etc/init.d/gdm stop (to stop gdm and drop to a terminal)
   7. Type cd /usr/src && sh ***NVIDIA-Linux-x86-100.14.23-pkg1.run*** (to launch the nVidia installer script)

    * Accept the license agreement to continue
    * Select No on the first question prompting to download Kernel from nVidia
    * Click Ok to compile a new Kernel
    * Select No at the prompt to abort now
    * Let the installer finish the build
    * Select Yes to let nVidia-xconfig automatically update your xorg.conf file
    * Click Ok
    * Once the installer has completed, type startx and enjoy your new video hardware enabled Lenny with nVidia drivers

> You can change your resolution and other advanced video card settings via the nice NVIDIA X Server Settings control applet. Simply navigate to Applications-> System Tools -> NVIDIA X Server Settings
From pendrivelinux.com.

**You will need to change the url and filename to match the driver you need/have downloaded.** You also may want to run
sudo apt-get install cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms 
before you start.

---

### Post by system60 on 2009-02-07
thanks I'll give that a shot tomorrow, if only all forums were this helpful

---

### Post by pistelli on 2009-02-07
I had the same problem, and I followed those steps and everything went well until the end when it told me that it failed to recognize my monitor.

What do I do now?

---

### Post by Yashiro on 2009-02-07
Check some other threads and/or look at
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)
[http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)
[http://ubuntuforums.org/showthread.php?t=488145](http://ubuntuforums.org/showthread.php?t=488145)
Or try [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Or as a quick fix replace the driver "nvidia" in your xorg.conf with "vesa" or log into recovery mode and do xfix, remove the drivers and try again. Or try another method. It sucks I know, Ati is no better.

---

### Post by system60 on 2009-02-08
Went to try this out and today it booted up fine, posting from ubuntu. :D

---

### Post by Yashiro on 2009-02-08
Great. One down, 50000000 to go. :D

---

