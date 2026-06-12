---
title: "State of x64 Ubuntu (?)"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by foundation on 2008-03-10
Ok, so I feel like giving 8.04 a shot (I'm backing up everything now (About 400GB.. it's going to take awhile) as I'm about to reinstall Vista x64 and I'd like to have Ubuntu as a secondary choice for a small subset of things and MacOS 10.5.2 as a third choice for *other* things) and I've burnt both the 32 and 64 bit versions and I'd really rather go with 64bit (Especially so after being on Vista 64 for the past >= 6 months) but I'm worried as to what won't work.

So, what things do not work or require a large amount of effort to get working? Last time I was messing around with Ubuntu things like FF (Well, I'm in the Live CD now and Firefox is working perfectly so scrap that), Flash and some other things were kind of horrible on the 64bit version. Also, what about problems with being up-to-date with whatever packages (What I mean is, are 64 bit versions of software generally available later or not at all? For things related to everything, like the core OS to Amarok, Pidgin, etc), things like Wine, etc? Basically, if you know of a con of the 64bit version, please let me know.

If it's bearable to get whatever things working in 64, I'll go with it, but if it really is **way** too much effort I might not bother.

The other thing I'd like to know are the pros of the 64bit version, so shoot. :)

Just in case you'd like to know, my specifications are:

Gigabyte P35-DS3P
Intel Core 2 Duo E6750
4GB (4x1GB) DDR2 800 Corsair TwinX
BFG8800 GT OC 512MB
500GB Western Digital SATAII
200GB Seagate SATAII
80GB Western Digital SATAI
Logitech Media Keyboard 600
Razer DeathAdder

Oh, and I'm not computer illiterate, no where near and I'm liking 8.04 so far, mostly just a ton of subtle changes I've noticed. Another question, how well does Linux work with the Vista bootloader? I'd rather use it than GRUB.

Edit:I only just noticed the sticky about 32 vs 64, I'll go through that now.

---

### Post by Kevbert on 2008-03-10
Apart from flash, nearly everything I have runs OK in Ubuntu 7.10 X64.  Updates are fine.  Flash works with a bit of fiddling.  Compiz doesn't seem to work as I can't get the rotating cube desktop to work.
I also have Ubuntu 32 bit installed, to fall back on, but have not needed to use it yet.

---

### Post by NightwishFan on 2008-03-10
64-bit has given me the exact same experience as 32-bit but a lot faster. Many of the old bugs are fixed and you can get flash from the repos now although I do not advise it. Use the r48 script kilz has offered. Note that 32-bit has many bugs as well, and 64-bit can only get better if we all work to fix it. :)

---

### Post by foundation on 2008-03-10
Sounds good so far but Compiz Fusion is a *must* for me, so in general does it not work on 64bit or are there kind of isolated problems?

---

### Post by NightwishFan on 2008-03-10
Compiz Fusion works flawlessly for me in 64-bit gutsy and even more flawlessly in hardy alpha. :)

---

### Post by foundation on 2008-03-10
Awesome, thanks for the good news. Anyway, I *will* go with 64bit 8.04 and if I do run into any problems I should be able to figure it out, or ask on here.

Time to finish backing up, only a couple hundre GB left. :x

---

### Post by Kilz on 2008-03-10
Hardy isnt even a beta yet. It is still in Alpha testing. An upgrade can make your system unusable when in development. I dont recomment anyone install it that  isnt 100% abel to troubleshoot and fix Ubuntu. This section is for release version, and as such will not be a good source of help with Hardy since it is in development.

---

### Post by jespdj on 2008-03-10
I am currently testing 64-bit Hardy alpha 6 on my desktop PC. It works great. Installing Flash is easy, if you
```
sudo apt-get install flashplugin-nonfree
```
then it automatically installs nspluginwrapper and the necessary 32-bit libraries to make Flash work in Firefox 3. No manual tweaking necessary.

I have no problems with Compiz on either 64-bit Hardy alpha 6 or 64-bit Gutsy.

I remember that I needed to tweak stuff in 64-bit Ubuntu 6.06 and 6.10, but with every release it's getting more and more easy. It looks like 64-bit Hardy is going to be really nice - I'm planning to go 64-bit on both my desktop and laptop when Hardy comes out.

Also please read the [sticky](http://ubuntuforums.org/showthread.php?t=368607) about 64-bit.

---

### Post by flick on 2008-03-10
To reinforce what kilz said :

[http://ubuntuforums.org/showthread.php?t=720140](http://ubuntuforums.org/showthread.php?t=720140)

Too many people running an alpha release because it's kewl or something. Then mad as hell when a batch of updates breaks everything, when the whole point of alphas, betas and release candidates is to find out what breaks and how, NOT to be a productive OS.

If you're going to run Hardy, please, run it to find and report bugs, not to get the "latest and greatest".

For those who like apt-get, and want current software all the time, I recommend Sidux/Debian Sid. However, Debian Sid is the Unstable branch and it's called Unstable for a reason. Bleeding edge software and stability are mutually exclusive, by definition.

---

### Post by Kevbert on 2008-03-10
> **NightwishFan said:**
> Compiz Fusion works flawlessly for me in 64-bit gutsy and even more flawlessly in hardy alpha. :)

Hi.  Could you let me know how you set up Compiz to get to rotating cube desktop ?

---

### Post by NightwishFan on 2008-03-10
If you have the restricted drivers installed skip to step 2. :)

1) Install the restricted drivers, and reboot.
2) open a terminal and type:
```
glxgears
```
If you see spinning gears then you should be fine.
3) open a terminal and type:
```
sudo apt-get update && apt-get install compizconfig-settings-manager
```

Should work from there. In system, prefererences there is an advanced desktop settings thing. Configure from there. If you cannot use it then open a terminal window and type:
```
compiz --replace
``` and see what it says.

---

### Post by Kevbert on 2008-03-10
Hi. Thanks for the info.  It looks like I have the cube already, but the cube is the full size of the screen and was rotating very quickly.  I slowed the rotation down by using Shift-F10.  I still can't seen the top or bottom face when the cube rotates.  How do I reduce the cube size ?
Thanks in advance...

---

### Post by NightwishFan on 2008-03-10
Check the "rotate cube" and "cube caps" plugins.

Then you can configure the zoom and images of the caps respectively. Also you can add "cube reflection" as I did.

---

### Post by Kevbert on 2008-03-10
Thanks NightwishFan. It's working at last...:KS:KS:KS

---

### Post by NightwishFan on 2008-03-10
No problem. Now I just have to get Kubuntu Hardy working. Gnome finally bores me.

---

### Post by konungursvia on 2008-03-12
> **Kevbert said:**
> Apart from flash, nearly everything I have runs OK in Ubuntu 7.10 X64.  Updates are fine.  Flash works with a bit of fiddling.  Compiz doesn't seem to work as I can't get the rotating cube desktop to work.
I also have Ubuntu 32 bit installed, to fall back on, but have not needed to use it yet.

I have compiz working fine, I think it started working as soon as I enabled aiglx. I do occasionally have nautilus freeze up my volumes and have to reboot, but only twice a week.

---

