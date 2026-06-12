---
title: "cedega 4.2.1 debian packages for amd64"
date: 2005-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by subterrific on 2005-02-19
I finally learned how to make debian packages, so I stayed up all night packaging a bunch of software I use: gnome-clipboard-daemon, sun-jdk1.5, Azureus, teamspeak2 client and server, cedega.

I also put some work into a script that helps convert i386 packages to amd64 packages. It still needs a lot of work, but right now I've got it converting the cedega i386 deb's to amd64 debs.

To run my scripts, you'll need the cedega i386 4.2.1 debs, debhelper, make, and a gpg key (run: gpg --gen-key). You also need to: export DEBEMAIL=your@email.net before running make. Please give me feedback here if the script breaks. I've only tested it on my machine running Hoary, so it might not work for anyone else at this point. Consider it pre-release quality.

The script basically changes lib dirs to lib32, creates a symlink for libpng.so.3 and patches some shell scripts to get environment variables and paths correct. And repackages the deb's for the new architecture.


EDIT:

I took the time to clean up my scripts a little and package everything together. I'm calling it [ia32-extras](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz). It includes the scripts for skype and cedega, plus a pre-made package called ia32-libs-more that contains the libraries needed by these two apps.

Let me know of any other 32bit apps you'd like to see packaged. Already in my TODO list are: teamspeak2 client/server, quake3, and possibly mplayer (for win32 codecs). I'd also like to do wolfet, but I haven't been able to get it to run outside a 32bit chroot. I know it is possible because I had it working on gentoo. I've got a bug open in ubuntu bugzilla about this, but the developers don't seem to have time to look into it. Anyway, enjoy!

EDIT:

There are new versions of cedega and skype since I did this release. I'm working on updating my scripts, and I'll have a new version ready soon (next week sometime).

[ia32-extras 0.1](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz)
[packaging tips I used](http://people.debian.org/~calvin/unofficial/)

---

### Post by Dylanby on 2005-02-19
Thanks! Will try them out when I have some free time.

---

### Post by kassetra on 2005-02-19
Great work subterrific!  :)  Wow.  That is a lot of work there!
 
 Have you thought about working with the backport developers here?
 I'm sure they could use another talent such as yourself!  :)
 
 Here is the thread talking about the [backports project & developers needed]("http://ubuntuforums.org/showthread.php?t=12097").

---

### Post by subterrific on 2005-02-19
Thanks kassetra, I'll check it out. I still have a lot to learn. Last night was the first time I'd built a package. I haven't even read any of the debian policy guides or the full maintaner guide yet.

---

### Post by subterrific on 2005-02-19
I just finished modifying my scripts to package skype for Hoary amd64.

[skype amd64 script](http://illadvised.com/~jason/skype-amd64-0.1.tar.gz)

---

### Post by dewey on 2005-02-19
Wow, you're very needed.  64 bit packages are lacking quite a bit, and we need everyone we can to make more.

Thanks!

---

### Post by subterrific on 2005-02-20
I took the time to clean up my scripts a little and package everything together. I'm calling it [ia32-extras](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz). It includes the scripts for skype and cedega, plus a pre-made package called ia32-libs-more that contains the libraries needed by these two apps.

Let me know of any other 32bit apps you'd like to see packaged. Already in my TODO list are: teamspeak2 client/server, quake3, and possibly mplayer (for win32 codecs). I'd also like to do wolfet, but I haven't been able to get it to run outside a 32bit chroot. I know it is possible because I had it working on gentoo. I've got a bug open in ubuntu bugzilla about this, but the developers don't seem to have time to look into it. Anyway, enjoy!

---

### Post by artimess on 2005-02-21
[QUOTE=subterrific]I finally learned how to make debian packages, so I stayed up all night packaging a bunch of software I use: gnome-clipboard-daemon, sun-jdk1.5, Azureus, teamspeak2 client and server, cedega.

I also put some work into a script that helps convert i386 packages to amd64 packages. It still needs a lot of work, but right now I've got it converting the cedega i386 deb's to amd64 debs.

To run my scripts, you'll need the cedega i386 4.2.1 debs, debhelper, make, and a gpg key (run: gpg --gen-key). You also need to: export DEBEMAIL=your@email.net before running make. Please give me feedback here if the script breaks. I've only tested it on my machine running Hoary, so it might not work for anyone else at this point. Consider it pre-release quality.

The script basically changes lib dirs to lib32, creates a symlink for libpng.so.3 and patches some shell scripts to get environment variables and paths correct. And repackages the deb's for the new architecture.


EDIT:

I took the time to clean up my scripts a little and package everything together. I'm calling it [ia32-extras](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz). It includes the scripts for skype and cedega, plus a pre-made package called ia32-libs-more that contains the libraries needed by these two apps.

Let me know of any other 32bit apps you'd like to see packaged. Already in my TODO list are: teamspeak2 client/server, quake3, and possibly mplayer (for win32 codecs). I'd also like to do wolfet, but I haven't been able to get it to run outside a 32bit chroot. I know it is possible because I had it working on gentoo. I've got a bug open in ubuntu bugzilla about this, but the developers don't seem to have time to look into it. Anyway, enjoy!

[ia32-extras 0.1](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz)
[packaging tips I used](http://people.debian.org/~calvin/unofficial/)[/QUOTE]
 I was looking for some easy way to get Skype working on AMD64, thanks for your utility.
Would it be possible we adopt what is done on FC3 AMD that 32 bit applications are auomatically recognized and installed through rpm?
I am very impressed with ubuntu, but I find this inflexibility very time consuming and limiting.
Perhaps the other alternative could be to generalize your utility to convert any 32 rpms or debs to be accepted in X86_64 environment?

---

### Post by subterrific on 2005-02-21
[QUOTE=artimess]I was looking for some easy way to get Skype working on AMD64, thanks for your utility.
Would it be possible we adopt what is done on FC3 AMD that 32 bit applications are auomatically recognized and installed through rpm?
I am very impressed with ubuntu, but I find this inflexibility very time consuming and limiting.
Perhaps the other alternative could be to generalize your utility to convert any 32 rpms or debs to be accepted in X86_64 environment?[/QUOTE]

You're welcome.
It is my understanding that the Debian and Ubuntu developers are working on a solution called multiarch. I've thought about generalizing my scripts, but I haven't figured out how make the conversion entirely automated yet. I'm not sure it is even possible. RedHat and SuSE use a different file system layout where /lib is 32bit and /lib64 is 64bit. Debian, Ubuntu, and Gentoo have /lib64 as a symlink pointing to /lib and use a seperate lib32 for 32bit libraries. The advantage of the RedHat way is that nothing needs to be changed and you can install preexisting 32bit packages.

Debian multiarch:
[http://www.linuxbase.org/~taggart/multiarch.html](http://www.linuxbase.org/~taggart/multiarch.html) 
[http://raw.no/debian/amd64-multiarch-3.txt](http://raw.no/debian/amd64-multiarch-3.txt)

---

### Post by artimess on 2005-02-21
Could you please tell me what am I doing wrong that I get the following:
***************
*** 7,13 ****

  Package: skype
  Architecture: amd64
- Depends: libc6 (>= 2.2.5), libgcc1 (>= 1:3.4.1), libqt3c102-mt (>= 3:3.2.0), l
ibstdc++5 (>= 1:2.95.4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0
)
  Description: Skype is free Internet telephony that just works
   Skype offers free superior sound quality Internet telephony. In addition, it
   includes:
--- 7,13 ----

  Package: skype
  Architecture: amd64
+ Depends: ia32-libs-more
  Description: Skype is free Internet telephony that just works
   Skype offers free superior sound quality Internet telephony. In addition, it
   includes:
I have installed ia32-libs-more and I have all the needed packages libc6, libgcc1, ...etc.

Thanks,

Abbas

---

### Post by Juansolo on 2005-02-21
Thanks for your great work, Subterrific. But I have a problem: With the generated packages cedega does not work with acceleration.  My card is a ati 9800 pro.  Drivers correctly installed and works well.  The native games of linux as Armagetron works well with acceleration, but not cedega. Any idea?. Thanks! Juansolo, from Barcelona.

---

### Post by subterrific on 2005-02-21
[QUOTE=artimess]Could you please tell me what am I doing wrong that I get the following:
***************
*** 7,13 ****

  Package: skype
  Architecture: amd64
- Depends: libc6 (>= 2.2.5), libgcc1 (>= 1:3.4.1), libqt3c102-mt (>= 3:3.2.0), l
ibstdc++5 (>= 1:2.95.4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0
)
  Description: Skype is free Internet telephony that just works
   Skype offers free superior sound quality Internet telephony. In addition, it
   includes:
--- 7,13 ----

  Package: skype
  Architecture: amd64
+ Depends: ia32-libs-more
  Description: Skype is free Internet telephony that just works
   Skype offers free superior sound quality Internet telephony. In addition, it
   includes:
I have installed ia32-libs-more and I have all the needed packages libc6, libgcc1, ...etc.

Thanks,

Abbas[/QUOTE]

It looks like one of the patches isn't being applied correctly, but I'd need to see more output. What you gave me there isn't helpful in fixing the problem. Send me the full output either in a private message, or use CODE tags so it doesn't spam the forum.

---

### Post by subterrific on 2005-02-21
[QUOTE=Juansolo]Thanks for your great work, Subterrific. But I have a problem: With the generated packages cedega does not work with acceleration.  My card is a ati 9800 pro.  Drivers correctly installed and works well.  The native games of linux as Armagetron works well with acceleration, but not cedega. Any idea?. Thanks! Juansolo, from Barcelona.[/QUOTE]

I only have an nvidia card, so I have no experience with the ATI drivers. That said, I did a little googling and checked out the gentoo forums, and it looks like it is possible to get 3d accel with 32bit apps. I talked to several people in #gentoo-amd64 who reported that cedega works if you do this:
```
export LIBGL_DRIVERS_PATH=/usr/X11R6/lib32/modules/dri
```
before running it. That of course would require that Ubuntu's package installs the 32bit fglrx support files correctly. Honestly, this is one area I find Ubuntu is really lacking. On Gentoo I was able to run native quake3, ET, etc... with 3d accel, but I can't with Ubuntu (I did recently figure out that the quake3-smp binary works even though I don't have an smp box).

---

### Post by Juansolo on 2005-02-22
I extract the files of the 32 bit rpm package and copy the libraries to /usr/X11R6/lib32/modules and works!!!!!!!! You're great, subterrific!!!!! Thanks from Barcelona.
Juansolo.

---

### Post by songochain on 2005-02-26
Well i've read README file, i did all and i tried to install cedega
Files```
songochain@ximian64:~/ia32-extras-0.1/cedega-amd64$ ls
cedega-4.2.1             README
cedega_4.2.1-1_i386.deb  transgaming-fontinstaller_1.0_i386.deb
files                    transgaming-mozctlinstaller_1.0-1_i386.deb
Makefile
```
If a i type make...```
songochain@ximian64:~/ia32-extras-0.1/cedega-amd64$ make
./files/dpkg-arch-convert cedega_4.2.1-1_i386.deb . 1jjt2
Traceback (most recent call last):
  File "./files/dpkg-arch-convert", line 47, in ?
    os.mkdir(working_dir)
OSError: [Errno 17] File exists: './cedega-4.2.1'
make: *** [cedega] Error 1

```Also with sudo
Any idea??
Thanks

---

### Post by RastaMahata on 2005-02-26
[QUOTE=songochain]Well i've read README file, i did all and i tried to install cedega
Files```
songochain@ximian64:~/ia32-extras-0.1/cedega-amd64$ ls
cedega-4.2.1             README
cedega_4.2.1-1_i386.deb  transgaming-fontinstaller_1.0_i386.deb
files                    transgaming-mozctlinstaller_1.0-1_i386.deb
Makefile
```
If a i type make...```
songochain@ximian64:~/ia32-extras-0.1/cedega-amd64$ make
./files/dpkg-arch-convert cedega_4.2.1-1_i386.deb . 1jjt2
Traceback (most recent call last):
  File "./files/dpkg-arch-convert", line 47, in ?
    os.mkdir(working_dir)
OSError: [Errno 17] File exists: './cedega-4.2.1'
make: *** [cedega] Error 1

```Also with sudo
Any idea??
Thanks[/QUOTE]

you have the installer cedega_4.2.1-1_i386.deb, just type:
dpkg -i cedega_4.2.1-1_i386.deb

---

### Post by subterrific on 2005-02-26
delete the cedega-4.2.1 directory and run make again, I've fixed that issue in the next version.

---

### Post by robot on 2005-02-26
This was a godsend. I'd been messing around trying to get wine installed on my amd64 system but synaptic was complaining about broken packages all the time. After a bit of hacking with the scripts included in this package, I finally got it to run.

Thanks a bunch!

---

### Post by subterrific on 2005-02-26
If you'd like to send me your changes, I can include them in the next version, so people without cedega can use wine.

---

### Post by songochain on 2005-02-26
Hi dude, finally i've installed cedega :D but now i get a error when i try to execute a windows game```
/usr/lib32/transgaming_cedega//winex/bin/wine: can't exec '/mnt/winxp/Programas/Games/CS-S/hl2.exe': error=21

```Any idea to fix it?
Thanks, great works !

---

### Post by subterrific on 2005-02-26
I'm guessing that you're mounting an ntfs partition there and you don't have execute permissions. The transgaming forum would be a better place to get answers related to cedega.

---

### Post by songochain on 2005-02-27
[QUOTE=subterrific]I'm guessing that you're mounting an ntfs partition there and you don't have execute permissions. The transgaming forum would be a better place to get answers related to cedega.[/QUOTE]
 I changed my fstab but i get a error (Could not load graphics driver 'x11drv') so i want to install point2play to test my system to see if it has 3d acceleration or no (glxinfo says yes in rendering... i've installed official ati drivers) Is there any point2play that runs in amd64??
Thanks

---

### Post by subterrific on 2005-02-27
I have not made any point2play packages. point2play is just a GUI that runs cedega for you. It isn't going to fix your 3d drivers. Read the rest of this thread, some other people have had trouble with ATI drivers and found ways to fix them.

---

### Post by iotc247 on 2005-03-03
```
make[2]: Leaving directory `/root/cedega/cedega-4.2.1'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
 signfile cedega_4.2.1-1jjt2_amd64.changes
gpg: skipped `root <iotc247@gmail.com>': secret key not available
gpg: [stdin]: clearsign failed: secret key not available
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/cedega/cedega-4.2.1'
make: *** [cedega] Error 2
```

How do i fix this?  :cry:

---

### Post by subterrific on 2005-03-03
Looks like your gpg key isn't available, did you enter the right passphrase? Are you sure you generated the key correctly? Btw, you don't need to run any of this as root, and probably shouldn't. Thats why it requires the fakeroot package.

---

### Post by iotc247 on 2005-03-03
Nvm going to 32 bit.. I cant stand having to not find packages and w32codecs etc.. Thanks though..

---

### Post by downtime on 2005-03-08
thanks for your work on this subterrific! WoW broke unexpectedly the other day (shell32.dll error) and this fixed it!

now if i can just get ALSA to work with cedega...

---

### Post by mips on 2005-03-09
Thanks,

I get the following error though:

reon@box:~/tmp/ia32-extras-0.1/skype-amd64$ **make**
rm -rf skype-1.0.0.7
./files/dpkg-arch-convert skype_1.0.0.7-1_i386.deb . 1jjt2
patch -p0 skype-1.0.0.7/debian/control < files/skype.control.patch
patching file skype-1.0.0.7/debian/control
Hunk #1 FAILED at 7.
1 out of 1 hunk FAILED -- saving rejects to file skype-1.0.0.7/debian/control.rej
make: *** [skype] Error 1


reon@box:~/tmp/ia32-extras-0.1/skype-amd64$ **ls -l**
total 5516
drwxr-xr-x  2 reon reon    4096 2005-02-21 03:45 files
-rw-r--r--  1 reon reon     357 2005-02-21 03:40 Makefile
-rw-r--r--  1 reon reon     155 2005-02-21 03:36 README
-rw-r--r--  1 reon reon 5623362 2005-03-09 19:47 skype_1.0.0.7-1_i386.deb



Cheers
mips

---

### Post by mips on 2005-03-10
Just in case anybody was wondering I would like to resolve this issue as I use Skype on a daily basis (or should I say 'did').

Please help.

Thanks
mips

---

### Post by S4fi on 2005-04-24
sry but i can't find where can i download the script?

---

### Post by elasticwings on 2005-04-26
I think it's the file at the very bottom of his first post.

---

### Post by mduduzi on 2005-04-28
[QUOTE=subterrific]I finally learned how to make debian packages, 
.
.
.
There are new versions of cedega and skype since I did this release. I'm working on updating my scripts, and I'll have a new version ready soon (next week sometime).

[ia32-extras 0.1](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz)
[packaging tips I used](http://people.debian.org/~calvin/unofficial/)[/QUOTE]

Thanks for the good work. I wish I had found this prio to updating my Hoary using Synaptics. Now your scripts give me the error:

rm -rf skype-1.1.0.3
./files/dpkg-arch-convert skype_1.1.0.3-1_i386.deb . 1jjt2
patch -p0 skype-1.1.0.3/debian/control < files/skype.control.patch
patching file skype-1.1.0.3/debian/control
Hunk #1 FAILED at 7.
1 out of 1 hunk FAILED -- saving rejects to file skype-1.1.0.3/debian/control.rej
make: *** [skype] Error 1

As you can see, after my failure to use your scripts, I combed through every file and script and updated all references to reflect currently installed versions of packages. But I still get the same error message as though I had not made any changes.

Where am I going wrong? ](*,)  Has anybody been able to get this right using the latest versions of both Skype (1.1.0.3) and a fully update Ubuntu Hoary?

MMK.

---

### Post by Jarz Corp on 2005-04-30
Okay like a lot of other sad people who bought a kickass Amd64 based system, I really thought this looked cool, until I realized I had to buy cedega in order to get skype up and runing. I don't think so.

But great effort nonetheless man.

/Jarz Corp

---

### Post by mduduzi on 2005-05-01
I suppose that means I should just forget it for now. I'm not buying cedega either. The irony is that Ubuntu if freedom-free and open, Skype is money-free ('mahala' -As we say in South Africa) and to get these two to work together we've gotta pay a third party?

As a temporary measure, I think I'd rather dual boot with Linux 32bit than the other stuff.

---

### Post by Jarz Corp on 2005-05-01
I would just like to add that I really love ubuntu. I have been trying a lot of distros in my time, both the ones that claim to be easy to use and the ones that don't even bother to do that.

It works so well and it is so darned easy to install. Which probably is why it makes it so much harder to accept the fact that some things just don't plain exist.

So lets hope that the small part of the developer world, the word developer doesn't allways fit the people doing just that =), stops following the wintel train and realize that there are such a thing as a true 64 bit chip for common man, and then maybee Sun, Real, Skype, (add your one fav missing soft here), could once again get the imense pleasure of counting us amoungst their "users".

Funny detail. One thing that never worked on this maching on XP Windows, which I have bought just for gaming purposes, was the cpu scaling, it ROCKS on ubuntu.

---

### Post by picard on 2005-06-20
Hey

i just want to know if anyone has figured out how to over come this error when tying to install skype or cedega?

```

./files/dpkg-arch-convert cedega_4.2.1-1_i386.deb . 1jjt2
mv cedega-4.2.1/debian/tmp/usr/lib cedega-4.2.1/debian/tmp/usr/lib32
patch -p0 cedega-4.2.1/debian/tmp/usr/bin/cedega < files/cedega.patch
patching file cedega-4.2.1/debian/tmp/usr/bin/cedega
patch -p0 cedega-4.2.1/debian/control < files/control.patch
patching file cedega-4.2.1/debian/control
Hunk #1 FAILED at 7.
1 out of 1 hunk FAILED -- saving rejects to file cedega-4.2.1/debian/control.rej
make: *** [cedega] Error 1

```

I have just recently installed ubuntu and now trying to get my cedega working.

If anyone has any help please post or pm me

Thanx

Picard

---

### Post by subterrific on 2005-06-25
[QUOTE=Jarz Corp]Okay like a lot of other sad people who bought a kickass Amd64 based system, I really thought this looked cool, until I realized I had to buy cedega in order to get skype up and runing. I don't think so.

But great effort nonetheless man.

/Jarz Corp[/QUOTE]

You seem to be very confused. amd64 is the best of both worlds, it can run 32bit and 64bit, you don't need anything else and you definitely shouldn't be sad. You do **not** need to buy cedega to run skype. If you can't handle running a 64bit kernel, install the i386 version of Ubuntu and everything will work just fine. You won't even notice a speed difference. The instructions in this thread are for people who care about having a 64bit kernel and don't mind the extra work it takes.

---

### Post by Jarz Corp on 2005-06-25
Yup skype can be made to work on the 64bit version, U just have to killall esd before U run it, but that goes for a lot of apps on the 64bit, ET and so on.

---

### Post by Jarz Corp on 2005-06-25
Sorry me again.

I don't mind the extra work and having to hack stuff, that is the only way to get linux to work, it is proably 10 years to early to expect linux to be ready out-of-the-box, even though ubuntu is damn close to doing just that.

No way am I going to install 386 stuff, that is a stupid proposal, but the real shi** about 64 bit is all the stuff that just doesn't exist, like alsalibs f.ex. So U can't hack a solution just accept things as they are without any alternatives, that isn't what linux is about for me.

---

### Post by erikfzr on 2005-08-08
Hello,
I have a problem with installing skype.
(NOTE: I changed the Makefile, because a newer version of skype is available)

This is what I get, when I type make:

rm -rf skype-1.2.0.11
./files/dpkg-arch-convert skype_1.2.0.11-1_i386.deb . 1jjt2
patch -p0 skype-1.2.0.11/debian/control < files/skype.control.patch
patching file skype-1.2.0.11/debian/control
Hunk #1 FAILED at 7.
1 out of 1 hunk FAILED -- saving rejects to file skype-1.2.0.11/debian/control.rej
make: *** [skype] Fehler 1


Erik

---

### Post by patricia on 2005-09-16
Hey!

I have skype working pretty fine here, except that it didn't ring when I got or made a call. When its done, i can hear pretty well the other side, and they also heard me.

Any idea about what could I do to fix it?



Thanks


Patrícia

---

### Post by subterrific on 2005-09-16
Sorry, I never tried using skype for anything other than text chat.

---

### Post by mihai_marandici on 2006-12-28
Hi!
I have an AMD64 and try to install quake3. Found this thread, but the link: [http://illadvised.com/~jason/ia32-extras-0.1.tar.gz](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz) is broken. Can anybody send me this package to mail? Or post a new working link? My email is [email]mihai.marandici@gmail.com[/email]
Thank you in advance!

---

