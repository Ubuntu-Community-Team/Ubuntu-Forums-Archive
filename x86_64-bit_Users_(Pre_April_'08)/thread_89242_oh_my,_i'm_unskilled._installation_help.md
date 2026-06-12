---
title: "oh my, i'm unskilled. installation help?"
date: 2005-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by telegraphmelts on 2005-11-12
Hello everyone!

A friend of mine burned me an ubuntu live cd and I more than liked what I saw. 

Recently another friend gave me a 1999 iMac with 266 mhz G3, and so I figured I might as well make Ubuntu its primary OS. I tested the live cd on the machine and it works perfectly.

I went to this page ([http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)) and downloaded and burned both the hoary and the breezy editions of Ubuntu, mounted the disk image in OSX, copied the files within to a blank cd, and burned. I then took the cd, put it in my iMac, and tried to boot from them (since am under the assumption that in order to install it as my main OS, I would probably have to boot from the cd). 

Well, nothing happened with both attempts. It simply went right into Mac OS 8.5 without even acknowledging my attempts by either holding the "c" key during startup or by holding the command+option+shift+delete keys during startup. 

I know I'm doing something wrong, and I know it's probably something painfully simple, but I just can't figure out what the problem is. 

If anyone can helpe me out, guide me a little bit here, it would be infinitely appreciated.

Thank you!

---

### Post by skeporang on 2005-11-12
You need to burn the iso in its entirety to a CD, not just copy the files within: it contains hidden data which the computer uses to boot from the CD.

Take a look @ [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

or google for "burning iso images mac os" or similar.

---

### Post by teaker1s on 2005-11-12
also the motherboard bios settings will need altering to boot from cd and on old motherboards you need to boot from a floppy to get cdrom support.

---

