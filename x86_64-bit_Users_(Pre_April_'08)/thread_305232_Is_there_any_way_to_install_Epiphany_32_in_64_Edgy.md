---
title: "Is there any way to install Epiphany 32 in 64 Edgy"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by artik on 2006-11-23
Hello,
Is there any way to install 32bit Epiphany (like 32bit firefox) in Edgy. I want to use flash but npwarper doesn't work well (epiphany/and ff time to time gets to 100% CPU and then crashes).

So I want to use 32bit epiphany with flash?
Is there any way?

P.S.: I don't want and like FF - because of keyboard shutcuts that do not work in non latin layout.

---

### Post by Kilz on 2006-11-23
> **artik said:**
> Hello,
Is there any way to install 32bit Epiphany (like 32bit firefox) in Edgy. I want to use flash but npwarper doesn't work well (epiphany/and ff time to time gets to 100% CPU and then crashes).

So I want to use 32bit epiphany with flash?
Is there any way?

P.S.: I don't want and like FF - because of keyboard shutcuts that do not work in non latin layout.

All you should have to do is force architecture a 32bit package.

---

### Post by RAOF on 2006-11-23
> **Kilz said:**
> All you should have to do is force architecture a 32bit package.

...although that will replace your current Epiphany, and won't work because Epiphany depends on the firefox libraries.

The short answer is: No, you can't.

The longer answer: Yes, you can.  You'd want to have **ia32-libs-gtk** installed, and you'd need to manually download the i386 firefox packages from  [packages.ubuntu.com](packages.ubuntu.com).  

Then, you should manually extract all the libraries from those packages (using **dpkg --extract *package* *temporary_directory***), copy all the *.so files to /usr/lib32, then run "sudo ldconfig".  

Now, you can either install the 32bit Epiphany .deb using **sudo dpkg --install --force-architecture *package*** (which will replace your existing 64bit Epiphany), or extract the files from the deb as before, and mess around with copying the binaries to the right spots, with a different name.

Now, try running your new Epiphany from the command-line.  If it runs, cool.  If it doesn't, it will probably say: "cannot find shared library: *libfoo*".  This means you'll need to track down the package containing *libfoo*, and do the manual extraction of *.so files to /usr/lib32.  Rince and repeat, until Epiphany starts.

---

### Post by artik on 2006-11-26
> **RAOF said:**
> 
The short answer is: No, you can't.

The longer answer: Yes, you can.
Ok I see, it does not looks well.
So probably it will be better to create chroot and work with it.

Thanks!

---

