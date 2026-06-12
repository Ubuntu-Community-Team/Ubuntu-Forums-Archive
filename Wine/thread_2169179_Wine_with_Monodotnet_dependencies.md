---
title: "Wine with Mono/dotnet dependencies"
date: 2013-08-20
forum: Wine
---

### Post by psfal on 2013-08-20
I've been trying to get Wine to accept dotnet dependencies. I've tried 5 times with various wikis and had to reinstall my Ubuntu 12.04 2 times because they screwed my system up. I need to get 2 apps running that require dotnet20 and dotnet35sp1. What it's always come down to is the Mono/dotnets won't work on my 64bit system.

I installed UbuntuGNOME 13.04 32bit on another partition and still haven't been able to get it done, had to reinstall that once already too. There are no clear-cut instructions on this, and all the terminal command lines just keep on screwing up my system. I've dealt with the WineHQ forum too and they just confuse me.

It seems like an extremely ignorant way to make a Wine application when the dotnet dependencies are left out, making it absolutely useless for anything but running a Netflix desktop (2 lines and it's installed).

Is there an EASY way to make this work, either on the 32bit install or on a 64bit install? This doesn't seem to me to be something that should be so complicated, it is after all a "Windows Compatibility Layer". If it can't do windows compatibility, what good is it?

I am not a "nuts & bolts" Linux hacker, nor will I ever be, I am a Linux user who loves the way Linux works and, if not for these two apps I need for work, which I run currently on a VM running XP, all would be perfect in my world...

The assumption is made that I can run all these terminal command line instructions, but the fact is that I can't, I have no idea what they do, as with most computer users. talking down to me doesn't make me respect someone, it just makes them look like a snob. It's well to be proud of your accomplishments, but it doesn't make you any better a person than the next guy

No, I don't know how to "run this script" for mono

---

### Post by QIII on 2013-08-20
*Moved to** Wine.***

Hopefully this will get you some visibility with the right crowd.

Cheers!

---

### Post by psfal on 2013-08-20
Thank you :-)

---

### Post by Mark Phelps on 2013-08-21
Couple of aspects you're missing ...

First, "compatiblity" is not uniform across all Windows apps.  You can see this clearly by going to the WineHQ Application Compatibility website and doing a search for app and version you want to use.  You will see ratings ranging from Platinum (fully compatible -- everthing works) to Garbage (won't install or won't run).

Second, if you browse that site, you will see that apps dependent on other MS middleware for their operation (like .net or silverlight) do not perform well.

You should really check that site for the apps you're trying to run.  If they are not listed, or if their ratings are less than Gold, you're essentially wasting your time trying to get them to work.

---

### Post by psfal on 2013-08-22
@Mark Phelps
They're not standard apps, they're company specific apps, I have no idea if they'd run with mono 4.0 since I haven't been able to get it running.

---

