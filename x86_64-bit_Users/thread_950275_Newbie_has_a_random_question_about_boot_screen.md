---
title: "Newbie has a random question about boot screen"
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by TheSynysterSaint on 2008-10-17
I have a dual-boot on my HP laptop of Vista and Ubuntu. Obviously I'm a bit more versed with Vista than Ubuntu (like most users) and this one is just a random "wtf" about Ubuntu. Whenever I choose to load the Linux kernel, it automatically updates when I connect to the internet. That much I like. However, on the boot screen where I choose which operating system to choose to boot, it offers a new Linux kernel as well as the older ones. I currently have 3 different kernel choices as well as my Vista. Is there any way to get rid of the older options that I don't need? Or will I just have to put up with having obscene amounts of choices for Linux kernel versions to load?

---

### Post by Milleman on 2008-10-17
You could of course remove all the previous kernels except the last one. But it is wise to at least keep the previous latest kernel left, in case something happens to the one that you are using. So you could remove the third last kernel (2.6.24-18 ?) and only keep two kernels visible during boot.

Open up your 'Synaptic Package Manager' and search for "2.6.24". Don't forget to widen the "Package" list by sliding the divider towards right, to be able to see the Package name.

Now, just scroll down and make "Mark for Removal" (right klick) all the modules that are named as your third latest kernel version (2.6.24-18 ?). You should find about 5 modules long the way:

```
linux-headers-2.6.24-18
linux-headers-2.6.24-18-generic
linux-image-2.6.24-18-generic
linux-restricted-modules-2.6.24-18-generic
linux-ubuntu-modules-2.6.24-18-generic
```

Then click "Apply" to make it take effect. After reboot, you will now see only a selection list of 2 kernels. As I mentioned... Keeping at least 1 previous kernel intact as safety, is really wise. If something happens to your latest kernel, either by accident or after package updates, you can always select the previous one and boot from there.

/Mill

---

### Post by TheSynysterSaint on 2008-10-17
Thank you so much! I'll give it a try and see how it works.

---

### Post by purefan on 2008-10-18
very wise tip from Milleman, it just recently happened to me that a kernel update (caused after installing VirtualBox) crashed before showing the log in screen, I dont dual boot, instead I virtualize which has worked fine for me, but in this case the new kernel didnt work, im so glad I kept that .19 kernel... really saved my day, funny thing is, VirtualBox worked fine with the older kernel... so even when it upgraded it (I assume it upgraded it) it was able to work fine with the old one... (?)

---

### Post by TheSynysterSaint on 2008-11-06
To Milleman:

I haven't had a chance to load up and play around in my Ubuntu for a while and I just tried your suggestion. I searched for "2.6.24" and it showed me dozens of options to select. I tried to mark a few I know I don't need for removal, but it only gives me the option to Mark for Installation. I installed all of them that Ubuntu suggested I install, but it still won't let me remove any from the list. What do I do?

---

### Post by blackened on 2008-11-06
The "Startup Manager" application also gives you the ability to remove (by commenting out) older kernel versions from menu.lst. The downside to this is that it doesn't remove the packages themselves (thereby freeing up diskspace).

```
sudo apt-get install startupmanager
```
Find it in "System->Administration->Startup Manager

You could also remove them manually by editing /boot/grub/menu.lst and either comment out or delete the appropriate entries.

---

