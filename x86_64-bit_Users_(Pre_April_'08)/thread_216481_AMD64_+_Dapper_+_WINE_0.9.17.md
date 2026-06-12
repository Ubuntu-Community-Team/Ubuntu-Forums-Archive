---
title: "AMD64 + Dapper + WINE 0.9.17???"
date: 2006-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by amcquown on 2006-07-15
I'm a 100% n00b to linux (took me four hours to just decide on using ReiserFS for my FS during install!) and I need some severe help installing WINE 0.9.17 on my AMD64!

I have the 0.9.17 tar.bz2 extracted onto my desktop - Can anyone give me a step-by-step in the terminal on how to get this working, and are there any other packages I'd need in order for WINE to run properly?

---

### Post by synacktion on 2006-07-15
Unless you absolutely have to have a 64 bit binary, you could just apt-get wine and it will get the 32 bit version and all the dependencies for you. You'll also have to enable the universe repository.

Otherwise, you will need to acquire these dependencies and compile everything.  Let me know if you want help with that.

EDIT: Sorry but apparently the 32 bit wine causes some troubles - I just noticed the following thread that might help:

[http://www.ubuntuforums.org/showthread.php?t=185557]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by amcquown on 2006-07-15
I tried that link before even posting, and none of it seems to work. Sadly Synaptic will not 100% accept the repositories I was told to input in order to get wine. Arrrgh - guess I should've just installed 6.06 32-bit :( Talk about slight disappointment.

---

### Post by Kilz on 2006-07-15
> **amcquown said:**
> I tried that link before even posting, and none of it seems to work. Sadly Synaptic will not 100% accept the repositories I was told to input in order to get wine. Arrrgh - guess I should've just installed 6.06 32-bit :( Talk about slight disappointment.

No matter what version you install there is always something that needs a little extra work to get installed. [My howto has worked for a lot of people, you may want to give it another try.]("http://www.ubuntuforums.org/showthread.php?t=185557") If you cant follow the howto the automated setup scripts at the top of the page may be better for you.

---

### Post by PisstMSTRCHIEF on 2006-07-15
I managed to get it install with your great howto:)   

What I did was not take the additional steps, follow it word for word and copy/past the codes in the terminal. Up to the code, as stated in the tutorial you have to change some numbers, for 0.9.17 try copying and pasting this in the terminal:

sudo cp ~/Desktop/usr/lib/* /usr/lib32
cd ~/Desktop
sudo dpkg --force-architecture -i wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb

Post back with results

---

