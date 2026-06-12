---
title: "Boot splash again (sigh)"
date: 2007-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-12-01
I have tried off and on ever since I installed Gutsy x86_64 on my brand new thinkpad to get the boot splash screen working. I have tried every fix suggested in just about every thread on these forums. (But there are hundreds of them, so I may have missed some.) However, now I think I have discovered the reason I do not have a boot splash screen. While fiddling with this I ran update-grub and got this:

jjj@Devil7:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Evidently the boot splash screen isn't even installed! Guess that would explain why it does not appear during boot!

So I went into Synaptic and reinstalled usplash, but it didn't change anything. I also note that the /boot/grub/splashimages folder is empty.

So what is the name of the usplash image and where is it supposed to live? And if I don't have it, how do I get it?

---

### Post by Ehtetur on 2007-12-01
In Ubuntu, usplash images are kept in /usr/lib/usplash

To see the usplash images you can select, begin with step #3 on this page:
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by erginemr on 2007-12-01
Hello,

I think you are referring to the Ubuntu splash screen not showing up (i.e. the one with a big Ubuntu logo and an orange progress bar).

On the other hand, the grub menu.lst file you have mentioned in your thread is something else. The message you receive during boot refers to the absence of a Grub (the initial boot menu, where you select linux or windows if you have a dual-boot system) background image, which normally is not installed.

I believe you should follow this thread, which will (hopefully) address your problem:

[http://ubuntuforums.org/showthread.php?t=628850](http://ubuntuforums.org/showthread.php?t=628850)

---

### Post by John Jason Jordan on 2007-12-01
> **erginemr said:**
> Hello,

I think you are referring to the Ubuntu splash screen not showing up (i.e. the one with a big Ubuntu logo and an orange progress bar).

On the other hand, the grub menu.lst file you have mentioned in your thread is something else. The message you receive during boot refers to the absence of a Grub (the initial boot menu, where you select linux or windows if you have a dual-boot system) background image, which normally is not installed.

I believe you should follow this thread, which will (hopefully) address your problem:

[http://ubuntuforums.org/showthread.php?t=628850](http://ubuntuforums.org/showthread.php?t=628850)
Thanks for the suggestions. You are correct - I meant the Ubuntu splash screen with the orange progress bar is not showing up. I did not realize that the update-grub error message referred only to the Grub menu. 

I looked at the link to thread 628850, but there is nothing in that thread that I have not read about in a hundred other threads and tried. So far I have not hit on the magic combination to get the usplash screen to appear during boot.

My monitor is 15.4 inch widescreen LCD (laptop) and has a native resulution of 1680 x 1050. I installed hwinfo and it gives me a long list of acceptable resolutions. Considering all the options it would take a very long time to test them all, so I tried just the obvious - 1680 x 1050, 1440 x 900, 1280 x1024, 1024 x 768, 640 x 480 and a couple more. I added them in menu.lst and also in /etc/usplash.conf. And I updated Grub, updated intramfs and nothing has gotten the splash screen to appear.

A lot of the how-tos on this subject have been successful in getting the splash screen to appear for some people, but there are a number of us out there who still have not succeeded. So far I have spent at least a dozen hours trying various how-tos and wikis. As far as I can tell that splash screen depends on a number of other configuration things - too many to make it work reliably. 

[rant mode:on]Every time there is a new release of Ubuntu (especially the x86_64 versions) there are a host of complaints about the splash screen not showing up, followed by pages and pages of instructions and patches for people to try. Maybe it's time for Ubuntu developers to scrap the whole thing and start over with something that requires no other modules so it will just work always on all computers. Or maybe someone could write such a tool and make it available in Synaptic as an alternative boot splash utility. I don't need the official Ubuntu splash screen, I just need a progress bar so I can be sure it didn't hang up on something or decide to go into fsck because it's the 30th boot. I'm sick of fiddling with it. [rant mode:off]

---

### Post by Clancy_s on 2007-12-01
> **John Jason Jordan said:**
> My monitor is 15.4 inch widescreen LCD (laptop) and has a native resulution of 1680 x 1050. I installed hwinfo and it gives me a long list of acceptable resolutions. Considering all the options it would take a very long time to test them all, so I tried just the obvious - 1680 x 1050, 1440 x 900, 1280 x1024, 1024 x 768, 640 x 480 and a couple more. I added them in menu.lst and also in /etc/usplash.conf. And I updated Grub, updated intramfs and nothing has gotten the splash screen to appear.]

PMJI - I'm browsing all splash threads at the moment since I'm about to try fixing it y on my own newish64 bit gutsy install.

The lower resolutions you list above look like standard not widescreen to me: the one i know best is for a 1280 width since that's my default: the height would be *800* not *1024* for widescreen.  I don't know if that would make any difference....

I agree that this is one of those things that the developers should make considerable effort to get to 'just work' since it's a problem that'll face newbies on their first boot.  It's been 10 days since I installed ubuntu, only today did I find out that there was *supposed* to be a splash screen.  It's not mentioned in the pre-install notes so far as I remember.

eta: on my laptop (Toshiba Satellite A200) with a max screen resolution of 1280X800, the default 1280 x 1024 means no splash screen, changing that to 1280 x 800 and running sudo update-initramfs -u  fixed it. :)

---

### Post by erginemr on 2007-12-02
> **John Jason Jordan said:**
> ...
My monitor is 15.4 inch widescreen LCD (laptop) and has a native resulution of 1680 x 1050. I installed hwinfo and it gives me a long list of acceptable resolutions. Considering all the options it would take a very long time to test them all, so I tried just the obvious - 1680 x 1050, 1440 x 900, 1280 x1024, 1024 x 768, 640 x 480 and a couple more. I added them in menu.lst and also in /etc/usplash.conf. And I updated Grub, updated intramfs and nothing has gotten the splash screen to appear.
...

Could you please post your current menu.lst and usplash.conf here?

---

### Post by erginemr on 2007-12-02
> **Clancy_s said:**
> PMJI - I'm browsing all splash threads at the moment since I'm about to try fixing it y on my own newish64 bit gutsy install.

The lower resolutions you list above look like standard not widescreen to me: the one i know best is for a 1280 width since that's my default: the height would be *800* not *1024* for widescreen.  I don't know if that would make any difference....

I agree that this is one of those things that the developers should make considerable effort to get to 'just work' since it's a problem that'll face newbies on their first boot.  It's been 10 days since I installed ubuntu, only today did I find out that there was *supposed* to be a splash screen.  It's not mentioned in the pre-install notes so far as I remember.

eta: on my laptop (Toshiba Satellite A200) with a max screen resolution of 1280X800, the default 1280 x 1024 means no splash screen, changing that to 1280 x 800 and running sudo update-initramfs -u  fixed it. :)

You are right. The decision of the developers for making default usplash resolution too high has rendered it unusable esp. for the laptop owners and has been a source of confusion for quite a few Ubuntu users. I am a desktop computer user but I believe neither Edgy nor Feisty had this problem. 

I hope Ubuntu developers will issue an official patch, guide or something for this soon.

---

### Post by chubs on 2007-12-02
i'm also missing a boot splash screen.  I tried changing the resolutions in /etc/usplash.conf (my desktop resolution is 1680x1050) and running sudo update-initramfs -u, but still no splash.  Also, I tried startupmanager with no effect either.

---

### Post by John Jason Jordan on 2007-12-03
> **chubs said:**
> i'm also missing a boot splash screen.  I tried changing the resolutions in /etc/usplash.conf (my desktop resolution is 1680x1050) and running sudo update-initramfs -u, but still no splash.  Also, I tried startupmanager with no effect either.
If you search the forums you will find lots of threads on this, mostly from x86_64 users. There are a number of fixes that have helped a lot of people. But each person's situation seems to be slightly different, so what works for some does not work for all. I am still trying to find a solution.

My native screen resolution is also 1680 x 1050. Out of curiosity, what kind of computer and video do you have?

---

### Post by erginemr on 2007-12-03
> **chubs said:**
> i'm also missing a boot splash screen.  I tried changing the resolutions in /etc/usplash.conf (my desktop resolution is 1680x1050) and running sudo update-initramfs -u, but still no splash.  Also, I tried startupmanager with no effect either.

Those who cannot see the Ubuntu boot splash screen, please try to do the folllowing:

> Originally Posted by erginemr View Post
You are welcome. I am not sure but it seems there is a problem with the Ubuntu splash screen resolution. I am also using Gutsy and my default splash screen had a very high resolution by default. The file to change is:
/etc/usplash.conf

Mine looks like this:
# Usplash configuration file
xres=1024
yres=768

Can you start with editing this file, first backing up the original just in case with:
sudo cp /etc/usplash.conf /etc/usplash.bak

Then edit it with:
gksu gedit /etc/usplash.conf

and change the resolution as
xres=800
yres=600

Do it and reboot to see if there is any progress. Otherwise, we shall attack xorg.conf.

and

> Originally Posted by eye208 View Post
The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash

to apply the changes. This step will copy the usplash config file into the ramdisk image used by the kernel on startup.

If the out-of-range warning appears after the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg

Choose manual monitor configuration, then pick the appropriate resolution(s) from the list. When configuration is done, press Ctrl-Alt-Del to reboot.
will surely solve it.

Especially the step "sudo dpkg-reconfigure -phigh usplash" after editing your "/etc/usplash.conf" file.
It worked for many people.

---

### Post by chubs on 2007-12-03
> **John Jason Jordan said:**
> If you search the forums you will find lots of threads on this, mostly from x86_64 users. There are a number of fixes that have helped a lot of people. But each person's situation seems to be slightly different, so what works for some does not work for all. I am still trying to find a solution.

My native screen resolution is also 1680 x 1050. Out of curiosity, what kind of computer and video do you have?

compal ifl90 with an nvidia 8600gt.

also, erginemr... neither of those restored the boot splash, so i'm still stumped

---

### Post by erginemr on 2007-12-04
Gosh! It seems your laptop is this one:

[http://www.xoticpc.com/force-3297-built-compal-ifl90-p-1983.html](http://www.xoticpc.com/force-3297-built-compal-ifl90-p-1983.html)

which defaults to 1680x1050, but I have also seen web pages that refer to several versions of Compaq IFL90 as having 1440x900 as the native resolution. The thing is that, quite a few LCD displays have one and only natural resolution and refresh rate, with which they run and look best. The problem is to find out which.

If I were in your boots, I would grab the Live CD of a former Ubuntu version, be it Feisty or Edgy (a Linux Mint Live CD also does the job), boot it and if I can see the splash screen and progress bar, I would chek the "/etc/usplash.conf" file of the Live CD environment. Hopefuly, this will help you pipoint the required solution for the usplash.

---

### Post by Jimmy_r on 2007-12-15
> **John Jason Jordan said:**
> 
[rant mode:on]Every time there is a new release of Ubuntu (especially the x86_64 versions) there are a host of complaints about the splash screen not showing up, followed by pages and pages of instructions and patches for people to try. Maybe it's time for Ubuntu developers to scrap the whole thing and start over with something that requires no other modules so it will just work always on all computers. Or maybe someone could write such a tool and make it available in Synaptic as an alternative boot splash utility. I don't need the official Ubuntu splash screen, I just need a progress bar so I can be sure it didn't hang up on something or decide to go into fsck because it's the 30th boot. I'm sick of fiddling with it. [rant mode:off]

How about splashy
[http://ubuntuforums.org/showthread.php?t=477426](http://ubuntuforums.org/showthread.php?t=477426)

---

