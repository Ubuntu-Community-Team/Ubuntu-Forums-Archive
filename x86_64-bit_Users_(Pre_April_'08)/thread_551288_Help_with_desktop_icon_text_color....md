---
title: "Help with desktop icon text color..."
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-15
I've search and found very little information about a good working solution.  The problem is that I have a light colored background and white text under my icons.

This isn't the case when browsing files with nautilus, it has white background and black text.  I download the source files for a program called gnome configurator that is supposed to allow me to make this change.  I compiled (yay it compiled correctly) the program and still can't change the color.  Have a look at the .png and you'll see what I mean.

Can some one help me fix this please?

---

### Post by John Jason Jordan on 2007-09-15
> **crjackson said:**
> I've search and found very little information about a good working solution.  The problem is that I have a light colored background and white text under my icons.
This isn't the case when browsing files with nautilus, it has white background and black text.  I download the source files for a program called gnome configurator that is supposed to allow me to make this change.  I compiled (yay it compiled correctly) the program and still can't change the color.  Have a look at the .png and you'll see what I mean.
Can some one help me fix this please?
There is a fix for this and it is on these forums somewhere. Unfortunately, I used the fix but failed to bookmark it, so I can't tell you exactly where it is. But if you search the forums you will find it.

---

### Post by crjackson on 2007-09-15
> **John Jason Jordan said:**
> There is a fix for this and it is on these forums somewhere. Unfortunately, I used the fix but failed to bookmark it, so I can't tell you exactly where it is. But if you search the forums you will find it.

I'm pretty sure you are talking about editing the gtkrc[ thread]("http://ubuntuforums.org/showthread.php?t=89197").  I tried this on 2 of my computers already and it's not working for me.

Any other suggestions?

---

### Post by crjackson on 2007-09-28
> **crjackson said:**
> I've search and found very little information about a good working solution.  The problem is that I have a light colored background and white text under my icons.

This isn't the case when browsing files with nautilus, it has white background and black text.  I download the source files for a program called gnome configurator that is supposed to allow me to make this change.  I compiled (yay it compiled correctly) the program and still can't change the color.  Have a look at the .png and you'll see what I mean.

Can some one help me fix this please?

Okay, it looks like the solution to this problem is [COLOR="Red"]**_DON'T USE A LIGHT WALLPAPER..._**[/COLOR]

---

### Post by crjackson on 2007-10-12
Does anyone know if Gutsy has a built in vehicle to solve this problem?

---

### Post by John.Michael.Kane on 2007-10-12
This might be of use.
[HOWTO: Change Nautilus Icon Text Colors (Including Desktop Icons)]("http://ubuntuforums.org/showthread.php?t=89197")

---

### Post by crjackson on 2007-10-12
> **SD-Plissken said:**
> This might be of use.
[HOWTO: Change Nautilus Icon Text Colors (Including Desktop Icons)]("http://ubuntuforums.org/showthread.php?t=89197")

Thanks SD.  That's the same link I was talking about in post 3 above.  It doesn't work on my system.  I'm guess that since it was posted back on 2005, it doesn't work the same on U 7.04.  I was hoping Gutsy might have a built in tweak for this.  Otherwise I'm limited in my wallpaper choices.

---

### Post by John.Michael.Kane on 2007-10-12
> **crjackson said:**
> Thanks SD.  That's the same link I was talking about in post 3 above.  It doesn't work on my system.  I'm guess that since it was posted back on 2005, it doesn't work the same on U 7.04.  I was hoping Gutsy might have a built in tweak for this.  Otherwise I'm limited in my wallpaper choices.

Ok I tested that howto, and can verify it still works under Gutsy.

I posted my .gtkrc-2.0 file remove the .txt extension, and copy it to your home folder, and run the command below.
```
killall nautilus
```
You should be good to go after this.

Note: The way the file is setup it will make the icon text black.

---

### Post by crjackson on 2007-10-13
> **SD-Plissken said:**
> Ok I tested that howto, and can verify it still works under Gutsy.

I posted my .gtkrc-2.0 file remove the .txt extension, and copy it to your home folder, and run the command below.
```
killall nautilus
```
You should be good to go after this.

Note: The way the file is setup it will make the icon text black.

Okay, I'll give this a try tonight.  Thanks.

---

### Post by crjackson on 2007-10-13
> **SD-Plissken said:**
> Ok I tested that howto, and can verify it still works under Gutsy.

I posted my .gtkrc-2.0 file remove the .txt extension, and copy it to your home folder, and run the command below.
```
killall nautilus
```
You should be good to go after this.

Note: The way the file is setup it will make the icon text black.

It didn't work on my Feisty system. Perhaps it will under Gutsy.

---

### Post by John.Michael.Kane on 2007-10-13
> **crjackson said:**
> It didn't work on my Feisty system. Perhaps it will under Gutsy.

Give me a few minutes, and I will see if this works under Feisty, and report any findings.

Edit update I tested this under Feisty, and was able to change the icon text color. As of now I'm not sure why you are unable to make this work under Feisty.

I have included a screen shot showing the icon text color changed.

[[IMG]http://img525.imageshack.us/img525/6342/screenshotia7.th.png[/IMG]](http://img525.imageshack.us/my.php?image=screenshotia7.png)

---

### Post by crjackson on 2007-10-14
> **SD-Plissken said:**
> Give me a few minutes, and I will see if this works under Feisty, and report any findings.

Edit update I tested this under Feisty, and was able to change the icon text color. As of now I'm not sure why you are unable to make this work under Feisty.

I have included a screen shot showing the icon text color changed.

[[IMG]http://img525.imageshack.us/img525/6342/screenshotia7.th.png[/IMG]](http://img525.imageshack.us/my.php?image=screenshotia7.png)

Thanks, just tried again and it won't work for me.  I have black text in nautilus, it's just the desktop that won't cooperate.  Could it be my theme that's causing the problem?

---

### Post by John.Michael.Kane on 2007-10-14
> **crjackson said:**
> Thanks, just tried again and it won't work for me.  I have black text in nautilus, it's just the desktop that won't cooperate.  Could it be my theme that's causing the problem?

Might be. I only tested this using the standard installed theme. You may want to try one of the default Ubuntu themes.

---

### Post by Jouke74 on 2007-10-15
You did reboot, did you (after placing the file in your home dir)? 

The .gtkrc-2.0 only overrides the standard file that is delivered with your theme when it is read the first time during boot. Killing nautilus has little to do with that as it counts for the full GTK theme. I use it on Xubuntu for the same problem and at first it also did not seem to work, however after a full reboot al of a sudden my icon text was different.

---

### Post by crjackson on 2007-10-22
> **Jouke74 said:**
> You did reboot, did you (after placing the file in your home dir)? 

The .gtkrc-2.0 only overrides the standard file that is delivered with your theme when it is read the first time during boot. Killing nautilus has little to do with that as it counts for the full GTK theme. I use it on Xubuntu for the same problem and at first it also did not seem to work, however after a full reboot al of a sudden my icon text was different.

Yes I did reboot.  Doesn't really matter right now, I just did a fresh install of Gutsy and I'm working on a few higher priority tweaks.  I'll get back to this though and let you know if it works for me in Gutsy.

---

### Post by Jerry N on 2007-11-28
Sorry to be reviving a thread that is several weeks old but I tried the prescribed font color fix on my Ubuntu 7.10 system and the font colors did not change.  (I rebooted, of course).  I also tried some variations of this code on LinuxMint 4 (Based on Ubuntu 7.10) and it doesn't work there either.  I would still like to change to a light background.

Jerry

---

