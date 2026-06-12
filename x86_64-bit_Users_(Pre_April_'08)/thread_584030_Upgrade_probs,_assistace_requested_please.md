---
title: "Upgrade probs, assistace requested please"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by BobJ on 2007-10-20
Last week I responded to a notice on my screen that updates were available. I allowed the NVidia driver update, bad move. What had been working fine now gave a black screen. I knew that 7.10 would release this week so I thought id get it and repair my 7.10 beta installation. It appears that the only thing the new install wants to do is wipe my disk and do a clean install. Can anyone tell me how i get this thing to repair? Or, failing that point me to a version of Linux that will repair itself? If Im going to lose all my files I might as well get a slightly more friendly OS.

Thanks in advance
BobJ:???:

---

### Post by John.Michael.Kane on 2007-10-20
You can try this.

Recovery Mode.

1)Reboot the machine.

2) Hit Esc key as Grub loads.

3) Select the most recent kernel recovery mode.

4) After booting it should leave you at a root command line.

You can then try typing the below command.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
followed by startx

Or try the below method

```
sudo nano /etc/X11/xorg.conf 
```
Next scroll down to the section that has your driver listed, and change it to vesa save the file, and reboot.

---

### Post by BobJ on 2007-10-21
Thank you for the assistance. Method one fails at step 4, it never reaches a command prompt. 

Method two was successful, I did modify the file and had a successful reboot. I can now back up whaat I wanted to save.

Thank you VERY much sir.

In reference to my second question, is there a version of Lunux that will upgrade itself? Must one save everything, wipe the disk, and do a complete reinstall every time? Is there a way to persuade Ubuntu to perform this miracle?

Any information deeply appreciated.

BobJ

Thanks again

---

### Post by John.Michael.Kane on 2007-10-21
> **BobJ said:**
> In reference to my second question, is there a version of Lunux that will upgrade itself?
Theoretically, you should be able to upgrade from one version to the next version,Without having to do clean installs.

> **BobJ said:**
> Must one save everything, wipe the disk, and do a complete reinstall every time?
No the end user does not have to save everything, wipe the disk, and do a complete reinstall every time,however. backing up ones data just in case the upgrade goes south is usually good practice.

Also some users feel doing a clean install is the best approach. in the end the end user will have to chose which route is best for their needs, and time.

One more note some users have had issues with Ubuntu's upgrade method. Why is not fully known. Some fell these kinds of issues arise from using third party apps/repos or having a heavily modified installed. 

This might be one reason some users go the clean install method or advise backing up one's data before proceeding.

> **BobJ said:**
> Is there a way to persuade Ubuntu to perform this miracle?
Yes Ubuntu allows for upgrading from one version to the next. One method is outlined in the post below.
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

The other way some users upgrade is by using the command below.
```
sudo apt-get update gksudo "update-manager -c -d
```

> **BobJ said:**
> Any information deeply appreciated.

BobJ

Thanks again
Hope the answers given have helped.

---

