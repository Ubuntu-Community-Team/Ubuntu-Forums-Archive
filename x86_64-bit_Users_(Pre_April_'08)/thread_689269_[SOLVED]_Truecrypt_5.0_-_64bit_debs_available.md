---
title: "[SOLVED] Truecrypt 5.0 - 64bit debs available?"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbkerns on 2008-02-06
Truecrypt 5.0 has been released and only the i386 debs are available, do you guys know where a 64 bit deb is available?  Thanks in advance.

---

### Post by Heinzelotto on 2008-02-06
[SIZE="5"]**[COLOR="Red"]A new .deb for Ubuntu 64-bit is ready, you can download TrueCrypt v5.0a [here]("http://rapidshare.com/files/92304004/truecrypt_5.0a-0ubuntu1_amd64.deb")[/COLOR]**[/SIZE] 
md5sum: f936b5d6912ada0e3389b5cb6c693abc


Version 5.0 (old version) with dependencies (for ubuntu users): [here]("http://rapidshare.com/files/89758961/truecrypt_5.0-0ubuntu1_amd64.deb")
md5sum: md5sum: a80d3c52f3fa690fa0040abda531462b

Version 5.0 (old version) WITHOUT dependencies (maybe good for debian stable users who don't have all those new versions of the packages as Ubuntu users do): [download here]("http://rapidshare.com/files/90068414/truecrypt_5.0-0ubuntu1_amd64.deb")
md5sum: ecae7e5966d13e12121cc3289cec5202)

if you'd rather like to compile the package yourself, see [this post]("http://ubuntuforums.org/showpost.php?p=4281459&postcount=13") for information.

---

### Post by gorgor_bay on 2008-02-06
I've also unsuccessfully tried to build, see [http://ubuntuforums.org/showpost.php?p=4280504&postcount=29](http://ubuntuforums.org/showpost.php?p=4280504&postcount=29)

and there are indeed no deb for amd64 yet.

Plus the TrueCrypt forums are down, so we got to wait and see.

---

### Post by AusIV4 on 2008-02-06
I've been working on compiling the 64 bit version, but I've been getting errors with the wx libraries. If I get it compiled I'll post a .DEB

---

### Post by ushimitsudoki on 2008-02-06
I'm getting unsuccessful results trying to compile. Posting to add my voice and keep track of this thread!

Here's as far as I got:
The wxrelease directory builds successfully (albeit with one warning: warning: &#8216;wxDummyGsockVar&#8217; defined but not used)

After that the make process fails with:
jason@apollo:/usr/src/truecrypt-5.0-source$ sudo make
Compiling Buffer.cpp
StringConverter.h:23: error: &#8216;static std::wstring TrueCrypt::StringConverter::FromNumber(long int)&#8217; cannot be overloaded
StringConverter.h:22: error: with &#8216;static std::wstring TrueCrypt::StringConverter::FromNumber(TrueCrypt::int64)&#8217;
StringConverter.h:26: error: &#8216;static std::wstring TrueCrypt::StringConverter::FromNumber(TrueCrypt::uint64)&#8217; cannot be overloaded
StringConverter.h:25: error: with &#8216;static std::wstring TrueCrypt::StringConverter::FromNumber(long unsigned int)&#8217;
make[1]: *** [Buffer.o] Error 1
make: *** [all] Error 2

---

### Post by gorgor_bay on 2008-02-06
I have exactly the same symptoms as ushimitsudoki. I'm also following the truecrypt website to see when their forum will be up and running again.

---

### Post by AusIV4 on 2008-02-06
> **gorgor_bay said:**
> I have exactly the same symptoms as ushimitsudoki. I'm also following the truecrypt website to see when their forum will be up and running again.

For what it's worth, there forum has been down for weeks. It may come back soon, but I wouldn't count on it.

On another note, I've just tried compiling the source on my 32 bit machine, and did not have the same problems, which means there's something here that's conflicting directly with the 64 bit architecture or libraries.

---

### Post by Heinzelotto on 2008-02-06
> **ushimitsudoki said:**
> 
Here's as far as I got: [...]

i got exactly the same errors and warnings as you.

The conflicting lines in the Code are:

[PHP]static wstring FromNumber (int64 number);
static wstring FromNumber (long number);[/PHP]

and

[PHP]static wstring FromNumber (unsigned long number);
static wstring FromNumber (uint64 number);[/PHP]

i am not that familiar with the 64-bit architecture but i think the problem is that on a 64-bit machine a "long" is as big as a "int64" and the compiler treats them the same way so this piece of the code looks to the compiler as two times the same thing.

you can solve this problem by commenting one of them out (either the int64 or the long one) and it works, but unfortunately there are more complex problems in other source files. I am working on these right now, hopefully it aren't that many ;)

[COLOR="Red"]EDIT: weheeee, got it working.... umm.. at least compiling. I will post my changes to the code soon (after testing it a bit ;) )[/COLOR]

Greetings,
Heinzelotto

---

### Post by gorgor_bay on 2008-02-06
Thanks Heinzelotto !

---

### Post by AusIV4 on 2008-02-06
I believe, int64 is defined by truecrypt. Any idea on where it's defined?

---

### Post by Heinzelotto on 2008-02-06
> **AusIV4 said:**
> I believe, int64 is defined by truecrypt. Any idea on where it's defined?

yes:

[PHP]
./Platform/PlatformBase.h:      typedef __int64 int64;
./Platform/PlatformBase.h:      typedef unsigned __int64 uint64;
[/PHP]

so it's just a short-form for "__int64" and "unsigned __int64"

---

### Post by AusIV4 on 2008-02-06
I got past that problem!

I modified StringConverter.h and StringConverter.cpp to avoid having overloaded operators. Instead of having FromNumber (int num), FromNumber (int64 num), FromNumber...

I changed it to be FromNumberi (int num), FromNumberi64(int64 num) ... So that the functions all had different names.

Then I compiled modified the one instance where this function was actually called.

Now I'm having a problem that it can't find the necessary sources for fuse, but hopefully I'll have that taken care of within the hour.

[Edit]
Resolved by installing libfuse-dev.

Now have problems with application.cpp

---

### Post by Heinzelotto on 2008-02-06
alright, in the attachment or [here]("http://nopaste.biz/34954") you can find the diff to make it work.

to apply the diff, navigate to the source-code directory of truecrypt and run ```
patch --dir ./ -p0 -i /path/to/patch_file
```

have fun ;)

PS: @AsusIV4: the sources of fuse are in the package libfuse-dev :)

EDIT: thanks, i updated the patch to include StringConverter.h, too

---

### Post by AusIV4 on 2008-02-06
> **Heinzelotto said:**
> alright, in the attachment or [here]("http://nopaste.biz/34846") you can find the diff to make it work.

to apply the diff, navigate to the source-code directory of truecrypt and run ```
patch --dir ./ -p0 -i /path/to/patch_file
```

good luck ;)

PS: @AsusIV4: the sources of fuse are in the package libfuse-dev :)
Damn, you beat me by 5 minutes. I was logging in to post my solution. Yours, however, seems a tad more elegant (and less likely to break things), so I'll be using yours.

Thanks a bunch.

(Any thoughts on making a DEB?)

[EDIT]
I believe you forgot to include the patch for your Platform/StringConverter.h file.

---

### Post by Heinzelotto on 2008-02-06
I've never made a DEB before, but I'll try it, so this will be my first time ;)

---

### Post by TuxDevil on 2008-02-06
Did either of you get these errors about missing header files?

Compiling MainFrame.cpp
Forms/MainFrame.cpp:23:32: error: TravelerDiskWizard.h: No such file or directory
In file included from Forms/MainFrame.cpp:24:
Forms/VolumeCreationWizard.h:13:44: error: TravelerMountOptionsWizardPage.h: No such file or directory
make[1]: *** [Forms/MainFrame.o] Error 1
make: *** [all] Error 2

---

### Post by Heinzelotto on 2008-02-06
> **TuxDevil said:**
> Did either of you get these errors about missing header files?

Compiling MainFrame.cpp
Forms/MainFrame.cpp:23:32: error: TravelerDiskWizard.h: No such file or directory
In file included from Forms/MainFrame.cpp:24:
Forms/VolumeCreationWizard.h:13:44: error: TravelerMountOptionsWizardPage.h: No such file or directory
make[1]: *** [Forms/MainFrame.o] Error 1
make: *** [all] Error 2

this error occures because TC_WINDOWS is defined. this shouldn't happen while compiling under Ubuntu ;) are you using the procedure described in Readme.txt?

---

### Post by TuxDevil on 2008-02-06
> **Heinzelotto said:**
> this error occures because TC_WINDOWS is defined. this shouldn't happen while compiling under Ubuntu ;) are you using the procedure described in Readme.txt?

Yes.  I did a clean unzip of the source.  Applied your patch then ran:

$ make WX_ROOT=/usr/src/wxWidgets-2.8.7 wxbuild
Configuring wxWidgets library...
Building wxWidgets library...
/usr/src/wxWidgets-2.8.7/src/gtk/gsockgtk.cpp:134: warning: ‘wxDummyGsockVar’ defined but not used

$ make
Compiling Buffer.cpp
...
Compiling MainFrame.cpp
Forms/MainFrame.cpp:23:32: error: TravelerDiskWizard.h: No such file or directory
In file included from Forms/MainFrame.cpp:24:
Forms/VolumeCreationWizard.h:13:44: error: TravelerMountOptionsWizardPage.h: No such file or directory
make[1]: *** [Forms/MainFrame.o] Error 1
make: *** [all] Error 2

---

### Post by Guenter on 2008-02-06
und how can I "undefine" TC_WINDOWS? Sorry, not a pro ;)

---

### Post by Heinzelotto on 2008-02-06
I am creating the .deb right now and had the same error. I have no idea why this error didn't occur the first time i tried to compile. Maybe truecrypt changed something in the source-archive (i downloaded a new copy for building the .deb)

---

### Post by Heinzelotto on 2008-02-06
> **Guenter said:**
> und how can I "undefine" TC_WINDOWS? Sorry, not a pro ;)

if you want an easy way to solve this problem, just remove/comment out the #includes to the missing files in the following files:
Main/Forms/VolumeCreationWizard.h
Main/Forms/MainFrame.cpp

---

### Post by Heinzelotto on 2008-02-06
Sorry for tripleposting, BUT:

I finally built Truecrypt for Ubuntu x86_64! see [this post]("http://ubuntuforums.org/showpost.php?p=4280471&postcount=2") for information

have fun :=)

---

### Post by TuxDevil on 2008-02-06
> **Heinzelotto said:**
> if you want an easy way to solve this problem, just remove/comment out the #includes to the missing files in the following files:
Main/Forms/VolumeCreationWizard.h
Main/Forms/MainFrame.cpp

This worked perfectly.  Thanks for the help.  I'll give the DEB a try also and let you know how that works out.

Thanks again!

---

### Post by Gumper on 2008-02-06
> **Heinzelotto said:**
> Sorry for tripleposting, BUT:

I finally built Truecrypt for Ubuntu x86_64! You can download and try it here: [http://rapidshare.com/files/89758961/truecrypt_5.0-0ubuntu1_amd64.deb.html](http://rapidshare.com/files/89758961/truecrypt_5.0-0ubuntu1_amd64.deb.html)

have fun :=)

I tried installing our deb and I get the following message:

Could not open 'truecrypt_5.0-0ubuntu1_amd64.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

---

### Post by Heinzelotto on 2008-02-06
> **Gumper said:**
> I tried installing our deb and I get the following message:

Could not open 'truecrypt_5.0-0ubuntu1_amd64.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

did you try re-downloading the package to eliminate the risk of the file being corrupted during download? Or did your download-manager set the wrong permissions? check that too, please :)

if that doesn't work, try installing it from the commandline with ```
sudo dpkg -i /path/to/the/file.deb
```

that should give a more precise output.

hope this helps you,
Heinzelotto

---

### Post by Cappy on 2008-02-06
> **Heinzelotto said:**
> Sorry for tripleposting, BUT:

I finally built Truecrypt for Ubuntu x86_64! You can download and try it here: [http://rapidshare.com/files/89758961/truecrypt_5.0-0ubuntu1_amd64.deb.html](http://rapidshare.com/files/89758961/truecrypt_5.0-0ubuntu1_amd64.deb.html)

have fun :=)

Thanks; It works perfectly.

---

### Post by Gumper on 2008-02-06
> **Heinzelotto said:**
> did you try re-downloading the package to eliminate the risk of the file being corrupted during download? Or did your download-manager set the wrong permissions? check that too, please :)

if that doesn't work, try installing it from the commandline with ```
sudo dpkg -i /path/to/the/file.deb
```

that should give a more precise output.

hope this helps you,
Heinzelotto


I downloaded it again and it appears ok now.

Thanks!

---

### Post by skralljt on 2008-02-06
Argh I was hoping that this was going to be it, and with 5.0 I would finally be able to use truecrypt with ext2 or ext3.  I have been biting my fingernails, as lame as that sounds, waiting for the day I can finally format my 750 GB christmas present with whirlpool and aes and twofish.  Oh well, back to waiting.  I hope that deb you provided works!
EDIT:  I have finally got it working, thanks to that .deb posted on rapidshare.  Bless you Heinzelotto!  Bless you!

---

### Post by anitract on 2008-02-06
I was *this close* to installing this...until I started reading other postings of an apparant lack of command line features that were in 4.3a...like no ability to create a crypt...um, why remove this sort of thing?

---

### Post by malrost on 2008-02-06
thanks Heinzelotto -- the .deb worked like a charm

---

### Post by amorangi on 2008-02-07
Thanks for the deb.

The problem (feature?) I now have come across is creating hidden volumes - I get the message "The selected feature is currently not supported on your platform". Do I have to revert to CL?

---

### Post by Heinzelotto on 2008-02-07
hmm, i tried it on a mac with the mac-version, same "problem" there. Does anybody know whether it worked in one of the last (linux-)versions via command-line?
I'm pretty confident though that it will be implemented in one of the next versions.

---

### Post by meho_r on 2008-02-07
Yep, in 4.3a hidden volume can be created from CLI. In 5 almost nothing can be done from CLI. At least, cannot be created. What were they thinking?:confused:

---

### Post by amorangi on 2008-02-07
```
The following features are planned to be implemented in future versions:

    * Parallelized encryption/decryption

    * Ability to create hidden volumes on Mac OS X and Linux 
```

This is hopeless.

---

### Post by Heinzelotto on 2008-02-07
> **amorangi said:**
> ```
The following features are planned to be implemented in future versions:

    * Parallelized encryption/decryption

    * Ability to create hidden volumes on Mac OS X and Linux 
```

This is hopeless.

why hopeless? it is at least planned

---

### Post by anitract on 2008-02-08
Well the TC forums are finally up!  Maybe we should address some of our problems there?

---

### Post by Worried on 2008-02-09
I managed to compile successfully Truecrypt 5.0 on my Ubuntu 7.10 amd64. Heinzelotto deb won't install on my on 7.10 (dependency issues), so I decided to start from scratch using his patch.
The steps followed are here, let's hope they can be useful to someone. I hope I didn't forget anything, feel free to comment and correct.
[I][INDENT]

$ sudo apt-get install libfuse-dev
$ cd /usr/src/
$ sudo tar xvzf wxWidgets-2.8.7.tar.gz
Let’s suppose the truecrypt sources and the patch you downloaded are in your home directory
$ cd
$ gunzip  truecrypt_64bit.txt.gz
$ tar xvzf TrueCrypt 5.0 Source.tar.gz
You got the tar.gz version, didn’t you?
$ cd truecrypt-5.0-source/
$ patch -p1 <../truecrypt_64bit.txt
There you go, follow the Truecrypt provided Readme.txt
$ make WXROOT=/usr/src/wxWidgets-2.8.7 wxbuild
$ make
Please Keep in mind that Debian and Ubuntu discourage to trash with manually compiled binaries (e.g binaries you compiled outside the ubuntu/debian building system, and install bypassing dpkg, apt-get, synaptic and all the rest of the funny circus) the /usr/bin and the other system directories.
If you decide to install manually/using a foreign script, consider placing stuff in /usr/local/* .
I must say that using a different directory (such as you home) from /usr/src to place the wxWigdet stuff could probably save you from sudoing and/or becoming root. But I did not try (I will). Sudoing is necessary to install libfuse-dev, anyhow.[/INDENT][/I]
I'm wondering that, if Heinzelotto can produce the debian source skeleton used to produce the deb, we could contribute to the truecrypt-installer's work with an installer for 5.0.
Let me know, and thanks for your work,

---

### Post by Laughing Yogi on 2008-02-09
Ok, the amd64 package installs great but I don't know where the file is to run it. Please help.

Ok, I found it. /usr/bin/truecrypt

---

### Post by Heinzelotto on 2008-02-10
> **Worried said:**
> 
I'm wondering that, if Heinzelotto can produce the debian source skeleton used to produce the deb, we could contribute to the truecrypt-installer's work with an installer for 5.0.

do you mean [this]("https://launchpad.net/truecrypt-installer") "truecrypt-installer"?

I think this installer was mainly made because you needed to build truecrypt anew whenever you did a kernel-upgrade, but since truecrypt 5 doesn't have this "problem" anymore, i don't really think it would be useful to make a "truecrypt-installer" out of 5.0. The only reason _for_ doing it though are the licensing issues also described on that page:
> 
The Truecrypt licence does not allow distribution of modified sources.
However, it is possible for individuals to assemble all pieces, build
Truecrypt components, and install Truecrypt.


I'm sure posting a source-patch is allowed, but what is not allowed? distributing the .deb or distributing a source-package that will compile under 64-bit linux?

---

### Post by pwinterrowd on 2008-02-11
> **Heinzelotto said:**
> i haven't found any so far and building on my 64-bit machine fails as well. I tried looking for help in the Truecrypt forums, but unfortunately they're down at the moment.

[SIZE="5"]**[COLOR="Red"]EDIT: I have (finally) built a DEB for Ubuntu 64-bit, you can download it [here]("http://rapidshare.com/files/90068414/truecrypt_5.0-0ubuntu1_amd64.deb")[/COLOR]**[/SIZE]

md5sum: ecae7e5966d13e12121cc3289cec5202

if you'd rather like to compile the package yourself, see [this post]("http://ubuntuforums.org/showpost.php?p=4281459&postcount=13") for information.

First:

I tried following the post directions to compile for myself.  Being somewhat of an Ubuntu newbie it required a significant amount of effort and I eventually reached a point where I made no progress for over an hour, lost patience, and just used the DEB above.  (For some reason it's not finding all the wx_Functions when linking and I can't figure out why.)

Second:

After installing from the DEB above I now have truecrypt 5.0 running (thanks) but it won't use keyfiles.  Is anyone else having this issue?  Is it an issue with this compile, or with 5.0 in general I wonder?

---

### Post by MountainX on 2008-02-11
> **pwinterrowd said:**
> 
After installing from the DEB above I now have truecrypt 5.0 running (thanks) but it won't use keyfiles.  Is anyone else having this issue?  Is it an issue with this compile, or with 5.0 in general I wonder?

I am new to Linux, TrueCrypt and all of this. However, the issue you mention may be the same as what I experienced. I installed TrueCrypt 5 on Ubunut 7.10 amd64 (using the deb above). I created my first test TC volume using a file on a USB drive. I used a keyfile. I could not mount it. Mounting failed at the password/keyfile stage. Next I created a test volume *without* a keyfile and it mounted and worked correctly.

---

### Post by MountainX on 2008-02-11
> **anitract said:**
> Well the TC forums are finally up!  Maybe we should address some of our problems there?

I can't get in to the forums. When I try to view them, it asks me to accept the terms, then takes me to a registration page. Registration always fails and it always returns me to the terms page. I cannot even view the existing posts. Anyone else having this problem? 

My Firefox/Ubuntu combination isn't working well, so the TC forum issues may be on my end... At the moment, nothing in Ubuntu is working well for me. I'm going to have to use Windows to get any work done, but I sure am resisting that :(

UPDATE: I just tried the TC forums from my Windows box and I get the same issue - can't register. So I am happy to say, that particular problem has nothing to do with Ubuntu/Firefox on my machine :)

---

### Post by pwinterrowd on 2008-02-11
> **MountainX said:**
> 
UPDATE: I just tried the TC forums from my Windows box and I get the same issue - can't register. So I am happy to say, that particular problem has nothing to do with Ubuntu/Firefox on my machine :)

I get in just fine.  And what you described earlier is exactly what I've seen.  If I create a volume with a keyfile, when I later try to mount it I have to NOT use the keyfile in order to get it to work.  In other words, it's not using the keyfiles at all when creating the volumes.  Since I just installed ubuntu yesterday I've trashed the entire installation and I'm now installing the 32-bit version.  I'll then install truecrypt and see if I have the same issues in 32-bit land.

EDIT:  I just verified that the 32-bit compile of truecrypt has the same bug.

---

### Post by MountainX on 2008-02-12
> **pwinterrowd said:**
> I get in just fine.

I have tried to register from 3 different computers using both IE and Firefox. I cannot register. Maybe you can get in because you are already registered. I wonder if anyone who is new to the TrueCrypt forums can register? I can't.

---

### Post by MountainX on 2008-02-12
> **pwinterrowd said:**
>  If I create a volume with a keyfile, when I later try to mount it I have to NOT use the keyfile in order to get it to work.  
EDIT:  I just verified that the 32-bit compile of truecrypt has the same bug.

Wow - that's a serious bug. I suspect they will have to fix this quickly.

---

### Post by Worried on 2008-02-13
Heinzelotto,
I suppose there's no problem at all with regarding your patch (good job).
The issue I was wondering on was focused more on issues for affecting a wider attempt to make it available to amd64 debian and ubuntu users.
I think the point of the original truecrypt-installer was surely the kernel issue, but also the fact that programs to be packaged should have a clear licence. If it's not the case, they could be rejected by Debian and Ubuntu developers. An installer, as the proprietary flash one, or the java one can require the user to provide the source, thus bypassing some licence issues.
For exampe, you can read more here: [http://lists.debian.org/debian-legal/2006/06/msg00294.html]("http://http://lists.debian.org/debian-legal/2006/06/msg00294.html")
I understand that people from debian-legal ruled the truecrypt licence as unclear, so I expect t hem to reject any official to-be truecrypt package.
Let me know your opinion on this.
I would also like to know if the ubuntu-legal team would have a different view on this.
Anyone knows if truecrypt.com plans to relase official 5.0 amd64 debs?

---

### Post by jcrim on 2008-02-13
Thanks for posting 5.0 debs. Can someone post the latest version 5.0a deb package as well?

-Jesse

---

### Post by sp200606 on 2008-02-15
thanks,
works good, U're a savior!
sp

---

### Post by MountainX on 2008-02-16
> **jcrim said:**
> Thanks for posting 5.0 debs. Can someone post the latest version 5.0a deb package as well?

-Jesse

That sure would be great.

---

### Post by Heinzelotto on 2008-02-16
okay I'll package the new version

EDIT: done, see [post no. 2]("http://ubuntuforums.org/showpost.php?p=4280471&postcount=2") for information and download

---

### Post by zaffod on 2008-02-20
```
# dpkg -i /usr/installs/truecrypt_5.0a-0ubuntu1_amd64.deb 
(Reading database ... 133027 files and directories currently installed.)
Preparing to replace truecrypt 5.0a-0ubuntu1 (using .../truecrypt_5.0a-0ubuntu1_amd64.deb) ...
Unpacking replacement truecrypt ...
dpkg: dependency problems prevent configuration of truecrypt:
 truecrypt depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 truecrypt depends on libfuse2 (>= 2.6); however:
  Package libfuse2 is not installed.
 truecrypt depends on libgcc1 (>= 1:4.2.1); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 truecrypt depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.12.11-0ubuntu1.
 truecrypt depends on libgtk2.0-0 (>= 2.12.0); however:
  Version of libgtk2.0-0 on system is 2.10.11-0ubuntu3.
 truecrypt depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.16.2-0ubuntu1.
 truecrypt depends on libstdc++6 (>= 4.2.1); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
 truecrypt depends on libxdamage1 (>= 1:1.1); however:
  Version of libxdamage1 on system is 1:1.0.3-3.
 truecrypt depends on libfuse2; however:
  Package libfuse2 is not installed.
 truecrypt depends on fuse-utils; however:
  Package fuse-utils is not installed.
dpkg: error processing truecrypt (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 truecrypt
```

I get the above error when I try and install Heinzelotto's deb. Running feisty 64bit version. 
Any help would be appreciated.

---

### Post by zaffod on 2008-02-20
More info: 

After the above occured, I had issues with the software Update feature and had to do
```
apt-get install -f
```
to fix the issue. 

Didn't try installing te deb file again as I figured that's what caused te problem in the first place.

---

### Post by jcrim on 2008-02-20
Thanks Guys!

---

### Post by Keith Hedger on 2008-02-23
Thanks to  Heinzelotto for his patch file compiled perfectly on AMD64 duo, well done that man! :):)

---

### Post by marshmelbo on 2008-02-26
Thanks!   The truecrypt_5.0a-amd64.deb  works great in hardy alpha 5!! 
Many thanks!!!

---

### Post by yaidiot! on 2008-03-08
Got it, thanks for the walkthrough!

---

### Post by amarand on 2008-03-08
Patch worked just fine with Truecrypt 5.1a under CentOS 5.1.  I had to build FUSE but that wasn't a big deal.  I'm sure it was a dependency listed somewhere.  :)

Thank you!

---

### Post by MountainX on 2008-03-09
> **amarand said:**
> Patch worked just fine with Truecrypt **5.1a**

Is that a typo, or has there been a new release that I can't find? Afaik, the latest is 5.0a.

---

### Post by BassKozz on 2008-03-11
v5.1 released yesterday ( 3-10-08 ), can be downloaded here: [http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")
:)

---

### Post by BassKozz on 2008-03-13
> **B/-\ssKozz said:**
> v5.1 released yesterday ( 3-10-08 ), can be downloaded here: [http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")
:)

I got my very 1st Thanks \\:D/ ...
Thank you newbieforever  ):P

---

