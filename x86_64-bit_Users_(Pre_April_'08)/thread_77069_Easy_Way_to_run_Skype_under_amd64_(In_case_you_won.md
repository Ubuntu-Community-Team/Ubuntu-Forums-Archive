---
title: "Easy Way to run Skype under amd64 (In case you wonder)"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by vladvv3 on 2005-10-16
1. Install the linux32 package from the Synaptic Package Manager.
(linux 32-bit emulator for 64-bit versions)


2. Download the Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB) from the Skype Linux section, 

[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

3. Extract the archive somewhere you like

4. Type  in terminal 

 linux32 ./skype  

(or create launcher on the desktop)

 (start in the directory where you untared the tar) 

It take a little bit of time before Skype starts.
Works like a magic no complicated qt libraries installs and so on. It might not be a particularly pretty method but it seems to be the quickest and easiest.

---

### Post by natto on 2005-10-16
I tried that, but I get the following error:

./skype: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

---

### Post by rplantz on 2005-10-16
The description for linux32 in Synaptic says "On systems without support for the PER_LINUX_32 execution domain, this program has no effect."

How do I determine if my system has that support?

If it does not, how do I install it?

Bob

---

### Post by chaok on 2005-10-16
[QUOTE=natto]I tried that, but I get the following error:

./skype: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory[/QUOTE]

Same problem and I do have that libary.

---

### Post by sfabel on 2005-10-17
Works like a charm with me, thanks!

Cheers,
Stephan

---

### Post by Kuolio on 2005-10-17
Seems to be working, thanks alot!

---

### Post by olivierp on 2005-10-17
[quote=vladvv3]1. Install the linux32 package from the Synaptic Package Manager.
(linux 32-bit emulator for 64-bit versions)
[/quote] 
Ah, no. linux32 will only fool (as per the man page) a script/program into thinking it is running on a 32bit system.

You really want to install ia32-libs and ia32-libs-gtk at least to get skype running as described. Note that those 2 packages should have been pulled in if you installed ooo2, along with ia32-libs-openoffice.org

If you need to run other 32bit apps that require KDE libraries, then you may be better off installing ia32-libs-kde also, to save some space.

---

### Post by userzz21 on 2005-10-18
Again I get the same output:

yesi@whoda:~/Desktop/skype-1.2.0.17$ linux32 ./skype
./skype: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

I have installed both libXxf86vm and the dev of that from debian for amd64.

If I knew where skype was looking for these libs then I could put links there.

Some more help would be much appreciated

ya

---

### Post by mloskot on 2005-10-25
[QUOTE=userzz21]I have installed both libXxf86vm and the dev of that from debian for amd64.[/QUOTE]

I have the same problem.
I have all libXxf86*.so.* libraries installed to /usr/lib

Here is what ldd says:

```
mloskot@dog:~/download/skype-1.2.0.17$ ldd ./skype
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x55585000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x555eb000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x55600000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55603000)
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x5560c000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x5561e000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x55688000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x556b7000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x556be000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x556d7000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556da000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556e7000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x557a7000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x557b9000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55873000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55895000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x558a0000)
        libXxf86vm.so.1 => not found
        libdrm.so.1 => not found
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x559cf000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x55a1d000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x55a25000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a29000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a3d000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a5d000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55a60000)
```

Here is listing of all libXxf86.* libraries I have installed:

```
mloskot@dog:~/download/skype-1.2.0.17$ ls -s /usr/lib/libXxf86*
 0 /usr/lib/libXxf86dga.so.1      12 /usr/lib/libXxf86misc.so.1.1.0   0 /usr/lib/libXxf86vm.so.1
24 /usr/lib/libXxf86dga.so.1.0.0  24 /usr/lib/libXxf86vm.a           20 /usr/lib/libXxf86vm.so.1.0.0
 0 /usr/lib/libXxf86misc.so.1      0 /usr/lib/libXxf86vm.so
```

That's clear library libXxf86vm.so.1 is present in my system and is installed where it should be.

So, why when I try to run skype I'm getting following message?

mloskot@dog:~/download/skype-1.2.0.17$ linux32 ./skype
./skype: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

Could anyone explain how to solve it?
Does linux32 needs special LD_* path or something like this?

Thanks in advance

---

### Post by Harlequin chase on 2005-10-30
I have the same problem with libXxf86vm.so.1 using the static binary. 

I tried the dynamic binary and it worked fine. Its smaller too. :)  It does take a long time to load though.

---

### Post by RAOF on 2005-10-30
[QUOTE=mloskot]I have the same problem.
I have all libXxf86*.so.* libraries installed to /usr/lib

Here is what ldd says:

```
mloskot@dog:~/download/skype-1.2.0.17$ ldd ./skype
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x55585000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x555eb000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x55600000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55603000)
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x5560c000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x5561e000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x55688000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x556b7000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x556be000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x556d7000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556da000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556e7000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x557a7000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x557b9000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55873000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55895000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x558a0000)
        libXxf86vm.so.1 => not found
        libdrm.so.1 => not found
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x559cf000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x55a1d000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x55a25000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a29000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a3d000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a5d000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55a60000)
```
...[/QUOTE]
You might notice that all of the libs referenced are actually under the /usr/lib**32** directory.  That's because skype, as a 32bit binary, needs 32bit libs, and **cannot** link to the 64bit libs you've got in /usr/lib.  I suspect that you wouldn't find a libXxf86vm.so.1 under the /usr/lib32 directory, and that's what it's complaining about.

---

### Post by mloskot on 2005-10-30
Yes, you are right. It escaped my notice.
So, is there any lib32 version of missing libraries?
How lib32 versions are marked in Ubuntu repositories?
I don't remember I set up i32 repositories on my sources.list.
It confused me a little.

---

### Post by Inigo Montoya on 2005-11-07
i just install skype on my system (amd64/ubuntu5.10) as followes:
[LIST=1]
[*]install the debian package:
[INDENT][LIST]
[*]download the debian package for from [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
[*]force the installation (we are brave, aren't we?):
*sudo dpk -i --force-all ./skype_1.2.0.18-1_i386.deb*
[/LIST][/INDENT]
[*]install the i386 version of the libqt3-mt library:
[INDENT][LIST]
[*]download the libqt3-mt package for i386 from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[*]force the installation (we are brave, aren't we?):
*sudo dpk -i --force-all ./libqt3-mt_3.3.4-8ubuntu5_i386.deb*
[/LIST][/INDENT]
[*]check if skype is missing anything else:
[INDENT]ldd /usr/bin/skype[/INDENT]
[*]start skype by typing *skype* into a console
[*]go, have an old fashioned...
[/LIST]
don't know if it runs stable. didn't test it intesively yet...

---

### Post by mloskot on 2005-11-08
Here I posted my solution how to run Skype on amd64 box (thanks to ROAF for great help): [Installing lib32 on amd64]("http://www.ubuntuforums.org/showthread.php?p=475023#post475023").

Good luck!
Cheers

---

### Post by mariuss on 2006-04-11
this worked for me just fine

---

### Post by deibuntu on 2006-04-18
Thanks to all for your advices on installing skype for AMD64 ubuntu. Following your guidelines everything seems to be right (when I type ldd /usr/bin/skype all the lib32 libraries are found), but in my case skype doesn't start up... I can see a "Fatal: No Motif style available!" message and the execution is aborted. Does anybody know how to fix this??

Thanks in advance for your help

---

### Post by Prot on 2006-05-01
very nice. although i'm currently configuring chroot access for all my 32-bit apps.

thanks!

---

### Post by steefjeqv on 2006-06-04
Thanks vladvv3,

Works quite good for me.
Using Dapper Drake 64bit on an Opteron based system.

Greetings,
Steven

---

### Post by Hairback357 on 2006-06-04
It worked for me. Thank you.:)

---

### Post by flapane on 2006-06-06
I tried with wine and it worked well
[[IMG]http://img201.imageshack.us/img201/7607/skype5ju.th.jpg[/IMG]](http://img201.imageshack.us/img201/7607/skype5ju.jpg)

---

### Post by apuredol on 2006-06-11
Hi, i just recently installing skype but i have a problem with  libXcursor.so.1 and
libXft.so.2. 

The other libraries are fine... if I made a ldd ./skype i got:

       linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5557a000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x555e0000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x555f6000)
        libXcursor.so.1 => not found
        libXft.so.2 => not found
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x555f9000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x55662000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x55691000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x55699000)
        libdl.so.2 => /lib32/libdl.so.2 (0x556b1000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556b4000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556c1000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x557a7000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x557ba000)
        libm.so.6 => /lib32/libm.so.6 (0x55874000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55896000)
        libc.so.6 => /lib32/libc.so.6 (0x558a1000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0x559d0000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0x559d5000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x559dd000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x55a2b000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a33000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a47000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a66000)

Any Ideas?

Thanks...

---

### Post by aristomastrosi on 2006-06-22
Same problem here... occured ~1 month ago after an aptitude upgrade

---

### Post by Hg80 on 2006-06-23
Thanks got skype to work under 6.06 64bit using this guide

---

### Post by cscashby on 2006-07-01
Just tried it with the beta of 1.3 and it works well. However, it also requires libasound2 - downloading and force installing the i386 version of this leads to a broken apt - running 'sudo apt-get install -f' fixes the 'problem' but stops skype working.

I'm going to copy the libasound2 libraries back from the i386 install after reinstalling the amd64 ones; seems the .debs cannot coexist.

Otherwise - thanks for the easy how-to!

Christian Ashby

---

### Post by cscashby on 2006-07-01
Sorry for the double-post, but FYI the following works:

force-install the i386 version of libasound2
run:
sudo cp /usr/lib/libasound.so.2* /usr/lib32
then to 'unbreak' the apt setup:
sudo apt-get install -f

Christian.

---

### Post by Xizorbg on 2006-07-01
I have a question.  Skype is working well.  I love it!  But I am having trouble getting a launcher to work.  Can you tell me the code?  I went and launched it from a root terminal, which seems to work reliably.  I installed the linux32 and it does function normally, except I have no ringer!  If anyone knows how to make THAT work with the 64bit archi, let me know, too.

Thanks again for all your guys' efforts!

X

---

### Post by zathras777 on 2006-07-03
[QUOTE=cscashby]Sorry for the double-post, but FYI the following works:

force-install the i386 version of libasound2
run:
sudo cp /usr/lib/libasound.so.2* /usr/lib32
then to 'unbreak' the apt setup:
sudo apt-get install -f

Christian.[/QUOTE]

Forgive the daft question, but how do I "force-install" the i386 lib? Thanks :-)

---

### Post by cscashby on 2006-07-03
See 'man dpkg' under '--force-things'

Christian.

---

### Post by zathras777 on 2006-07-04
[QUOTE=cscashby]See 'man dpkg' under '--force-things'

Christian.[/QUOTE]

Thanks, installed the lib exactly as you said and skype now runs. I've run into a problem that when another app is using the alsa output I get

> ALSA lib pcm_dmix.c:788:(snd_pcm_dmix_open) unable to create IPC shm instance

Do I need to alter my .asoundrc file somehow or is it something more involved? 

Thanks!

---

### Post by lwaldron on 2006-07-18
Another easy way that's perhaps less of a hack is to install the "Static binary tar.bz2 with Qt compiled in" - no installation of QT32 libraries needed.

---

### Post by Encryptor on 2006-08-18
The previous post makes it obvious that: simple is genius. Eureka, lwaldron!
I have Ubuntu 6.06 2.6.15-26-amd64-server and I just installed the Static binary tar.bz2 with Qt 3.2 compiled in. No installation needed, just extract and start up the application. Be sure to adjust your devices if you cant hear or record sounds.
Thanks a lot guys! I have been trying to make skype work for a while now. I am glad I found this thread.

---

### Post by craigsn on 2006-08-21
I'm a newbie to linux, so please a little help. I have downloaded the static binary with QT, but when I  try to extract it using the Archive Manager to the /etc directory (I thought this is the one to use), I get a message saying I don't have right permissions to extract archives in the folder "/etc". What should I be doing to make this work?

Thanks
Craig

---

### Post by craigsn on 2006-08-22
cscashby, I have the same problem, where do I get the amd64 libraries, and did this work for you?

Thanks
Craig

> **cscashby said:**
> Just tried it with the beta of 1.3 and it works well. However, it also requires libasound2 - downloading and force installing the i386 version of this leads to a broken apt - running 'sudo apt-get install -f' fixes the 'problem' but stops skype working.

I'm going to copy the libasound2 libraries back from the i386 install after reinstalling the amd64 ones; seems the .debs cannot coexist.

Otherwise - thanks for the easy how-to!

Christian Ashby

---

### Post by kopilo on 2006-09-02
> **craigsn said:**
> I'm a newbie to linux, so please a little help. I have downloaded the static binary with QT, but when I  try to extract it using the Archive Manager to the /etc directory (I thought this is the one to use), I get a message saying I don't have right permissions to extract archives in the folder "/etc". What should I be doing to make this work?

Thanks
Craig
Extract it to your Desktop.

Then open up terminal (Applications -> Accessories -> Terminal) and try typing "linux32 ~/Desktop/sky" then **hit tab** so it completes the name of the directory, then type "skype" then hit enter.

In total the command should look something like this; "linux32 ~/Desktop/skype-1.2.0.18/skype"

The cursor should move to the next line and blink for a bit before Skype opens up.

If not, you either entered in the command wrong or there are some files which are missing from your computer which are needed in order to run the 32 version skype.

Those who are having issues with files could try running this command...

```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```
(Taken from [http://www.tghc.org/staticpages/index.php/32bitfirefoxfordapperamd64](http://www.tghc.org/staticpages/index.php/32bitfirefoxfordapperamd64))

---

### Post by whizbaby on 2006-09-02
Check dis, skyperz...
[www.secdev.org/conf/skype_BHEU06.handout.pdf](www.secdev.org/conf/skype_BHEU06.handout.pdf)

---

### Post by TomPurnell on 2006-10-21
The methods described here all failed for me, skype would fail as if it was not even there, when it blatantly was.
```
./skype
bash: skype: command not found
```

But kopilo's apt-get stuff fixed all that for me :)

> **kopilo said:**
> 
```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```


(For any that are interested, I'm running skype-1.3.0.53 with QT compiled-in, and launching without invoking linux32)

---

### Post by hckurniawan on 2006-12-13
I now can use Skype on Ubuntu64 after installing ia32-libs, ia32-libs-gtk, and lib32asound2 from Sypnatic.

---

### Post by RAOF on 2006-12-14
> **Inigo Montoya said:**
> ...
install the i386 version of the libqt3-mt library:
[INDENT][LIST]
[*]download the libqt3-mt package for i386 from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[*]force the installation (we are brave, aren't we?):
*sudo dpk -i --force-all ./libqt3-mt_3.3.4-8ubuntu5_i386.deb*
[/LIST][/INDENT]
...

I'll just point out that this will **break** any 64bit QT programs you have.  dpkg --force-all will almost certainly bite you!

A better way is to install the **ia32-libs-kde** package, which has those same libraries, but installed to the right spot.

---

### Post by faheyd on 2007-01-11
> **kopilo said:**
> Extract it to your Desktop.

Then open up terminal (Applications -> Accessories -> Terminal) and try typing "linux32 ~/Desktop/sky" then **hit tab** so it completes the name of the directory, then type "skype" then hit enter.

In total the command should look something like this; "linux32 ~/Desktop/skype-1.2.0.18/skype"

The cursor should move to the next line and blink for a bit before Skype opens up.

If not, you either entered in the command wrong or there are some files which are missing from your computer which are needed in order to run the 32 version skype.

Those who are having issues with files could try running this command...

```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```
(Taken from [http://www.tghc.org/staticpages/index.php/32bitfirefoxfordapperamd64](http://www.tghc.org/staticpages/index.php/32bitfirefoxfordapperamd64))

This is great, I just installed 65MegaBytes of libraries to get  a 15MB program to run.
Almost as bad as loading up perl to get  a one line script to run.

(or course, at least I got skype to work. How come skype hasn't released any 64bit programs, could it be that hard?)

---

### Post by faheyd on 2007-01-11
> **faheyd said:**
> This is great, I just installed 65MegaBytes of libraries to get  a 15MB program to run.
Almost as bad as loading up perl to get  a one line script to run.

(or course, at least I got skype to work. How come skype hasn't released any 64bit programs, could it be that hard?)

Well, after doing 65MB lib install above, I get:
MATRIX-64:/usr/local/skype-1.3.0.53$ linux32 ./skype
Segmentation fault (core dumped)
MATRIX-64:/usr/local/skype-1.3.0.53$
dmesg reveals:
[15652.301584] skype[11355]: segfault at 0000000000000000 rip 0000000000000000 rsp 00000000ffa31610 error 14
[15731.213356] skype[11415]: segfault at 0000000000000000 rip 0000000000000000 rsp 00000000ffb4fd50 error 14

---

### Post by Cuppa-Chino on 2007-04-13
> **flapane said:**
> I tried with wine and it worked well
[[IMG]http://img201.imageshack.us/img201/7607/skype5ju.th.jpg[/IMG]](http://img201.imageshack.us/img201/7607/skype5ju.jpg)

have you managed to get skype w/ video working in wine?

---

### Post by Kalon on 2007-05-01
I think I had this working before but now,
when I force the 32bit ver. of libqt3-mt it clobbers the 64 bit one causing problems with some kde apps.

any ideas. did I do somthing wrong?

---

### Post by RAOF on 2007-05-04
As I said in my [post on the previous page](http://ubuntuforums.org/showpost.php?p=1884924&postcount=38) of this thread, installing the i386 .deb of libqt3 **will break all your KDE apps**.

[size=5][color=red]Don't do it![/color][/size]

A much, much better way (also found in my post on the previous page) is to install the **ia32-libs-kde** package!

---

### Post by rickyrockrat on 2007-09-05
Hi all. Here is how I did the install on my Duo-core with Feisty:
<rant>
Skype is a bunch of idiots, are shortsighted, and are idiots. The world is going to 64 bits. Skpe isn't. It is not hard to write portable code unless, apparently  you are working for skype.
</rant>

First get the deb version (feisty) from skype and do a
dpkg -i --force-architecture skpe-debian_1.4.0.99-1_i386.deb
This sets the menus and icons up for you.
Then get the static tarred version (it isn't static, btw) and replace the /usr/bin/skype with it.  This avoids some lib dependencies (QT4, for one).
Then do:
apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32
You may not need all of the above, but it shouldn't hurt.
Then run getlibs on the exe. (getlibs /usr/bin/skype NOTE:After you copy the static bin over) It asks  you if you want to install /feisty/libs/xxx. Say yes, 
hopefully it puts it in the lib32 dir (it did for me). 

You can run ldd /usr/bin/skype |grep not to see if there are any more libs, but this worked well for me.  Kudos to Cappy for his getlibs script:

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)

---

### Post by FlowingSnake on 2007-09-11
> **rickyrockrat said:**
> Hi all. Here is how I did the install on my Duo-core with Feisty:
<rant>
Skype is a bunch of idiots, are shortsighted, and are idiots. The world is going to 64 bits. Skpe isn't. It is not hard to write portable code unless, apparently  you are working for skype.
</rant>

First get the deb version (feisty) from skype and do a
dpkg -i --force-architecture skpe-debian_1.4.0.99-1_i386.deb
This sets the menus and icons up for you.
Then get the static tarred version (it isn't static, btw) and replace the /usr/bin/skype with it.  This avoids some lib dependencies (QT4, for one).
Then do:
apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32
You may not need all of the above, but it shouldn't hurt.
Then run getlibs on the exe. (getlibs /usr/bin/skype NOTE:After you copy the static bin over) It asks  you if you want to install /feisty/libs/xxx. Say yes, 
hopefully it puts it in the lib32 dir (it did for me). 



You can run ldd /usr/bin/skype |grep not to see if there are any more libs, but this worked well for me.  Kudos to Cappy for his getlibs script:

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)



Ok a silly question.
Where should the "skpe-debian_1.4.0.99-1_i386.deb" be when i run the "dpkg -i --force-architecture skpe-debian_1.4.0.99-1_i386.deb" command?
becuase i keep getting this error: "dpkg: error processing skpe-debian_1.4.0.99-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skpe-debian_1.4.0.99-1_i386.deb".

LOL did you leave out the "y" in skype for a reason LOL

The other problem i have is that i keep getting this error: "getlibs: command not found" when i run "getlibs /usr/bin/skype".

any ideas

---

### Post by Cappy on 2007-09-11
Look here: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by rickyrockrat on 2007-09-11
Sorry - you have to download the .deb from Skype's page, then hopefully you know where it is :)

And you have to download getlibs from the URL:
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/) - click on the ubuntu 7.04 link.

Hope that cleared it up.

---

### Post by Mochtroid-X on 2007-09-30
> **rickyrockrat said:**
> Hi all. Here is how I did the install on my Duo-core with Feisty:
<rant>
Skype is a bunch of idiots, are shortsighted, and are idiots. The world is going to 64 bits. Skpe isn't. It is not hard to write portable code unless, apparently  you are working for skype.
</rant>

First get the deb version (feisty) from skype and do a
dpkg -i --force-architecture skpe-debian_1.4.0.99-1_i386.deb
This sets the menus and icons up for you.
Then get the static tarred version (it isn't static, btw) and replace the /usr/bin/skype with it.  This avoids some lib dependencies (QT4, for one).
Then do:
apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32
You may not need all of the above, but it shouldn't hurt.
Then run getlibs on the exe. (getlibs /usr/bin/skype NOTE:After you copy the static bin over) It asks  you if you want to install /feisty/libs/xxx. Say yes, 
hopefully it puts it in the lib32 dir (it did for me). 

You can run ldd /usr/bin/skype |grep not to see if there are any more libs, but this worked well for me.  Kudos to Cappy for his getlibs script:

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)

This worked great for me! Thanks! :KS

---

### Post by locoleo1 on 2008-05-09
> **vladvv3 said:**
> 1. Install the linux32 package from the Synaptic Package Manager.
(linux 32-bit emulator for 64-bit versions)


2. Download the Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB) from the Skype Linux section, 

[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

3. Extract the archive somewhere you like

4. Type  in terminal 

 linux32 ./skype  

(or create launcher on the desktop)

 (start in the directory where you untared the tar) 

It take a little bit of time before Skype starts.
Works like a magic no complicated qt libraries installs and so on. It might not be a particularly pretty method but it seems to be the quickest and easiest.

Hi,

I managed to get my skype working following the instructions here.  I had no problems like others have been reporting.  Just in case, I had followed the instructions on this link first ([https://lists.ubuntu.com/archives/ubuntu-users/2006-August/090685.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-August/090685.html)) and then the ones posted here.

Good luck
Leo

---

