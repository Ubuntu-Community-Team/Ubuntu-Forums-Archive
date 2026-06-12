---
title: "Install WinXP on external HD on Ubuntu Laptop"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by trepid666 on 2009-02-13
Hey all.

Today I took on the task of trying to install M$ XP on my 250gig external HD.

I followed these instructions at [http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

I managed to make my own .iso from my original xp cd

When I boot to install, i got ntldr not found error. So i copied that file from my install cd to my external. Then I received a NTDETECT.com error, so I copied that file onto the external. I also copied boot.ini and get an error about a corrupt or missing hal.dll file. Well, I copied that .dll file onto the HD aswell, but still receive that error.

Grub is my bootloader on my internal HD

I have formatted the external to NTFS and made it bootable with gparted.

I'm hoping someone will be able to help me out. I even tried copying the contents of the install cd directly on the HD but that gives me a No Operating System found error.

I have Legacy support enabled in the Bios aswell as having USB and removable drives before my main internal HD and CDRom is first.

It seems to be a big job, but would be well worth the hassle.

Thanx ahead of time

:guitar:

---

### Post by dcstar on 2009-02-14
> **trepid666 said:**
> Hey all.

Today I took on the task of trying to install M$ XP on my 250gig external HD.
......

You better go to a Windows forum and find out if it is possible to do an install onto an external disk.

---

### Post by trepid666 on 2009-02-14
> **dcstar said:**
> You better go to a Windows forum and find out if it is possible to do an install onto an external disk.

Been there, done that.

Is possible

I use Ubuntu, which is why I posted here

Oh, and windows forums are nowhere near as useful as Linux ones =)
The only reason I'm doing this is because I am going to be taking a college A+ course and a prerequisite is to have a laptop computer with windows operating system on it. I really do not want windows actually ON my laptop thank you very much.

---

### Post by khelben1979 on 2009-02-14
According to [this list]("http://www.ngine.de/index.jsp?pageid=4176") you may or may not be succesfull in doing this.

[Here]("http://www.windowsbbs.com/hardware/43314-booting-usb-external-hard-drive.html") you have a thread which might give you something.

---

### Post by trepid666 on 2009-02-14
Cool! Thanks a lot. Appreciate it.

I **will** figure this out! There **has** to be a way haha

---

### Post by khelben1979 on 2009-02-14
I'm interested in this also.

Please post your progress in this thread. I personally thought it was easier than this.

---

### Post by empty_spaces on 2009-02-14
Have you considered virtualbox?
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by trepid666 on 2009-02-14
> **khelben1979 said:**
> I'm interested in this also.

Please post your progress in this thread. I personally thought it was easier than this.


I thought it would be easy too, just disconnect my internal HD , pop in a modified install disc and away i go... but my install disc doesn't allow me to choose where to install. Damn automated windows.

There is tons of documentation on installing a Linux distro on external HDs, I guess thats always an option, but I would rather have windows on the external.

---

### Post by trepid666 on 2009-02-14
I wonder if Vista would install any better?

---

### Post by trepid666 on 2009-02-16
Well, i tried and tried, but have not yet been successful at installing windows onto my external HD.

I have, however, installed both Ubuntu and Gentoo onto that external HD. Simple as pie. I installed Gentoo first from LiveCD, created two partitions, one for Gentoo and one for Ubuntu. Both partitions are 115Gigs each. I then installed Ubuntu 8.04 and was able to use the same swap partition as Gentoo's. Both OS's show up in Grub, and both are fully functioning.

I then made a complete backup of my / directory using TAR. I unpacked backup.tgz in my new Ubuntu, except for the /boot and /grub directories, and voila. Even my Broadcom wireless works!

+1 for Linux -1 for Windows

I think that brings the score to about +100 Linux -99 Windows lol

I think I may just have to install windows onto my internal =(

---

### Post by trepid666 on 2009-02-16
Darn, I spoke too soon. My grub got overwritten in the process and now i can't get back into the external lol crap!

Any1 know how to restore grub?

---

### Post by khelben1979 on 2009-02-16
I'm not sure how to fix your problem, but I think that [this Grub wiki document]("http://www.supergrubdisk.org/wiki/Boot_Problems") can be of interest.

---

### Post by caljohnsmith on 2009-02-16
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problems might be.

---

### Post by trepid666 on 2009-02-16
Cool, thanks for that link about Super Grub. I learned a lot reading through there. I tried editing my menu.lst file to no avail. It still wanted to look for my OS from my internal HD.

I ended up re-installing Ubuntu, which boots perfectly. This time I chose to save the bootloader on a seperate partition on my external HD. Then I just imported my documents and settings from my previous install. I still had to apt-get all my favorite programs and codecs again, but thats not a big deal.

I tried that code posted previous but couldn't get it to work.. Ah well.

---

