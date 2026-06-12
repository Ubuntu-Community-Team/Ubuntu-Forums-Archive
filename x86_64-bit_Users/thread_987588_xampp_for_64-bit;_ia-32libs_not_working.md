---
title: "xampp for 64-bit; ia-32libs not working"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by tiercel on 2008-11-19
So... I'm trying to install XAMPP for Linux on Ubuntu 8.10 (Server, but I installed Desktop on top of it as well).

I'd like to run XAMPP out of its own partition (so I can keep the entire web service etc separate from the root partition).  So I just unpacked the tarball into /server (its own partition), and following the advice of other threads, used apt-get to install ia32-libs.  When I try to run 

sudo /server/lampp/lampp start

I still get the error "XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system."

Is this because I didn't put XAMPP into /opt?  Is there some way I can link in the 32-bit libraries to XAMPP?  (It's a tarball, not a .deb/.rpm package.)

I tried ldd on the lampp executable but it just returned that it's not a dynamic executable, so I assume that has something to do with it.  I'm just stumped because others here seem to indicate that merely installing ia32-libs was enough to get XAMPP working for them.

Thanks!

---

### Post by cariboo on 2008-11-19
I not sure what you are trying to accomplish by using a seperate partition, but you can aacomplis the same thing by putting /var on a separate partion and installjng the Lamp server which is 64bit natively and much easier to maintain.

Jim

---

### Post by rakiabr on 2009-04-02
type this in terminal:

sudo apt-get update

sudo apt-get install ia32-libs

---

### Post by moissi on 2009-06-26
After installing the last update today, my xampp is not working
The message is
XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

I've tried to solve the problem with
apt-get install ia32-libs
which is installed

and xampp send always the same error message

---

### Post by moissi on 2009-06-26
In the previous post, please read:
after installing the last update of ubuntu 64 bits (is that always Intrepid?)
...

---

### Post by Yellow Pasque on 2009-06-27
Try: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

