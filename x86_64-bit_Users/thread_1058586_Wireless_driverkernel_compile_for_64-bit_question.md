---
title: "Wireless driver/kernel compile for 64-bit question"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by MaindotC on 2009-02-03
I'd like to try the directions of the last post in [this thread](https://answers.launchpad.net/ubuntu/+question/45440).  I know very little about 64-bit vs 32-bit and yes I know there is a ton of documentation and I apologize for not having read all of it but I'd just like to ask my question and hope that you can answer it genuinely.

If I follow those instructions in the last post, will it make any difference that I'm using Hardy 64?

---

### Post by Yellow Pasque on 2009-02-03
It shouldn't, but if there is an issue with the driver not working with 64-bit, it will probably manifest itself with compile errors when you attempt to build the driver module.

Also note that ralink released a new driver version about a week after those directions were written, so the exact line numbers you have to edit may be a little different.

---

### Post by MaindotC on 2009-02-03
Forget it - I plugged in my WUSB600N last night because my [Belkin F5D7050](is.gd/ig6E) suddenly lost signal strength and it's been up for a full 24 hours!  I won't bother installing the driver as posted on launchpad.  Here's a [link I've been following](http://is.gd/igGM) on Linksysforums.  I included my package update history that may have fixed a library or header or something.

---

### Post by cariboo on 2009-02-03
No, the files should be compiled for 64bit.

Jim

---

### Post by MaindotC on 2009-02-03
Hey guys, thanks for all your help.  Until I become a developer and understand how to examine drivers I'll just have to be satisfied with falling backwards into luck.  Thank you all.

---

