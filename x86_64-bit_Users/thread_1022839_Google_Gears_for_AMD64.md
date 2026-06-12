---
title: "Google Gears for AMD64?"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by indiapavan on 2008-12-27
I am using the 64-bit version of the Hardy Heron release and I wanted to install Google gears to simplify my blogging. But I was very disappointed when the installer said that it could not be installed on a 64-bit OS. Is there anything I can do about it? If so, please help me.:confused:

---

### Post by Rog-Mahal on 2008-12-27
Someone ported an older version of Gears, you can find install instructions [here.]("http://www.techrecipes.net/linux/google-gears-in-64-bit-linux.html") I can verify that it installs correctly, but I never used it very much, and you will get errors about it being unable to update. It's the closest I've found to 64 bit Gears.

---

### Post by indiapavan on 2008-12-28
So does that mean 64-bit OS is not as good as 32-bit when it comes to software support?

---

### Post by downhillgames on 2008-12-28
> **indiapavan said:**
> So does that mean 64-bit OS is not as good as 32-bit when it comes to software support?
Depends, really. For example, Adobe Reader is 32-bit only, as well as a few other apps. 64-bit Flash and Java are coming, so THAT'S a big relief. *shrug* Generally speaking, 64-bit support is just as good as 32-bit these days, with only a few niche apps not capable of running on a 64-bit OS.

Honestly, it just comes down to if you use or might want to use those few niche apps or not.

HTH,
-Downhill

Oh yeah, there are also some compatibility libraries in the repos, but not nearly like Fedora where you pretty much end up with double your OS installed just to run a few random 32-bit apps. It becomes massive overhead, so don't expect a 32-bit compat. library for everything :) Just for important stuff like drivers, et al.

---

### Post by hyperdude111 on 2008-12-28
You can install the 32bit libs to allow you to install the 32 bit apps under 64 bit.

the code is " sudo apt-get -V install ia32-libs "

~Hyper~

---

### Post by Rog-Mahal on 2008-12-28
I would also be patient. I'm sure some enterprising code monkey will give us a 64 bit Linux .xpi for Gears that actually updates.

---

### Post by portis on 2008-12-28
You can find 64bit precompiled plugin here: 

[http://dev.laptop.org/~joel/gears/]("http://dev.laptop.org/~joel/gears/")

---

### Post by Frak on 2008-12-28
With us already having 64-bit Flash and 64-bit Java with a 64-bit web plugin, I can only say a few bugs still remain. Though, I bet there's a gears repo somewhere.

EDIT
Hey, I was right.

---

### Post by jaduncan on 2009-02-03
I have put up a working 64 bit binary for the most recent Gears as of 02/02/09 and the legacy versions at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

---

### Post by sportsdude81 on 2009-08-17
> **jaduncan said:**
> I have put up a working 64 bit binary for the most recent Gears as of 02/02/09 and the legacy versions at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

Why 4 GB?

---

