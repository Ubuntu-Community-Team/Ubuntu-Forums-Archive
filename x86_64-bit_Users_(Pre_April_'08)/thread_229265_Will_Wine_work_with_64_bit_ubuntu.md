---
title: "Will Wine work with 64 bit ubuntu?"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by lou1998 on 2006-08-04
I have spent the past 3 days trying to get wine installed on my new computer witha amg 64 x2 processor.  Can wine be compiled or isntalled in 64 bit ubuntu?  Would it be easier to just swtich to 32 bit ubuntu?

---

### Post by Kilz on 2006-08-04
> **lou1998 said:**
> I have spent the past 3 days trying to get wine installed on my new computer witha amg 64 x2 processor.  Can wine be compiled or isntalled in 64 bit ubuntu?  Would it be easier to just swtich to 32 bit ubuntu?

Wine is easy to [install in 64bit Ubuntu.]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by lou1998 on 2006-08-04
Does that script insall the World of Warcraft patch?  I have been trying to compile from source so I can include the patches.

---

### Post by Kilz on 2006-08-04
> **lou1998 said:**
> Does that script insall the World of Warcraft patch?  I have been trying to compile from source so I can include the patches.

Unfortunatly no, You might want to look at [this compiling guide]("https://help.ubuntu.com/community/BuildingWineFromSource") for wine.

---

### Post by lou1998 on 2006-08-04
Those are the directions I have been following.  When I run make, I get an error about a missing lib???.so.1 file.  Not sure about the exact name since I am at work right now.

On a side note, I originally tried installing Kubuntu since I prefer KDE.  All the Jack files were missing during that compile from source.  Are those gnome specific?

---

### Post by cocteau on 2006-08-04
> **lou1998 said:**
> Those are the directions I have been following.  When I run make, I get an error about a missing lib???.so.1 file.  Not sure about the exact name since I am at work right now.

I don't know what the exact problem might but that guide worked flawlessly for me on my athlon 64, so yes, it is possible to install wine on a 64 bit computer.

> On a side note, I originally tried installing Kubuntu since I prefer KDE.  All the Jack files were missing during that compile from source.  Are those gnome specific?

No, I believe Jack might be dependent on ALSA but that's about it. It definately isn't desktop specific. However, I have noticed that some apps won't install with the new libjack-0.100* as the claim to be missing a dependency for libjack0.80* or higher. I don't know how to get around that problem, though.

Hope that at least made things a bit clearer...

---

### Post by lou1998 on 2006-08-04
I will give it another try this afternoon when I get home from work.
This is my first time using Ubuntu.  Are there any tricks to making sure have all the required dependencies before I start?  I added the repository per the instructions and I ran the sudo apt-get dep wine command as well, but still have those missing items.  Do I need to do something else? 
Thanks!

---

### Post by cocteau on 2006-08-04
I don't know other than try and have a quick look through the wine readme and see what dependencies they say wine has and install them.

But if the file you are missing is libGL.so.1 the problem might be slightly worse. I tried to install ATIs fglrx driver and had the same file missing. Kilz suggested deleting it and doing the installation again to recreate the link but that didn't work for me. In the end I let it go as I could live without the ATI control panel. But that's bad if that is a pervasive error for many users.

Sorry I can't give any more specific help.

---

### Post by lou1998 on 2006-08-04
I tried again since I got home and have the same error.  Here is the error text:

/usr/bin/ld: warning: libdl.so.2, needed by ../libs/wine/libwine.so, not found (try using -rpath or -rpath-link)
../libs/wine/libwine.so: undefined reference to `dlclose@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlerror@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlopen@GLIBC_2.1'
../libs/wine/libwine.so: undefined reference to `dlsym@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dladdr@GLIBC_2.0'
collect2: ld returned 1 exit status
make[2]: *** [sfnt2fnt] Error 1

My /lib32 directory has lbidl.so.2 in it, so I am not sure why its giving me this error.
Any help is greatly appreciated.

---

### Post by cocteau on 2006-08-04
> **lou1998 said:**
> My /lib32 directory has lbidl.so.2 in it, so I am not sure why its giving me this error.

Is libdl.so.2 also in your /usr/lib/ folder? If not try and create a symlink to it.

```
sudo ln -s /usr/lib32/libdl.so.2 /usr/lib/libdl.so.2
```

---

### Post by lou1998 on 2006-08-04
Thanks Cocteau!
I copied libdl.2.so into my /usr/lib directory and that got me past that error.  
Unfortunately, I now have this error:

2 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -ldxguid -luuid  -L/usr/X11R6/lib  -lXe xt -lX11   ../../libs/port/libwine_port.a
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../ libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../ libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for  -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.

---

### Post by cocteau on 2006-08-04
That looks strange indeed. Do you have all the 32bit compatability layers installed? I got these from Kilz' 32bit firefox guide. Try and run this:

```
sudo apt-get update
sudo apt-get install ia32-libs ia32-libs-gtk gsfonts gsfonts-x11 linux32
```

---

### Post by lou1998 on 2006-08-04
I did the update you sugested and still have the same problem.
Would it be any easier to run wine if I installed 32 bit Ubuntu instead?

---

### Post by cocteau on 2006-08-04
> **lou1998 said:**
> I did the update you sugested and still have the same problem.
Would it be any easier to run wine if I installed 32 bit Ubuntu instead?

To tell you the truth I don't know. I haven't tried to install wine on a 32 bit system. 

Your problem seems weird though. I have just done a fresh install today, and I installed the fglrx driver, the 32 bit firefox (to get Java) and wine using Kilz's guides and now I am running wine fine.

I'm afraid I can't give you much help here. I can only tell you that I tried to install compiz/xgl which turned out to be a bad idea as it broke openGL on my system and never actually worked, hence my reason for a fresh install.

Sorry I couldn't be of any more help.

---

### Post by lou1998 on 2006-08-04
Ok, I tried a different approach described here:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

and now I get this error:

ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.8kzbo6.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2

---

### Post by Kilz on 2006-08-05
I have a 32bit virtual machine. I will try and compile wine with the wow patches tomarow, just got in late. If I am sucessfull I will post them here.

---

### Post by Kilz on 2006-08-05
Ok, I was able to compile wine 9.17 with the current wow patch for that version. I couldnt find any patches for 9.18, I think its to new. [I am upload it it now to here]("http://home.comcast.net/~ubuntu64user/wine_0.9.17_4wow_Ubuntu-6.06-1_i386.deb"). It is still a i386 .deb file. You will have to follow [my howto]("http://www.ubuntuforums.org/showthread.php?t=185557") to install it.

---

### Post by Mooie on 2006-08-17
I have a cedega account, but i would like to try all my games that work /w cedega on wine to see how my fps compares, and see if I really need to keep cedega.  Your download seems to be broken, I currently have wine 9.19 installed on my 64 bit system (i used your howto).  could you mabey email the wine install file to me as an attachment? my email address is [email]mooieisme@hotmail.com[/email]

thanks:D

---

### Post by Kilz on 2006-08-17
> **Mooie said:**
> I have a cedega account, but i would like to try all my games that work /w cedega on wine to see how my fps compares, and see if I really need to keep cedega.  Your download seems to be broken, I currently have wine 9.19 installed on my 64 bit system (i used your howto).  could you mabey email the wine install file to me as an attachment? my email address is [email]mooieisme@hotmail.com[/email]

thanks:D

I just checked the downloads on the page and they are good. The script installs wine 9.19 without problems. The download link to the manual howto is to a directory that you have to select the wine .deb file.

---

### Post by Mooie on 2006-08-18
so the link has 9.19 with the WoW patches? I can currently run WoW with wine,  but the d3d is messed up, and i have to run it in opengl (though I have to use a mod that hides the minimap, or the game crashes).

I still cant open your link, it gives the error
> Page URL Not Found!!

The requested page does not exist on this server. The URL you typed or followed is either outdated or inaccurate.


is there anywhere else i could download it? thanks :D

---

### Post by Kilz on 2006-08-18
> **Mooie said:**
> so the link has 9.19 with the WoW patches? I can currently run WoW with wine,  but the d3d is messed up, and i have to run it in opengl (though I have to use a mod that hides the minimap, or the game crashes).

I still cant open your link, it gives the error


is there anywhere else i could download it? thanks :D

No mooie the WoW patches are not linked in my howto.

---

