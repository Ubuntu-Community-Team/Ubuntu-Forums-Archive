---
title: "[SOLVED] If I want a new usplash, does it have to be 64 bit. One I want says i386"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by philinux on 2008-05-28
Does it matter?

I dont want to mess my boot up.

[Edit] the one I wanted was an alpha so when I chose the stable one I was offered a 64 bit version

Not solved.

---

### Post by pixel :-) on 2008-05-28
A usplash is a png image, translated to C code and a few functions for drawing.So i would say yes,it maters.

Try installing the source pakage if there is one.Anable source packages in your repozitories and try to install it.At my knoledge this can be done only with the command line(apt-get).

//installs whats needed,sudo mandatory
sudo apt-get build-dep package
//downloads and builds the pakage,don't use sudo so that you become the woner of the file
apt-get -b source packagename
//install the .deb that was created
sudo dpkg -i packagename.deb
//update the system
sudo update-alternatives --config pakagename.so
//update the ram disk
sudo update-initramfs -u

hope it helps.

[Edit] Whell,this should help you in the future

---

### Post by philinux on 2008-05-28
Ok I'm using startupmanager.

I put the 64 bit version of the so file in usplash folder and sum picks it up. But it never gets configured. Reverts back to default.

---

### Post by Kilz on 2008-05-28
I have installed usplash packages without looking to see what they are. But if the package says its i386, it may be that package is dependent in the 32bit architecture.

---

### Post by philinux on 2008-05-28
I've copied another 64 bit usplash theme chrome-theme.so into /usr/lib/usplash and startupmanager recognises it as an option. I choose it close sum.

Reopen sum and it's back to the default again. Arrrggghhh

---

### Post by pixel :-) on 2008-05-28
try the manual method for now
sudo dpkg -i packagename.deb
//update the system
sudo update-alternatives --config pakagename.so
//update the ram disk
sudo update-initramfs -u

@Kilz
It's a image tranclated in C, and compiled with some extra fonctions.It's not just an image.

---

### Post by philinux on 2008-05-28
> **pixel :-) said:**
> try the manual method for now
sudo dpkg -i packagename.deb
//update the system
sudo update-alternatives --config pakagename.so
//update the ram disk
sudo update-initramfs -u
.

I aint got a .deb only a chrome-theme.so file, well there are 4 .so files in /use/lib/usplash to choose from now.

The latest one did not offer an i386 or amd64 version just the .so file. That wont install via sum either.

---

### Post by pixel :-) on 2008-05-28
.so it's a library, it's a binary.Where you find it,if it doesn't say any thing, chances are good that it's 32bit.

Where did you find it?

you can try

sudo update-alternatives --config pakagename.so
//update the ram disk
sudo update-initramfs -u

but is it 64 bit.Don't try it if your not.

---

### Post by philinux on 2008-05-28
> **pixel :-) said:**
> .so it's a library, it's a binary.Where you find it,if it doesn't say any thing, chances are good that it's 32bit.

Where did you find it?

you can try

sudo update-alternatives --config pakagename.so
//update the ram disk
sudo update-initramfs -u

but is it 64 bit.Don't try it if your not.

There are loads on [http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by philinux on 2008-05-28
sudo update-alternatives --config usplash-theme-ubuntu
No alternatives for usplash-theme-ubuntu.

edit

sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

---

### Post by philinux on 2008-05-28
Solved as far as the thread title goes.

---

### Post by pixel :-) on 2008-05-29
I suspect that it's 32bit, and thats why it doesn't work.i think you will have better luck asking your question **at the forum of the particular usplash** for clarifications.

Try compilling from source.I couldn't find a tarball for most of what i clicked.I think that the image IS the source,you can use the image provided to make the usplash.

[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

---

### Post by philinux on 2008-05-29
Not due to 64 or 32 bit.

[http://ubuntuforums.org/showthread.php?t=810981](http://ubuntuforums.org/showthread.php?t=810981)

---

