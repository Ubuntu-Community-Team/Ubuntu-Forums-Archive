---
title: "How to install 32 bit Firefox on 64 bit Ubuntu."
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by ThatBosnianDude on 2009-03-20
I need someone to show me how to install 32 bit Firefox on 64 bit Ubuntu Intrepid. I have some add-ons that wont work on the 64 bit version. I also need help trying to figure out how to uninstall Firefox that is not showing up under Synaptic Package Manager, you see I tried this tutorial to install 32 bit Firefox on 64 bit Ubuntu but I still can't add add-ons and themes, so I need to find a way to remove what I have done in that tutorial and start with a new tutorial that works. Thank you for reading.

PS. I followed this tutorial [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins) but I still can't use my add-ons and themes. I did do a complete removal of the 64 bit version before doing the tutorial, could that have made the problem? And I know they have 64 bit versions of Flash Player and Java, but these add-ons are different from those.

---

### Post by 3Miro on 2009-03-20
Firefox themes are CPU independent, they would run regardless. For the extensions, when you go to search, they only have Linux as an option, so 32 vs 64 bit is not an issue. Any extension on Firefox would run.

For the plug-ins, I don't know. Flash runs easily, just install it from the 64-bit repository (i.e. install Ubuntu-restricted-extras) that's what I did and I have flash working perfectly on 64-bit Firefox. (never mid, you have something else in mind)

Other plug-ins, well are you sure they are for Linux? Windows plug ins wouldn't work in general (maybe with some hacking, but in general - no).

Under synaptic, Firefox is labeled as A Web Browser something - read the descriptions on which one.

Generally you should be able to download Firefox and install it just for your user from Firefox.com. I think the tutorial that you were reading is a bit outdated, but I am not sure.

I know I am not much of help, but I don't know what the problem is. There was a way to run 32-bit flash under 64-bit Firefox long time ago (before there was 64-bit flash), but I am not sure how. Also I am not sure if your plug in would work either (I will try to find the Flash instructions).

---

### Post by 3Miro on 2009-03-20
At the bottom of the tutorial page, there are instructions how to use flash on pre 7.10 versions of Ubuntu. It is basically telling you how to use 32-bit flash under 64-bit Firefox. Maybe you could try the same with 64-bit Firefox and your plug-in.

---

### Post by Slim Odds on 2009-03-20
What, exactly, seems to be the problem?

I use the 64 bit version, with extension and themes, flash, etc.. No problems.

---

### Post by ThatBosnianDude on 2009-03-20
Flash is not the problem I got that working, it's these extensions I have, xpi files that Firefox can't install and themes. I also need help on how to undo what I did in that tutorial.

PS. These extensions and themes are the ones for Firefox that comes with the mac4lin package.

---

### Post by Slim Odds on 2009-03-21
> **ThatBosnianDude said:**
> PS. These extensions and themes are the ones for Firefox that comes with the mac4lin package.

Are they secret or can you tell us which ones?   ;)

It's hard to help if we don't have some details.

---

### Post by ThatBosnianDude on 2009-03-21
No lol, they are not a secret. Sorry about that, probably would have been a lot easier to help if I had included the file names.

custom_buttons.xpi

fission-0.8.8.xpi

hide_menubar-1.0.20080310-fx.xpi

stop_reload_button.xpi

Mac4Lin_1.0.1b_FF3_Aqua.jar

The weird thing is though themes and add-ons I find on the Mozilla website wont work either. And I thought those were kind of guaranteed to work because they are on their website.

---

### Post by 3Miro on 2009-03-21
Add-ons might have a binary part to them, but themes are nothing but a bunch of images. I have 64-bit Linux and I am able to go to the Mozilla web-site and install a bun of themes. Some themes are for windows only and if that is the case, you may have to try Firefox under wine. 32 vs 64 - bit should make absolutely no difference theme wise.

---

### Post by mriendea on 2009-11-13
It may be overkill, but you could run chroot.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

I use it for testing 32bit apps from my 64bit system. Just set it up and install the 32-bit firefox. You can mount your same user acct. in the new root.

---

### Post by Ginsu543 on 2009-11-13
Are the 32-bit Firefox and the 64-bit Firefox the same versions (i.e. 3.5.x vs. 3.0.x)? The only time I had trouble installing extensions is when they become no longer supported. I run 64-bit 9.10 with Firefox 3.5.5 (latest available I believe) and I had no problem installing the Mac4Lin .jar file. You may want to see if you have the latest Mac4Lin available since I see that I have Mac4Lin_FF3_Aqua_v1.0.3b.jar installed.

---

