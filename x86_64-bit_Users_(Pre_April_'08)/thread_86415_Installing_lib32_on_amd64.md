---
title: "Installing lib32 on amd64"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mloskot on 2005-11-05
Hi,

Simply, I'm still struggling with skype on my amd64 box.
I know know what is writeen about skype on amd64 ([Easy Way to run Skype under amd64]("http://www.ubuntuforums.org/showthread.php?t=77069&page=2")) and this is the main problem I want to solve. But the real thing I'd like to learn is the concept and best practice behind linux32/lib32 and how to install i386 packages on amd64 properly.

I have only i386 repos in my sources.list.
I see a lot of files in my /usr/lib32 but I've not installed any i386 packages explicitely. They seems to be installed behind the scene.
Next, I have some application running as 
$ linux32 ./my-app 
just like I need to run Skype ($ linux32 $HOME/bin/skype).
But this application requires some libraries to be installed in lib32:

```
mloskot@dog:~/download/skype-1.2.0.18$ linux32 ./skype
./skype: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory
```

The main question is: where can I find those libraries? In amd64 repositories or i386?

I tried to install 
libxxf86dga1_7.0.0-3_i386.deb
libxxf86misc1_7.0.0-2_i386.deb
libxxf86vm1_7.0.0-2_i386.deb
downloaded from i386 repositories from [http://packages.ubuntu.com](http://packages.ubuntu.com) but I can not install them:

```
mloskot@dog:~/download$ sudo dpkg -i libxxf86vm1_7.0.0-2_i386.deb
dpkg: error processing libxxf86vm1_7.0.0-2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 libxxf86vm1_7.0.0-2_i386.deb
```

Here comes my questions:
Should I build those packages from sources downloaded from i386 repos?
Will those packages (from i386 repos) be installed to /lib/lib32 (and related) path on amd64 platform?

Where lib32 and linux32 packages are from? i386 or amd64 repos?

Thanks for any explanation
Cheers

---

### Post by RSX311 on 2005-11-06
I think you have to force the installation so try 

```
sudo dpkg -i --force install <package name>
```

---

### Post by RAOF on 2005-11-06
I would be cautious installing those i386 debs - they'll probably try to install their libraries to /usr/lib, and overwrite your 64bit libs.

The lib32 packages are all from the amd64 repos.  But it seems that libXxf86vm is not in any of the ia32* libraries.  You could try manually extracting the relevent libraries from those debs, and sticking them in the /usr/lib32 directory.  You'll then need to run ldconfig to update the library cache.  I believe that file-roller will open debs as archives.

---

### Post by mloskot on 2005-11-06
[QUOTE=RAOF]I would be cautious installing those i386 debs - they'll probably try to install their libraries to /usr/lib, and overwrite your 64bit libs.> 

Hurray! And that's what I'm talking about being affraid of and asking for confirmation it would happen.

[QUOTE=RAOF]The lib32 packages are all from the amd64 repos.

This is another useful information. I have to remember this rule **Usi amg64 I shouldn't even try to place i386 repos to my sources.list.** All I need is in amd64 repos, even stuff required for 32 bit emulation.

[QUOTE=RAOF]But it seems that libXxf86vm is not in any of the ia32* libraries.  You could try manually extracting the relevent libraries from those debs, and sticking them in the /usr/lib32 directory.  You'll then need to run ldconfig to update the library cache.  I believe that file-roller will open debs as archives.[/QUOTE]

Thanks, for that solution but if some day libXxf86vm will be available in amd64 repos and I will try to install them using apt-get is there any chance that all files I manually-extracted will be replaced by those from the deb?

Thanks for your anser, I was losing hope.

Cheers

---

### Post by RAOF on 2005-11-07
[QUOTE=mloskot]...
Thanks, for that solution but if some day libXxf86vm will be available in amd64 repos and I will try to install them using apt-get is there any chance that all files I manually-extracted will be replaced by those from the deb?...[/QUOTE]
If you install those files manually, and they wind up in some deb from the repository, apt-get will overwrite them with the packaged versions, if you install the package containing them.  They won't get accidentally overwritten by some version that doesn't work.

---

### Post by mloskot on 2005-11-07
[QUOTE=RAOF]If you install those files manually, and they wind up in some deb from the repository, apt-get will overwrite them with the packaged versions, if you install the package containing them.[/QUOTE]

Great! That's what I like to happen in future. Now, I have to find some time to try your solution.
Thanks for your help
Cheers

---

### Post by mloskot on 2005-11-08
**Skype works on my amd64 box!**

As **RAOF** suggested I installed missing i386 packages manually by unpacking every package and copying libraries to /usr/lib32 (NOT /usr/lib).
I had to install following packages:

[libxxf86vm1_7.0.0-2_i386.deb]("http://packages.ubuntu.com/breezy/libs/libxxf86vm1")
[libdrm1_1.0.3-2_i386.deb ]("http://packages.ubuntu.com/breezy/libs/libdrm1")

deb packages can be unpacked with following command:
*ar -x libxxf86vm1_7.0.0-2_i386.deb*

and you will get two archives:
control.tar.gz
data.tar.gz

You can safely do:
*rm control.tar.gz*

Next, unpack the second one:
*tar -zxf data.tar.gz*

and you will get new *usr* directory with files we need.
Now, copy them to proper location:
*sudo cp -p usr/lib/* /usr/lib32*

*(Please, not there is no forward slach at the beginning of the first path)*

You will have to check and fix symbolic links in /usr/lib32 for unpacked and copied libraries:
*sudo ln -s /usr/lib32/libXxf86vm.so.1.0.0 /usr/lib32/libXxf86vm.so.1* 

Do the same with libdrm1_1.0.3-2_i386.deb package and update ldd cache:
*sudo libconfig*

Now, try to find if skype can find all required libraries:
ldd <PATH_TO_SKYPE_BINARY>/skype | grep "not found"

If there is something missing repeat steps discussed above: download required i386 deb package, unpack, copy, fix symlinks, run ldconfig, run ldd and check the output for skype binary.

Finally, you can run skype:
linux32 <PATH_TO_SKYPE>/skype

and after a few seconds you will get skype window.

Here, Inigo Montoya posted another solution, but I'm not so brave on my workstation so I would not try to force packages installation to /usr/lib where amd64 stuff live, but everyone is free to do it his own way: [Easy Way to run Skype under amd64](http://ubuntuforums.org/showthread.php?p=474481#post474481)

Cheers

---

### Post by Simpele on 2005-11-08
libconfig should be ldconfig but apart from that: excellent how-to and it works for me.

---

### Post by mloskot on 2005-11-08
[QUOTE=Simpele]libconfig should be ldconfig but apart from that[/QUOTE]

Yes you're right.

[QUOTE=Simpele]excellent how-to and it works for me.[/QUOTE]

Great! Another happy Skype user on amd64 :-)
Cheers

---

### Post by rhaurison on 2005-11-11
More elegant:

Install chroot 32bit ([http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit"))

1) in /usr move default lib32 dir (from linux32)  to lib32.local 
2) make symlink from chroot... 

ln -s /chroot/usr/lib /usr/lib32

3) include /usr/lib32.local in /etc/ldconfig.so 
4) run ldconfig and finish.

All problems with deps can be solved with chroot /chroot and apt-get in 32bit chrooted.

---

### Post by chakatz on 2006-01-31
Here is a link to a page that that has nice instructions for 32 bit programs on amd64:
[http://www.maxxer.it/linux/notsoweirdprograms.html]("http://www.maxxer.it/linux/notsoweirdprograms.html")

The main advantage to his instructions is the way he installs the i386.deb files:
**dpkg -X libqt3c102-mt_3.3.3-7_i386.deb /emul/ia32-linux**
is an example. No need to extract the files individually.
**dpkg -X <*.deb file*> <*Location to extract it*>**

KISS: Keep It Simple Stupid (No insults intended)

BTW, I'm a debian user and just went to the sarge (i386) pool section to get the deb files. Drop the 'lib' at the beginning of the filenames to find the directory where they are located.

---

### Post by phyd on 2006-06-10
Hi! 
I did everything written above, copied all the libs in lib32.

After the first ldd skype | grep "not found" he said:

missing libqt3-mt 

So I copied the libqt3-mt libs files like the previous ones, but when I run 

linux32 skype

nothing appears and after a little time he writes:

Fatal: No Plastik style available!
Aborted

Any Ideas to solve this stuff? I use Ubuntu 64 
thankx

---

### Post by Jason_25 on 2006-06-10
I wouldn't use this route at all, especially for skype.  Download the static binary from the website, extract it somewhere, and try to run it.  It will probably say you need some xlibs.  I can't remember the names.  Grab them from the 32-bit ubuntu archives, put them in /usr/lib32, run ldconfig, and then run skype again.

---

### Post by phyd on 2006-06-12
I did it, my friend, and it goes. 
It's a bit slow when it starts, but is fine. :) 
Thanks

---

### Post by Jason_25 on 2006-06-12
To keep it from being slow to start, start it with
```

--disable-dbus

```

---

### Post by Torquemada28 on 2006-06-18
I'm far too much of a noob for this.
*waits for Skype to release a native 64bit version*

---

### Post by Jason_25 on 2006-06-18
[QUOTE=Torquemada28]I'm far too much of a noob for this.
*waits for Skype to release a native 64bit version*[/QUOTE]
It will never happen.  You'll be stuck to repo-only software  on 64-bit if you can't do something as basic as this.  Pm me if you have a problem with installing it.

---

### Post by dimogrec on 2006-07-07
> **mloskot said:**
> 


deb packages can be unpacked with following command:
*ar -x libxxf86vm1_7.0.0-2_i386.deb*

Sorry but *ar* command seems to be unknown for my Shell on Kubuntu 6.06 64bit :neutral: 

*bash: ar: command not found*

Is there something I could do to get this command working?

---

### Post by mesh2005 on 2006-11-11
I don't find the command ar !

---

### Post by hckurniawan on 2006-12-13
I now can use Skype on Ubuntu64 after installing ia32-libs, ia32-libs-gtk, and lib32asound2 from Sypnatic.

---

### Post by loosetoned on 2007-11-25
Here is a great solution to any 32-bit lib problem with amd64:

[getlibs]("http://ubuntuforums.org/showthread.php?t=474790")

It's installable from Synaptic as well, but I followed the instructions in that link to get it.  It works like a charm, saves hours.

It installs whatever file you request in the lib32 directory, and also installs all dependencies.  It does so by downloading and extracting, the exact same way that we do it manually, but it's automated and also installs all dependencies.

Whoever made it is a true hero. :)


(I used the "getlibs -32 libraryname.so.0" command to install the libs that I needed, worked perfectly.)

---

