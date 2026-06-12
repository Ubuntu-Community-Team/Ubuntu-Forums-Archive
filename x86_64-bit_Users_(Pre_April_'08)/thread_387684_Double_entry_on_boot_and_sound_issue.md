---
title: "Double entry on boot and sound issue"
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doz3r on 2007-03-18
Hi :D.

Firstly, I'm running edgy 64-bit install.
I needed to re-install xp two days ago, so I decided to get an ubuntu dual boot set up. I've messed about with a few versions of linux but was pretty excited about ubuntu, especially as I can have a 64bit os for free!

Anyway, I've managed to get my xpress 1100 working, and flash working in firefox, and dvd's to play all from previous posts.

I only have two remaining issues I'd like help with if anyone can help please as I can't find any information on this.

Firstly, as I mention I dual boot to xp, but at boot the line "Ubuntu, kernel 2.6.17 -11 generic" and the safemode boot lines are both displayed twice. Anyway I can have just the one line display for each?

Secondly, the onboard laptop sound wouldn't work, which I managed to get going with alsamixer. My only issue now is that the on board speakers don't turn off when I plug in the headphone jack. Anyway to sort this?

Thanks for your time, I've resolved loads of problems with previous posts, I just couldn't find anything for this.

Cheers!

---

### Post by dfreer on 2007-03-19
> Firstly, as I mention I dual boot to xp, but at boot the line "Ubuntu, kernel 2.6.17 -11 generic" and the safemode boot lines are both displayed twice. Anyway I can have just the one line display for each?

Check and see if /boot/grub/menu.lst has the same entry listed twice. If it does, BACKUP your menu.lst file and then delete the extra entry. It may be a bug that posts the same menu entry twice, however note that whenever you upgrade to a new kernel it will keep the original kernel installed on your system (in case their is problems with the new kernel). For example I have kernels 2.6.20-11, 2.6.20-10, 2.6.20-9, 2.6.17-11, 2.6.17-10. In this case if you *really* only want one kernel option available to you at boot,  look for this line:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
**[B]# howmany=all**[/B]

```
And then replace it with this one:
```
howmany=1
```
You should probably read the comments in the menu.lst file, they help alot :)

> Secondly, the onboard laptop sound wouldn't work, which I managed to get going with alsamixer. My only issue now is that the on board speakers don't turn off when I plug in the headphone jack. Anyway to sort this?

There has been problem's with the headphone detection in the kernel, this shouldn't be a problem in Feisty. For now, try just hitting the mute button twice (mute and then unmute), it *should* only play in your headphones now. Note you may have to mute/unmute again when you unplug your headphones...

---

### Post by Doz3r on 2007-03-19
You're a hero. Thank you, fixed fine :).

Looks like my only problem now is just a small kernel bug :-D. Thank you again. I'm struggling to get myself to boot the windows install to get that how I like it. Having too much fun in ubuntu!

Thanks again!

---

### Post by dfreer on 2007-03-19
Your welcome :) Ubuntu rocks!

---

