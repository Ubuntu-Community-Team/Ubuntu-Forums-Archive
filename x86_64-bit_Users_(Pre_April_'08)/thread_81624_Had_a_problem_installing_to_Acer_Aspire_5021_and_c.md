---
title: "Had a problem installing to Acer Aspire 5021 and could use some advice now"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by wit_ on 2005-10-24
Hey :)

I just installed the Ubuntu 5.10 to my Acer Aspire 5021 WLMi laptop today.
For information if needed;

AMD Turion ML28
512 MB DDR
80 GB HDD
15,4" widescreen
RADEON Xpress 200 chipset
X700 / 128 MB

And the problem.

I tried to install the system 5 times, and it always hang up at some point of copying files from CD to HD, or when installing the base system.
and this was not due to broken install media, because te hangs occurred in different states of install.

I tried to install it in expert mode, and with basic install, and neither of them worked. It always just hanged, at one point I gave it almost 2 hours to proceed but nothing happened, that's when I hit CTRL+ALT+DEL :|

In between of every install, I re-made the partitions and formatted them so the allready copied data would not corrupt the new install.

so, after toying for hours and hours, I finally got it to install.
with the server install option.

And now, I don't have graphics on my system or much of anything else either.

so now I could use some advice on how I should proceed and what would be the smartest way to install Gnome and such to my system.

Can this be done with apt-get?

I have never used a Debian system before, Suse and redhat to some extend so I'm not familiar with this system. If someone could help me with a little kick-start to upgrading the system to serve as a fully functional laptop, I would appreciate it very much :)

---

### Post by RAOF on 2005-10-24
The best way to proceed would be to install the ubuntu-desktop package.  That brings in all of the standard install.  If you've got an internet connection, just run "sudo apt-get install ubuntu-desktop", and wait :)

---

### Post by wit_ on 2005-10-25
Ok, that sounds like a good plan!

Does that command upgrade the missing parts to the allready installed system? I'm just a bit worried since it didn't isntall from the cd...

But maybe that will do the trick! :)

thanks!

---

### Post by RAOF on 2005-10-25
That will add all the missing parts, and update anything that's been updated since you downloaded the install image.  I think it's actually likely that the problem **was** your install cd - during development, it seemed that more than half of install problems were solved by people burning the install image at a lower speed.  Really.

---

### Post by wit_ on 2005-10-25
Thank you very much, that did the trick and now I'm typing the message on my new Ubuntu laptop setup :)

Now the only problem I have to this point is that my screen is at 1024x768, when the native resolution is 1280x800 :|

When I go to System-Settings-display (or something like that, I have it in finnish), the only resolutions it gives me are 1024x768 , 800x600 and 640x480.

during the installation, it asked me something about display setup, and I marked the 1280x800 because I thought it was asking for my default resolution, but Now I'm afraid it asked me what resolutions not to include :oops: 

So any suggestions where I could get that setup program up again and change the resolution, cause this looks really crappy now? :D

Thanks!

---

### Post by wit_ on 2005-10-25
Ok, now I have the native resolution, I reconfigured the whole X and got it from there :)

So much tweaking to do, so little time... ;)

---

