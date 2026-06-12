---
title: "HOWTO: DVD/CD Burning with Nero - [Outdated]"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bender NZ on 2005-10-30
Saw that there was no clear message about DVD burning for those who have DVD burners that don't get along with growisofs/cdrecord (I got massive buffer underruns etc)

NeroLINUX, while commercial, has proprietary drivers which seem to have very good support (given they have time and money to focus on these things) and is well worth trying.

To install on amd64 - they say it is not supported, but I forced it and it has no errors at all with Breezy.

Go to: [http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html) and download the deb trial version.

Run the command:
```

sudo dpkg --force-architecture -i nerolinux-2.0.0.3b-x86.deb

```

Then simply run 'nero' at the command line. You can add it into your Gnome/KDE menus at your own leisure.

The trial version does expire eventually and you will need to buy it, though given I have no other choice as growisofs doesn't work properly with my burner it is worth the USD19.95.

---

### Post by bsmith1051 on 2006-05-05
sweet, this worked immediately.  No need to look for other packages?  Thank you!

---

### Post by MetalMusicAddict on 2006-05-05
Cool. Though I do love K3B I would buy Nero for Linux if it supported all the things it does on the windows side. ;)

---

### Post by supanigga on 2007-09-25
Very cool neroLinux, too bad isn't free :twisted:

Any new app better them nero?

---

### Post by crjackson on 2007-09-25
> **Bender NZ said:**
> Saw that there was no clear message about DVD burning for those who have DVD burners that don't get along with growisofs/cdrecord (I got massive buffer underruns etc)

NeroLINUX, while commercial, has proprietary drivers which seem to have very good support (given they have time and money to focus on these things) and is well worth trying.

To install on amd64 - they say it is not supported, but I forced it and it has no errors at all with Breezy.

Go to: [http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html) and download the deb trial version.

Run the command:
```

sudo dpkg --force-architecture -i nerolinux-2.0.0.3b-x86.deb

```

Then simply run 'nero' at the command line. You can add it into your Gnome/KDE menus at your own leisure.

The trial version does expire eventually and you will need to buy it, though given I have no other choice as growisofs doesn't work properly with my burner it is worth the USD19.95.

I don't know why you had to force architecture.  There is a 64-bit deb on the site.  I own a license to this version and it works just fine.  You can download either 32-bit or 64 bit
[SIZE="3"]**_[nerolinux-3.0.1.3-x86_64.deb]("http://www.nero.com/eng/nerolinux-prog.php?pak=18")_**[/SIZE]

---

### Post by crjackson on 2007-09-25
> **supanigga said:**
> Very cool neroLinux, too bad isn't free :twisted:

Any new app better them nero?

K3B

---

### Post by pannerrammer on 2007-11-24
Thanks crjackson. 

If you go for the trial you get the option of downloading either the 32 or 64 bit version.  But if you buy Nero the shop 'download' button sends you the 32 bit version - no choice. 

Also I tried the --force-architecture command line method with the i386 version (3.0.0.0) and it didn't work for me

---

### Post by WiFi Ed on 2007-11-24
I've used the Nero product (the 32bit AND the 64bit versions). I purchased the 32bit version and received the product key by email.

After switching to 64bit Ubuntu I downloaded the 64bit trial version of Nero and the product key I received with the 32bit version works with the 64bit version.:)

Download and install the 64bit version. On first run, it asks for some info (user name, business name, product key). By default, the trial version product key is displayed in the box. I entered the 32bit version product key instead and now it is a fully functional, non-expiring application...

---

### Post by Perfect Storm on 2007-11-24
Closing thread - as it's not relevant anymore.

---

