---
title: "Downgrade Xorg 1.6 to 1.5.3 so I can use fglrx drivers again?"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by googlegot on 2009-05-20
Does anyone know how to downgrade xorg from 1.6 to 1.5.3 so I can use my x850xt again?

---

### Post by googlegot on 2009-05-21
Just solved my own problem, to use fglrx drivers, I downloaded the recompiled xorg from this site

 [http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

and followed his instructions (very simple and easy, but if youre running x64 like me, drop the fglrx componants and compile them yourself from the ati x64 drivers)

Dont be an idiot like me and install these in init 1, I couldnt for the life of me figure out why hald wouldnt refresh...

---

### Post by ssri on 2009-05-21
How is Jaunty running on xserver 1.5.x stability-wise?

---

### Post by googlegot on 2009-05-21
> **ssri said:**
> How is Jaunty running on xserver 1.5.x stability-wise?

Its very stable, and frankly I'm amazed by this fact because I'm running the 32 bit version of xserver on a 64 bit box with 64 bit fglrx drivers (I don't really have the time to recompile the 64 bit version, and it seems to work ok)

Ill update you on the situation in a while, but so far no errors/crashes other than apt yelling at me to update the entire time.

---

### Post by ssri on 2009-05-22
> **googlegot said:**
> Its very stable, and frankly I'm amazed by this fact because I'm running the 32 bit version of xserver on a 64 bit box with 64 bit fglrx drivers (I don't really have the time to recompile the 64 bit version, and it seems to work ok)

Ill update you on the situation in a while, but so far no errors/crashes other than apt yelling at me to update the entire time.

Thanks for the update!  Interesting, I thought that there is a way to freeze apt from upgrading a particular package.  Like you, I mainly use apt-get to manage my packages.  Did you install getlibs and force installed the deb?  Considering how the dev described compiling it as being close to hellish, I will not hold it against you for not doing the same for x86_64 ;).  Please keep us informed with this positive development! :)

---

### Post by googlegot on 2009-05-28
> **ssri said:**
> Thanks for the update!  Interesting, I thought that there is a way to freeze apt from upgrading a particular package.  Like you, I mainly use apt-get to manage my packages.  Did you install getlibs and force installed the deb?  Considering how the dev described compiling it as being close to hellish, I will not hold it against you for not doing the same for x86_64 ;).  Please keep us informed with this positive development! :)

Again, I did this on a stock install, and the only difference is that I used the 64 bit fglrx drivers, thats it.

It was stable for the 14ish days straight I had it running, until an unrelated problem caused enough issues to make me reinstall (this time I just used intrepid).

---

### Post by Sepero on 2009-09-22
This guide allowed me to easily downgrade Xorg and get this problem solved:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

