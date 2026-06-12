---
title: "&quot;Upgrading&quot; to edgy was a waste of time?"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kopilo on 2006-11-08
A few nights ago I tried to install Edgy by using the alternative disc, it failed horribly, it got to a section on the install and just hung then failed, I tried skipping the step but that also failed... Anyway after about 2 hours of playing with different settings I decided to do an upgrade instead.

So I installed Ubuntu drapper and used the alternative CD to upgrade to Edgy. Everything went perfectly well and I was excited as edgy started to boot (taking notice of the differences).

However it was incredibilly slower then draper, it was like having constant lag. Granted Open GL was automatically installed but the gears ticked, they didn't move smoothly and that's without mentioning the state of Firefox.

Did I do something wrong or does edgy 64 take a lot more processing power or something?

---

### Post by bluenova on 2006-11-08
Strange it was perfect for me, and much faster than Dapper, even with Beryl running. Granted the new nVidia beta drivers have helped a lot.

---

### Post by fabertawe on 2006-11-08
Edgy is supposedly faster or snappier but I haven't noticed much difference. It certainly doesn't boot any faster as I have seen claimed many times. Saying that it is certainly not slower, at all.

My upgrade went great. Maybe you will have to stick with Dapper until Edgy has some updates and then try again.

Paul

---

### Post by glotz on 2006-11-08
You mention 'the state of Firefox'. What do you mean by that?

---

### Post by kopilo on 2006-11-08
It's a bit hard to explain basically when I went to scroll down a page it was very choopy, like the whole page would re-render (each render taking around 600 milliseconds) on a new position on the scroll bar.

---

### Post by glotz on 2006-11-08
Are you by any chance on a dual core or dual processor machine?

---

### Post by kuja on 2006-11-08
At which section did your install hang? Oftentime when that happens it means the cd is corrupt. Did you check the integrity of the disk before installing with it? That can save headaches, seeing as even if you complete an install with a corrupted disk it will give you trouble later (ie: uninstalled packages, perhaps limitted functionality or crashes in the installer, etc). 

The rendering problems, plus the lack of smoothness with glxgears are linked to each other. That's a video driver problem.

I did my install a bit different this time. I did a server install, then installed kde-core along with the things I needed. My bootchart is 18seconds :D All in all, it's probably about the same speed as Dapper. (I hear that Edgy boots faster on exceptionally slow machines, but otherwise doesn't make much difference.)

---

### Post by fabertawe on 2006-11-08
> **kuja said:**
> My bootchart is 18seconds :D All in all, it's probably about the same speed as Dapper. (I hear that Edgy boots faster on exceptionally slow machines, but otherwise doesn't make much difference.)

Pardon? 18 seconds?! :shock: Do you know how to read bootcharts? Maybe you could post it please. I was 45 secs in Dapper and I'm 43 in Edgy but I've had to disable even more services to get down to that!

Cheers ... Paul

---

### Post by DJiNN on 2006-11-08
I've just done an upgrade here (From Xubuntu Dapper 6.06 to Xubuntu Edgy 6.10) and it all went superbly well, and is now working even better than it was in Dapper. In fact, i was expecting one or two issues but there were none at all, which was pleasantly surprising! :)

It certainly "Feels" faster, and Firefox 2 is a lot better than the last version. All in all, i'd say that it was a pretty amazing upgrade & all credit to the Ubuntu team for making it so.

---

### Post by kuja on 2006-11-08
> **fabertawe said:**
> Pardon? 18 seconds?! :shock: Do you know how to read bootcharts? Maybe you could post it please. I was 45 secs in Dapper and I'm 43 in Edgy but I've had to disable even more services to get down to that!

Cheers ... Paul
Lets see here, how to shave time off the boot:
Use the XFS filesystem(takes about a second less to mount than xfs, and well, a lot compared to reiser.... I think my boot time using reiserfs in edgy was around 30 seconds)
Only mount the needed filesystems on boot
have no cds in the drives(they add on about 3 seconds a piece)
disable usplash in /boot/grub/menu.lst (saves about 2 seconds)
It's default in edgy, but make sure /bin/sh points to dash instead of bash (might shave off up to a second, tops)
reprofile the boot sequence when you're done, to do so, in the grub menu at boot, hit e (for edit), and add the world "profile" to the end of the kernel line. You only need to do this once. (can make a world of difference in the boot time)

These are the things that will make the most difference, in my experience. As per disabling services, I suppose that save me about 2-5 seconds, not sure really. I just did a server install, followed by installing kde-core(you could use gnome-core instead) so I wouldn't have to have those services installed in the first place, because I didn't know what so many of them were, and even after disabling them it seemed like some of them still wanted to appear on boot. It's weird nonetheless. Oh, and unless you've got a fair grasp on what you're doing, don't attempt the server install. (I figure you do, but I figured I'd say so anyway).

---

### Post by an.echte.trilingue on 2006-11-08
Its been my experience that you should never upgrade a system that works unless it is no longer supported.  You will have to go through the configuration headaches all over again, and there is no guarantee that the new system will work.  Meanwhile, all of the new stuff you probably want, like the newest version of firefox or gnome, you can just install with backports.

I only upgrade if it might fix something that is broken (like suspend support).

I hope your troubles are resolved soon.

Take care

-mat

---

### Post by fabertawe on 2006-11-08
> **kuja said:**
> Lets see here, how to shave time off the boot:
Use the XFS filesystem(takes about a second less to mount than xfs, and well, a lot compared to reiser.... I think my boot time using reiserfs in edgy was around 30 seconds)
Only mount the needed filesystems on boot
have no cds in the drives(they add on about 3 seconds a piece)
disable usplash in /boot/grub/menu.lst (saves about 2 seconds)
It's default in edgy, but make sure /bin/sh points to dash instead of bash (might shave off up to a second, tops)
reprofile the boot sequence when you're done, to do so, in the grub menu at boot, hit e (for edit), and add the world "profile" to the end of the kernel line. You only need to do this once. (can make a world of difference in the boot time)

Thanks for the pointers. What are the differences between dash and bash? I'd reprofiled under Dapper but didn't think it was needed on Edgy because of readahead (or so I'd read). I'll try it again though.

> These are the things that will make the most difference, in my experience. As per disabling services, I suppose that save me about 2-5 seconds, not sure really. I just did a server install, followed by installing kde-core(you could use gnome-core instead) so I wouldn't have to have those services installed in the first place, because I didn't know what so many of them were, and even after disabling them it seemed like some of them still wanted to appear on boot. It's weird nonetheless. Oh, and unless you've got a fair grasp on what you're doing, don't attempt the server install. (I figure you do, but I figured I'd say so anyway).

Well I don't have that fair a grasp so I'll not attempt this (just yet)! I still can't believe you've shaved that much off, it's incredible!

Thanks ... Paul

---

### Post by kuja on 2006-11-08
> **fabertawe said:**
> Thanks for the pointers. What are the differences between dash and bash? I'd reprofiled under Dapper but didn't think it was needed on Edgy because of readahead (or so I'd read). I'll try it again though.



Well I don't have that fair a grasp so I'll not attempt this (just yet)! I still can't believe you've shaved that much off, it's incredible!

Thanks ... Paul
You're welcome.

Dash is the debian almquist shell. It's much smaller than bash. (the bourne again shell) It also executes scripts somewhat faster.

Readahead is a package installed and enabled in both dapper and edgy, but reprofiling it is neccessary, otherwise you're using the maintainers profile, which likely won't provide you with any advantage at all, and, as far as I understand, may even slow down the bootup process.

---

### Post by pony-tail on 2006-11-08
I did not upgrade to put "Edgy" on I clean installed . I have had major problems with all 3 installs (2 x 32bit and 1 x64) all have been related to xorg7.1 and AIGLX - I am wondering did they actually test this before they released it (or mayby just on nVidia cards) .It is definately NOT faster on ANY of my machines (AMD XP - Intel P4 - AMD 64x2 - Intel core 2 Duo ) .The Core2 machine is flakey on all distroes I have tried (I think it is because the 975 chipset is a little new (the machine is 2 weeks old)) - so no surprises there . Honestly it would be hard for me to be more dissatisfied with a Distro than I am with "Edgy" I went to file bug reports but they had already been filed at least weeks before "Edgy" shipped and still are in the final release . I guess I will have to wait six months for "Feisty" to see the bugs fixed . "Dapper" did not give me anywhere near this much grief ! All the machines above have been Reinstalled with "Dapper" the i975/core2 machine has a half borked SuSE64 10.2  install (xorg issues again)

---

### Post by mcglnx on 2006-11-08
> **fabertawe said:**
> Edgy is supposedly faster or snappier but I haven't noticed much difference. It certainly doesn't boot any faster as I have seen claimed many times. Saying that it is certainly not slower, at all.

My upgrade went great. Maybe you will have to stick with Dapper until Edgy has some updates and then try again.

Paul


Same experience! I did not notice any speed improvement. Mya be I missed something?

M.

---

### Post by killkoy on 2006-11-08
> **kopilo said:**
> It's a bit hard to explain basically when I went to scroll down a page it was very choopy, like the whole page would re-render (each render taking around 600 milliseconds) on a new position on the scroll bar.

I got this when i was using the vesa display drivers. don't have it now that i am using card specific drivers

---

### Post by kopilo on 2006-11-09
> **kuja said:**
> At which section did your install hang? Oftentime when that happens it means the cd is corrupt. Did you check the integrity of the disk before installing with it? That can save headaches, seeing as even if you complete an install with a corrupted disk it will give you trouble later (ie: uninstalled packages, perhaps limitted functionality or crashes in the installer, etc). 

The rendering problems, plus the lack of smoothness with glxgears are linked to each other. That's a video driver problem.

I did my install a bit different this time. I did a server install, then installed kde-core along with the things I needed. My bootchart is 18seconds :D All in all, it's probably about the same speed as Dapper. (I hear that Edgy boots faster on exceptionally slow machines, but otherwise doesn't make much difference.)
It hung at installing the ubnutu-desktop of the (I think it was) software step... I even went back and had it connect to the repositories for my country but it still failed.

I also did a disc check off the CD before trying to install.

I knew I should have pushed for an Nvidia card when my sis and I built this comp... Ohh well.

---

### Post by skullcorp on 2006-11-09
> **kopilo said:**
> It's a bit hard to explain basically when I went to scroll down a page it was very choopy, like the whole page would re-render (each render taking around 600 milliseconds) on a new position on the scroll bar.

[QUOTE=killkoy;1732850]I got this when i was using the vesa display drivers. don't have it now that i am using card specific drivers
[/QUOTE]

Same.  Just did a 64bit and a 32bit install and they both set me up with default vesa for video; installed the latest nvidia drivers and everything is smooth as can be now.

---

### Post by kopilo on 2006-11-09
Hmm, maybe I should find a way to install the ATI (Radeon 9200 se) drivers in Edgy and then try upgrading again.

---

