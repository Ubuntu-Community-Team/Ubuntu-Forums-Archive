---
title: "Can 64-bit Ubuntu run 32-bit programs?"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sunnz on 2007-09-30
Hi I am running 32-bit version of Ubuntu right now, its been fine.

But however I will be running 4 GiB of RAM for Xmas soon, and the easiest way to take advantage over it is to use a 64-bit OS.

Now the question is, some of the software I need to run the 32-bit version, such as Firefox 32-bit for Flash, MPlayer 32-bit for w32codec, perhaps VMware. How easy is it to install such software under 64-bit version of Ubuntu?

I kinda know it can be done, when I used Gentoo sometime ago they pretty much have all the "essential" 32-bit software pre-compiled and can be easily installed in a 64-bit Linux, so I am wondering what is the state of 32-bit support for 64-bit Ubuntu is like.

Thanks.

---

### Post by miggols99 on 2007-09-30
There are some scripts hanging around in the 64bit forum...nspluginwrapper lets you use 32bit plugins in a 64bit browser. The codecs can be installed quite easily...again just look around. As for VMWare, you could try Virtualbox, which runs natively on 64bit.

---

### Post by Kilz on 2007-09-30
> **Sunnz said:**
> Hi I am running 32-bit version of Ubuntu right now, its been fine.

But however I will be running 4 GiB of RAM for Xmas soon, and the easiest way to take advantage over it is to use a 64-bit OS.

Now the question is, some of the software I need to run the 32-bit version, such as Firefox 32-bit for Flash, MPlayer 32-bit for w32codec, perhaps VMware. How easy is it to install such software under 64-bit version of Ubuntu?

I kinda know it can be done, when I used Gentoo sometime ago they pretty much have all the "essential" 32-bit software pre-compiled and can be easily installed in a 64-bit Linux, so I am wondering what is the state of 32-bit support for 64-bit Ubuntu is like.

Thanks.

The simple answer is Yes it will. The longer answer is Yes it will, but you dont need to because there are 64bit versions of most everything. The Mplayer is a prime example. With the newest 64bit version you dont need the w32codecs to open wmv files.
The applications most people may want 32bit versions of can be counted on the fingers of one hand. Those all have howto's or scripts to install them.

---

### Post by Sunnz on 2007-09-30
Oh that's very nice to hear, that's a whole heap of 64-bit improvement since last time I try it!!

So how does the MPlayer stuff work? I don't have many WMV files, but I do have some rmvb (real media) files.

---

### Post by jamesford on 2007-09-30
im running vmware, works fine
wmw plays nicely in both vlc and totem. didnt try wmv in mplayer iirc
not sure about real media but presumeable real player can play them and ive got real palyer installed on my 64 bit feisty

---

### Post by Sunnz on 2007-10-10
So are 32-bit libraries installed in Ubuntu 7.10 by default?

Other distros like Gentoo, Fedora have 32-bit libraries installed in their respective 64-bit OS, making installing 32-bit software very easy.

---

### Post by Kilz on 2007-10-10
> **Sunnz said:**
> So are 32-bit libraries installed in Ubuntu 7.10 by default?

Other distros like Gentoo, Fedora have 32-bit libraries installed in their respective 64-bit OS, making installing 32-bit software very easy.

A few, very few. But you can install them all with apt/synaptic. The linux32 and ia32 packages could be installed with
```
sudo apt-get install linux32 ia32*
```
But for the most part these libraries are not needed, and the need is less and less with each version of Ubuntu. What 32bit applications are you wanting to install? If its mplayer, the 64bit version in the repos plays almost everything I have tried.

---

### Post by Sunnz on 2007-10-10
Well perhaps VMware. And it is always nice to know linux32 and ia32 packages exists should it is needed in the later on, thanks very much!!

---

### Post by Kilz on 2007-10-10
> **Sunnz said:**
> Well perhaps VMware. And it is always nice to know linux32 and ia32 packages exists should it is needed in the later on, thanks very much!!

Vmware, from what I remember , doesn't need any 32bit libraries. I installed it with the installer from vmware. But then again I know I had all the ia32 packages before trying.

---

### Post by Sunnz on 2007-11-01
> **Kilz said:**
> The simple answer is Yes it will. The longer answer is Yes it will, but you dont need to because there are 64bit versions of most everything. The Mplayer is a prime example. With the newest 64bit version you dont need the w32codecs to open wmv files.
The applications most people may want 32bit versions of can be counted on the fingers of one hand. Those all have howto's or scripts to install them.

Ok it turns out that I do need 32-bit version of MPlayer. w64codecs does not work with rmvb (rv40 codecs) files but it has worked in the past with w32codecs.

There are Google Summer of Code worked on free implementation on rv40 and rv30, they compiles and runs fine on my 64-bit system, it is great but it is still work in progress and not usable for watching movies.

So, may I ask where are the how-tos for installing 32-bit programs? Thanks you!!!

---

### Post by Saubazi on 2007-11-01
I haven't met a 32bit application that would not run - yet, not that I have many and with gutsy it is even better even with totem and stuff - I seem to be able to open email attachments and stuff with default apps - codecs are downloaded and they work.

Anyway I have some 32bit games and needed to get libs for them. I meticulously extracted them from 32bit debs and copied over to /usr/lib32 - However, I felt I lost track what I inserted there myself and what was there and got confused whether these libraries might change at sometime - so I created myself a chroot environment and so I can just softlink the libs to /usr/lib32 from 32bit chroot. No need for VMWare or anything for this prob - work like a toilet in a train, the 64bit gutsy does.

---

### Post by Sunnz on 2007-11-01
> **Saubazi said:**
> I haven't met a 32bit application that would not run - yet

Yea that's great so how do you install them? Do you like manually go to Ubuntu repository and download them and do a dpkg -i blah.deb?

---

### Post by Kilz on 2007-11-01
> **Sunnz said:**
> Yea that's great so how do you install them? Do you like manually go to Ubuntu repository and download them and do a dpkg -i blah.deb?

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by John.Michael.Kane on 2007-11-01
> **Sunnz said:**
> Yea that's great so how do you install them?
You would installed the deb file along with all it's dependencies. most likely using [getlibs: Automatically solves dependencies for binaries]("http://ubuntuforums.org/showthread.php?t=474790")

> **Sunnz said:**
> Do you like manually go to Ubuntu repository and download them and do a dpkg -i blah.deb?
You would have to download the deb file of the program from either their website 

Or
[packages.ubuntu]("http://packages.ubuntu.com/")

In most cases yes you will likely have to pass the dpkg -i --force-all package name.deb command

Also for programs you feel "need or have" to be run in or as 32bit. Your other options.

1) Try to debug the problem that you are having the current 64bit program.
2) File a bug report on any, and all issues either via launchpad or directly with the programs coders
3) Compile from source the latest version. 
4)Use another program that does the same job as the one giving you problems.

---

### Post by Saubazi on 2007-11-01
> **Sunnz said:**
> Yea that's great so how do you install them? Do you like manually go to Ubuntu repository and download them and do a dpkg -i blah.deb?

As already noted by others - if the program in question was 32bit Ubuntu one. Also installing it on chroot environment and launching from 64bit is a way: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

I just have to say that at the moment I don't think I am running anything 32bit provided by Ubuntu packages - that is to say Gutsy seems to have quite a bit of selection.

Where I still need it might be some games or commercial software - these are usually already compiled binaries but won't run without supporting libraries... usually executable that won't launch gives an error about missing library - the I search this one from ubuntu packages- also ldd <name of executable> gives me info about the libraries needed for it.

It is on case by case basis but far less complicated as it sounds...

---

### Post by wangrui on 2008-03-01
Can anyone just simply point out how to run 32bit programs? I have been searching for a while but didn't find any answer.

I installed a ubuntu 64bit today, but there isn't a firefox 3.0 beta 2 for 64 bit. I urgently need it to use the full page zooming. I have a 24 inch screen. It feels horrible without full page zoom while searching how to set each application up in 64 bit ubuntu.

For now, if I type ./firefox-bin, it just said 
```
bash: ./firefox-bin: No such file or directory
```
I have no idea how 32 bit program can run in 64 bit system.

---

### Post by Kilz on 2008-03-01
> **wangrui said:**
> Can anyone just simply point out how to run 32bit programs? I have been searching for a while but didn't find any answer.

I installed a ubuntu 64bit today, but there isn't a firefox 3.0 beta 2 for 64 bit. I urgently need it to use the full page zooming. I have a 24 inch screen. It feels horrible without full page zoom while searching how to set each application up in 64 bit ubuntu.

For now, if I type ./firefox-bin, it just said 
```
bash: ./firefox-bin: No such file or directory
```
I have no idea how 32 bit program can run in 64 bit system.

1. Download the 32bit firefox beta from Mozilla
2. Extract it anyplace.
3. open that folder and find the Firefox file.
4. Double click on the Firefox file.

---

### Post by wangrui on 2008-03-01
> **Kilz said:**
> 1. Download the 32bit firefox beta from Mozilla
2. Extract it anyplace.
3. open that folder and find the Firefox file.
4. Double click on the Firefox file.

Thanks very much. After I installed the ia32-libs, everything works like a charm.

Though the error message I got before is a little confusing:
 
```

firefox$ ./firefox-bin
bash: ./firefox-bin: No such file or directory

```

I thought it means: this executable can't be executed in this wasy
But actually it means: there are some lib missing

And for my experience, I sugguest only install ia32-libs, It seems linux32 is not required at all. And if you install linux32, the synaptic package manager will remove "until-linux", which has all import commands like mkfs,dmesg,fdisk,whereis. I don't think anyone can afford that.

So happy that I got almost everything back in 64bit ubuntu!

---

