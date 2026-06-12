---
title: "helping a newbie out with wifi issues on an hpzv5000"
date: 2005-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by grayskies on 2005-08-04
okay, found my first big hurdle...im running an amd64 system...i cant get ndiswrapper 1.2 to install,

i keep getting the same errors dealing with amd64 / i386 incompatability. DOH
following the instructions @SetupNdiswrapperHowto on the ubuntu wiki

I start getting issues at about here
"
4. Untar the ndiswrapper-1.1.tar.gz file to your /usr/src directory. NOTE: the location where you untar the source doesn't really matter, but the rest of these instructions will assume /usr/src.

cd /usr/src
tar xvzf ~/ndiswrapper-1.1.tar.gz

5. By default, the rules file that is responsible for specifying Debian packaging parameters specifies an install directory different from where Ubuntu keeps the same module. I adjusted by rules file to install in the proper place like so

cd /usr/src/ndiswrapper-1.1
sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp
mv debian/temp debian/rules

6. Enter the source directory and issue the make deb command.

cd /usr/src/ndiswrapper-1.1/
make deb

7. In your /usr/src directory, if all went well, you should find two brand new .deb package files. Let's install them, overwriting the modules that came with Hoary that don't work for us.

cd /usr/src
dpkg -i --force-overwrite ndiswrapper-utils_1.1-1_i386.deb
dpkg -i --force-overwrite ndiswrapper-modules-$(uname -r)_1.1-1_i386.deb
"

first off, when i execute tar, it gives me some random error so i just decompressed with archive manager (built-in)

then step 5 goes fine, and i get to the "make deb" command...
gives me an amd64 / i386 compatability error. dunno what to do with that...ive only used HP-UNIX / MacOS / Windows before, so this is all kind of foreign.

dpkg doesnt execute at all, another random error.

I'm running linux-k8 kernel, not generic for Ubuntu.
custom install "linux noacpi"

thanks a million,
adam

---

### Post by grayskies on 2005-08-04
okay, well after looking over these forums, i guess im pretty screwed when it comes to starting off with linux with an amd64 system...


am i completely screwed with wireless or should i experiment with the chroot ive been reading about 


am i just going to have a steep learning curve?  i guess what doesnt kill me will just make me stronger.

---

