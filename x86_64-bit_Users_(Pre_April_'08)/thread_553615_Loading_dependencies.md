---
title: "Loading: dependencies?"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by atomicdad on 2007-09-18
I've been trying to go through a couple of the tutorials for trying to get vmware going and to get the latest NVidia 8600GT graphics driver up and running.

the two different "how to's" start with a terminal command line as:

sudo apt-get install linux-headers-'uname -r' build-essential gcc gcc-3.4 xserver-xorg-dev

or

sudo apt-get install linux-headers-'uname -r' build-essential xinetd

each resulted in:
Reading Package lists ..... Done
Building Dependency tree
Reading state information .... Done
E:  Couldn't find package linux-headers-uname -r

I went back to the SPM and downloaded/installed pretty much everything that was labeled "linux-header..."

But no luck, still getting the same error. Any ideas out there????

---

### Post by Cappy on 2007-09-18
Either you didn't copy and paste or the person who wrote that wrote it wrong.
it isn't a ' it is a `

Copy and paste this into the terminal:
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```

---

### Post by saru411 on 2007-09-18
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

use envy. its the easiest way to install nvidia drivers. what could be simplier than point and click

:)

---

### Post by atomicdad on 2007-09-18
I ran envy last night, and got my NVidia driver updated. I tried running it previously when I had the 32 bit version running and it crashed and I didn't go back to it when I put on the 64bit version.

My bad, I didn't copy and paste, I typed the line in and as you caught, I used '  instead of `. I'll try to be more thorough before I put up questions in the future.

Thanks

---

