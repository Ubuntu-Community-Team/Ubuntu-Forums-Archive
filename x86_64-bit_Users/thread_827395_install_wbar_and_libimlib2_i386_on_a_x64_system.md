---
title: "install wbar and libimlib2 i386 on a x64 system"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by franciccio on 2008-06-12
hi all, i'm running xubuntu hardy x64 and i'm trying to use wbar (32bit) that needs libimlib2. i've downloaded the package libimlib2_1.4.0-1ubuntu1_i386.deb from packages.ubuntu.com then unpacked it and copyed the files from it's relative directory usr/lib to my absolute /usr/lib32/ path.
wbar stopped give me the "wrong ELF class: ELFCLASS64" error for imlib2 and returned with that:
"/usr/share/wbar/wbar.icons/osxbarback.png -> Image not found. Maybe using a relative path?"
obviously that file is there and have all the needed permission, i've googled and i found someone that solved that problem reinstalling just the libimlib2 package (in a 32bit system though), so i assume that tha problem is in my unclean "installation" of imlib2.
...any suggestion?
thanks in advance :)

---

### Post by Cappy on 2008-06-13
Have you installed the 64-bit libimlib2 yet?
```
sudo apt-get install libimlib2
```

Have you checked the wbar's configuration file /usr/share/wbar/dot.wbar

I downloaded wbar from [http://code.google.com/p/wbar/downloads/list](http://code.google.com/p/wbar/downloads/list) (installed using dpkg --force-all package_name.deb)
and my path to osxbarback is /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
Is it possible you have an older version?

If you exhaust all other possibilities, you can have getlibs reinstall the 32-bit library for you: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
with
```
sudo getlibs -p libimlib2
```

---

### Post by franciccio on 2008-06-14
> **Cappy said:**
> Have you installed the 64-bit libimlib2 yet?
```
sudo apt-get install libimlib2
```

Have you checked the wbar's configuration file /usr/share/wbar/dot.wbar

I downloaded wbar from [http://code.google.com/p/wbar/downloads/list](http://code.google.com/p/wbar/downloads/list) (installed using dpkg --force-all package_name.deb)
and my path to osxbarback is /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
Is it possible you have an older version?

If you exhaust all other possibilities, you can have getlibs reinstall the 32-bit library for you: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
with
```
sudo getlibs -p libimlib2
```

hi, thank you for reply.
yeah, the 64-bit libimlib2 package is cleanly installed.
the path in the error is the same as yours
(I was wrong pasting down the error that I've copyed from a web page cause when i posted the topic i wasnt at home and i couldnt reproduce the error... sorry, me bad).
in fact the package i installed was wbar_1.3.3_i386.deb from the google code site with dpkg --force-architecture exactly as you've done.

I've tryed installing the i386 libimlib2 package using getlibs but nothing is changed. (great tool though, thnx for the suggestion)
I solved, downloading the source package wbar-1.3.3.tbz2 and compiling it.
so i hink that the problem wasn't in the clean or unclean installation of the libimlib2 i386 package but in the wbar package.

with the libimlib2 i386 and 64bit packages installed from official repositories i can reproduce the problem reinstalling the wbar .deb pkg.
so i would like to post the problem to the issue page of the project home.
can you tell me if you done something different from me to have wbar work on your 64bit system? and in case, are you running pure ubunutu?

---

### Post by Cappy on 2008-06-16
Sorry; I've been on my 32-bit only ubuntu laptop lately.

Here's the fix:
> 
sudo ln -s /usr/lib32 /usr/l32; sudo sed -i -e 's+/usr/lib+/usr/l32+g' /usr/lib32/libImlib2.so.1


libImlib2.so.1 has a hardcoded path to /usr/lib32 so the binary just needs to be changed

---

### Post by thedinga on 2009-06-29
> **franciccio said:**
> hi all, i'm running xubuntu hardy x64 and i'm trying to use wbar (32bit) that needs libimlib2. i've downloaded the package libimlib2_1.4.0-1ubuntu1_i386.deb from packages.ubuntu.com then unpacked it and copyed the files from it's relative directory usr/lib to my absolute /usr/lib32/ path.
wbar stopped give me the "wrong ELF class: ELFCLASS64" error for imlib2 and returned with that:
"/usr/share/wbar/wbar.icons/osxbarback.png -> Image not found. Maybe using a relative path?"
obviously that file is there and have all the needed permission, i've googled and i found someone that solved that problem reinstalling just the libimlib2 package (in a 32bit system though), so i assume that tha problem is in my unclean "installation" of imlib2.
...any suggestion?
thanks in advance :)

so i've run into the same error as well and was wondering what the fix was exactly? i'm pretty new to linux so i'm not quite putting together what you did to fix the problem...

---

### Post by danlaptic on 2009-09-20
> **Cappy said:**
> Sorry; I've been on my 32-bit only ubuntu laptop lately.

Here's the fix:

sudo ln -s /usr/lib32 /usr/l32; sudo sed -i -e 's+/usr/lib+/usr/l32+g' /usr/lib32/libImlib2.so.1 

libImlib2.so.1 has a hardcoded path to /usr/lib32 so the binary just needs to be changed

Yup, that worked for my 64-bit Jaunty, thanks alot!

---

