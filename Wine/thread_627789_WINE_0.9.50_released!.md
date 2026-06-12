---
title: "WINE 0.9.50 released!"
date: 2007-11-30
forum: Wine
---

### Post by Sockerdrickan on 2007-11-30
Three weeks of work!
Just look at this list! [http://www.winehq.org/?announce=0.9.50](http://www.winehq.org/?announce=0.9.50) :popcorn:

---

### Post by cogadh on 2007-11-30
No 'buntu package yet, though.

---

### Post by MillDaKill on 2007-11-30
Hopefully Battle Net will start working again in WarCraft 3.

---

### Post by hotweiss on 2007-11-30
> **MillDaKill said:**
> Hopefully Battle Net will start working again in WarCraft 3.

Yes, someone else just confirmed it. Battle.net works in 9.50..

---

### Post by Sockerdrickan on 2007-11-30
Nice.

---

### Post by hikaricore on 2007-12-01
LOL

> What's new in this release:
  - **Completed I/O completion.**

WTF does that mean.  ^_^

---

### Post by karth on 2007-12-01
I was wondering a few days ago if M$ had sent some bounty killers to the Wine HQ, since they used to release every 12-15 days. ^^'

It's been a while, and I'm looking forward to testing this! ;)

---

### Post by cogadh on 2007-12-01
MS seems generally uninterested in what Wine is doing. I think they must believe that there is no way Wine will ever reach the necessary functionality to compete with Windows (I think it already has, to a degree). Besides, they aren't doing anything that is illegal or in violation of MS copyrights or licensing. They don't reverse engineer any Wine components using illegally decompiled code, they just use the API documentation and debug outputs from Windows applications. The process is very clearly documented and the code is completely open source, so MS can look at it and see that there is nothing illegal going on.

While Wine has been pretty good about releasing every two weeks lately, that schedule is not set in stone. They will occasionally go three to four weeks without a new release, if there is a good reason for it.

---

### Post by Bionic Apple on 2007-12-01
I can't get the latest Wine from Synaptic!  I have tried Synaptic Package Manager and the terminal way of getting it, but I still only see 9.49 available.  Or have they not uploaded the new one yet?

---

### Post by AnthoMacP on 2007-12-01
> **Bionic Apple said:**
> I can't get the latest Wine from Synaptic!  I have tried Synaptic Package Manager and the terminal way of getting it, but I still only see 9.49 available.  Or have they not uploaded the new one yet?

Give it a few days, it'll be there. Try again this evening or monday :)

---

### Post by Masterizaak on 2007-12-01
Does halo one for PC work on wine?

---

### Post by Sockerdrickan on 2007-12-01
Yes, with 0.9.42 I believe was the last version. We are still waiting for it to work again (hope this version fixes it!!)

---

### Post by rep@linux on 2007-12-01
> **Tux0r said:**
> Three weeks of work!
Just look at this list! [http://www.winehq.org/?announce=0.9.50](http://www.winehq.org/?announce=0.9.50) :popcorn:



someone knows if is solved the installation issue with call of duty?
(can't  insert/run cd2 during setup)

thanks

---

### Post by cogadh on 2007-12-01
That's not a bug, you can just use the "wine eject" command to remove CD 1 and then put in CD 2. There is a bug that occurs when the install asks you to put CD 1 back in the drive, but that one has not been corrected yet.

---

### Post by Takster on 2007-12-01
Cool, i just got the updated package via synaptic.

Warcraft , here i come... :)

---

### Post by Takster on 2007-12-01
Another bonus. PS CS2 is running like it was on XP now. Yesterday i had all sorts of errors and glitches. Now it does whatever i want.

:guitar:

---

### Post by cogadh on 2007-12-01
Sweeet! Advent Rising and Star Trek Armada 2 both work again! This is one hell of a Wine update!

---

### Post by rep@linux on 2007-12-02
> **cogadh said:**
> That's not a bug, you can just use the "wine eject" command to remove CD 1 and then put in CD 2. There is a bug that occurs when the install asks you to put CD 1 back in the drive, but that one has not been corrected yet.

I'll try, but wasn't possible also to mount cd2


....
cvd

[[IMG]http://img101.imageshack.us/img101/1332/schermata1kx9.th.png[/IMG]](http://img101.imageshack.us/my.php?image=schermata1kx9.png)


what can i do?

---

### Post by Sockerdrickan on 2007-12-02
Has it been released yet via their repo?

---

### Post by PmDematagoda on 2007-12-02
Whoa, nice, I can't wait to see what this version of Wine can really do:).

My greatest gratitude to the Wine developers for thinking of and sticking with this great piece of software for Linux:).

---

### Post by Sockerdrickan on 2007-12-02
7.10 debs released [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by cogadh on 2007-12-02
> **rep@linux said:**
> I'll try, but wasn't possible also to mount cd2


....
cvd

[[IMG]http://img101.imageshack.us/img101/1332/schermata1kx9.th.png[/IMG]](http://img101.imageshack.us/my.php?image=schermata1kx9.png)


what can i do?
We should probably take this into a new thread. Create a new one and we can continue over there.

---

### Post by CarpKing on 2007-12-02
Oooh nice- the background of the Wine virtual desktop is now a solid light blue instead of that ugly teal checked pattern.  And Jedi Kinght (Dark Forces 2) now kind of works again!

---

### Post by jpittack on 2007-12-02
I am having issues updating from the last version.  I have the software update icon option, which doesn't work, and using the terminal upgrade returns the error

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Must I use a different method, or can I get this upgrade to work?

I do not have any applications using wine as of yet.

---

### Post by cogadh on 2007-12-02
Did you run "dpkg --configure -a"?

---

### Post by jpittack on 2007-12-02
doesn't make a difference that I used it.  returns with the same error following the command

---

### Post by jpittack on 2007-12-02
I should note there are more errors.

> john@ubuntu:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1
Cannot find /lib/modules/2.6.23.1
update-initramfs: failed for /boot/initrd.img-2.6.23.1
dpkg: subprocess post-installation script returned error exit status 1


---

### Post by cogadh on 2007-12-02
It looks like you have bigger problems. Those messages would seem to indicate that you have a partially failed kernel update. I'd check thorough Synaptic for the current status of the Linux image and kernel module packages.

---

### Post by jpittack on 2007-12-02
I have recompiled a kernel before, the one that is listed, but got rid of it, as it did nothing for me.  I have a feeling I need to point it in the direction of my current kernel, the generic kernel for gutsy.

Package manager does not open.

---

### Post by cogadh on 2007-12-02
Fixing a busted kernel install is a little beyond my skills ATM (I haven't messed with custom kernels in years) and definitely beyond the content of this thread. You might want to post something about this in the General Help or Installation & Upgrades forums.

---

