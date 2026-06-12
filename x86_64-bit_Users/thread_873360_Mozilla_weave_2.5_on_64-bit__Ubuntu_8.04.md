---
title: "Mozilla weave 2.5 on 64-bit / Ubuntu 8.04"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by ariel on 2008-07-28
Just wondering if anyone succeeded in building the xpi for Mozilla weave 2.5 for ubuntu 8.04 - 64 bits. 

If so, mind posting the resulting package or (better) a step by step howto? 

I'm running into hundreds of error messages when trying the make. All dependencies seem to be satisfied, I am following Mozilla weave wiki "generic" linux instructions, but no joy.

thanks

---

### Post by Yellow Pasque on 2008-07-29
Obsolete

---

### Post by ariel on 2008-07-29
> **Temüjin said:**
> I successfully built it and it passed all of its built-in tests. You have to enable the "pre-released" (hardy-proposed) update repo in System->Administration->Software Sources and install the xulrunner-1.9-dev package if you want to build it. I'll attach the .xpi in case something goes wrong for you.

```
sudo apt-get install xulrunner-1.9-dev mercurial build-essential
hg clone http://hg.mozilla.org/labs/weave weave
cd weave
hg up -r c8bce0724360
make sdkdir=/usr/lib/xulrunner-devel-1.9.0.1 xpi
firefox-3.0 weave-Linux.xpi 

```

Thanks! I installed the .xpi and firefox stopped complaining about the crypto module; weave seems to run fine now; it takes a while to login but seems to be working.

---

### Post by milstein on 2008-08-02
Thanks for sharing, it's working great! :)

---

### Post by ariel on 2008-08-05
> **milstein said:**
> Thanks for sharing, it's working great! :)

Have you been able to get weave to synchronize? The 64 bit xpi worked fine for me when I installed, but during the last 5 days or so everytime I try to manually synchronize I get a "Server Busy" error message. This is not only with FF3 in Ubuntu/64 but with WinXP as well.

---

### Post by gecka on 2008-08-05
Same "server busy" error for me. Anyone?

---

### Post by jlh on 2008-08-06
Same here.  The server is always busy.

---

### Post by ariel on 2008-08-17
> **jlh said:**
> Same here.  The server is always busy.

My solution to the continous Weave issues: the foxmarks add-on. You can set it up to sync manually, works in 64 and 32 bits, all OS's supported, the server is never busy. Fits the bill.

---

### Post by gecka on 2008-08-17
Well weave is in beta test so downtime may happen frequently.

Anyway, the server busy problem got solved by itself for me.

---

### Post by xur17 on 2008-09-11
I have built the most recent version for linux 64 bit:

[http://www.sigmirror.com/browse/admin/898_jVuau](http://www.sigmirror.com/browse/admin/898_jVuau)

I will try to keep that folder updated with the most recent version, so if a new version comes out, please PM me, and I will build and upload the new version.

---

### Post by RadiusXE on 2008-09-14
> **xur17 said:**
> I have built the most recent version for linux 64 bit:

[http://www.sigmirror.com/browse/admin/898_jVuau](http://www.sigmirror.com/browse/admin/898_jVuau)

I will try to keep that folder updated with the most recent version, so if a new version comes out, please PM me, and I will build and upload the new version.

very thanks

---

### Post by kb9wte on 2008-09-14
> **xur17 said:**
> I have built the most recent version for linux 64 bit:

[http://www.sigmirror.com/browse/admin/898_jVuau](http://www.sigmirror.com/browse/admin/898_jVuau)

I will try to keep that folder updated with the most recent version, so if a new version comes out, please PM me, and I will build and upload the new version.

Thanks, you rock :guitar:

---

### Post by kruykaze on 2008-10-17
2.7 is out can't find an compiled one for 64 bit ubuntu

---

### Post by xur17 on 2008-10-17
> **kruykaze said:**
> 2.7 is out can't find an compiled one for 64 bit ubuntu

I have compiled the 64 bit for linux, and the 0.2.7 version has been added here: [http://www.sigmirror.com/browse/admin/898_jVuau](http://www.sigmirror.com/browse/admin/898_jVuau)

Anyone can PM me in the future, and I will compile and upload the newest version since I do not check this thread regularly.

---

### Post by kruykaze on 2008-10-18
> **xur17 said:**
> I have compiled the 64 bit for linux, and the 0.2.7 version has been added here: [http://www.sigmirror.com/browse/admin/898_jVuau](http://www.sigmirror.com/browse/admin/898_jVuau)

Anyone can PM me in the future, and I will compile and upload the newest version since I do not check this thread regularly.

Man you ROCK!!!
Thanks a lot.

---

### Post by kruykaze on 2008-12-23
0.2.7.1 is out if you could compile when you get a chance.thanks again :)

---

### Post by Lanrat on 2008-12-26
Im also waiting for 0.2.7.1

Thanks for the compiles!

---

### Post by Yellow Pasque on 2008-12-26
EDIT: Go further down this thread for latest version of weave

---

### Post by portis on 2008-12-28
Thanks Temüjin, 

but the newest version is 0.2.95. I tried to compile it, but got lots of erros, could you please upload on? Thanks.

---

### Post by portis on 2008-12-28
Thanks a lot. :)

---

### Post by kruykaze on 2008-12-28
> **Temüjin said:**
> I built the latest mercurial source (weave 0.2.95) with Ubuntu 8.10/Mozilla 1.9.0.5. If you want me to build 0.2.7.1, kindly point me to a source tarball for it.

EDIT: 0.2.93 -> 0.2.95

Thanks a bunch. how do you compile it.so i can do it by my self from now on

---

### Post by kruykaze on 2008-12-28
How about 2.7.1 for people that are not using FF 3.1 beta.

---

### Post by Yellow Pasque on 2008-12-29
I can't find a source tarball for weave 0.2.7.1, and I can't revert with mercurial because there's no seperate hg revision for it (the maintainer didn't make one).
[https://labs.mozilla.com/forum/comments.php?DiscussionID=4889&page=1#Item_0](https://labs.mozilla.com/forum/comments.php?DiscussionID=4889&page=1#Item_0)

For those asking how I built it from source, I'm not sure what to tell you because I can't successfully build weave with a fresh install of Ubuntu myself. IIRC, I had to do something strange like copy a bunch of header files from /usr/include/nspr and /usr/include/nss. The Mozilla SDK doesn't seem to be layed out correctly in Debian/Ubuntu.

---

### Post by kruykaze on 2008-12-29
> **Temüjin said:**
> I can't find a source tarball for weave 0.2.7.1, and I can't revert with mercurial because there's no seperate hg revision for it (the maintainer didn't make one).
[https://labs.mozilla.com/forum/comments.php?DiscussionID=4889&page=1#Item_0](https://labs.mozilla.com/forum/comments.php?DiscussionID=4889&page=1#Item_0)

For those asking how I built it from source, I'm not sure what to tell you because I can't successfully build weave with a fresh install of Ubuntu myself. IIRC, I had to do something strange like copy a bunch of header files from /usr/include/nspr and /usr/include/nss. The Mozilla SDK doesn't seem to be layed out correctly in Debian/Ubuntu.

Well at least i know i'm not doing something wrong thank you.:D

---

### Post by kruykaze on 2009-01-03
2.9.6 is out.Does it work with FF 3.0.5?

---

### Post by graingert on 2009-01-03
Weave 0.2.96 is out, can we have a recompile?

---

### Post by Yellow Pasque on 2009-01-04
> **graingert said:**
> Weave 0.2.96 is out, can we have a recompile?
Here you go.

---

### Post by kruykaze on 2009-01-04
Is anybody getting this error? "Component returned failure code: 0x80004005"

---

### Post by kruykaze on 2009-01-06
There we go again with 2.97 :(
is there a live cd or thumbstick image I can use to compile my own since ubuntu 8.10 is not working?
Thanks.

---

### Post by Yellow Pasque on 2009-01-07
0.2.97

---

### Post by kruykaze on 2009-01-08
Is it working for you guys? now it says:
 Service.Main	WARN	Some engines did not sync correctly

---

### Post by gecka on 2009-01-09
> **kruykaze said:**
> Is it working for you guys? now it says:
 Service.Main	WARN	Some engines did not sync correctly

Working and syncing well for me.

Maybe you should activate your 0.3 account here [https://services.mozilla.com/0.3/api/register/activate](https://services.mozilla.com/0.3/api/register/activate)

---

### Post by kruykaze on 2009-01-09
> **gecka said:**
> Working and syncing well for me.

Maybe you should activate your 0.3 account here [https://services.mozilla.com/0.3/api/register/activate](https://services.mozilla.com/0.3/api/register/activate)

I have 0.3 activated and using FF 3.05.
It didn't wanna sync I erased all data from server using curl.
Still didn't sync.
Changed the password and then it started syncing but only using the old password (go figure!)And when i say started syncing I mean it says so but doesn't here's the log: 
```
2009-01-09 00:41:11	Chrome.Window	INFO	Login successful
2009-01-09 00:41:18	Engine.Clients	INFO	1 outgoing items pre-reconciliation
2009-01-09 00:41:19	Engine.Bookmarks	INFO	0 outgoing items pre-reconciliation
2009-01-09 00:41:19	Service.Main	INFO	Sync completed successfully
```
Also if i try to create new account here's what i see attached pic: 
[IMG]http://i41.tinypic.com/331n1o2.jpg[/IMG]
And by the way i am using 2.97 from this thread and going nuts i havn't been able to sync since 2.3 i think

---

### Post by Yellow Pasque on 2009-01-09
kruy: Try re-downloading weave 0.2.97 from the above post. I just pulled the latest mercurial source and there were a lot of changes (although the version is still 0.2.97).

---

### Post by kruykaze on 2009-01-09
> **Temüjin said:**
> kruy: Try re-downloading weave 0.2.97 from the above post. I just pulled the latest mercurial source and there were a lot of changes (although the version is still 0.2.97).

From post 30? That's where i got it from and i just uninstalled it and installed again.Still the same thing.
cant start a new account also it logs in with any password i type in.
I am getting desperate .
I'll try reverting to 2.3 or something and disable updates.

---

### Post by kruykaze on 2009-01-09
OK reverted back to 2.7 (from this thread) and now i can sync using my disk.se (actually works!) but not mozilla severs.

---

### Post by Yellow Pasque on 2009-01-09
> **kruykaze said:**
> OK reverted back to 2.7 (from this thread) and now i can sync using my disk.se (actually works!) but not mozilla severs.
I remember reading something about this on the weave forum. Weave is in transition from 0.2 to 0.3 server, so not everything works properly on either one.

---

### Post by Yellow Pasque on 2009-01-09
For those that wanted to build their own weave:
```
sudo apt-get install xulrunner-1.9-dev mercurial build-essential libssl-dev python
cd ~/
hg clone http://hg.mozilla.org/labs/weave weave
cd weave
```

Now you have to edit the src/Makefile.
```
cd ~/weave/src
gedit Makefile
```

Here's the diff output (add the bolded stuff at the appropriate line numbers) :
```
163,165c163
<           -I$(sdkdir)/sdk/include **\**
<           **-I/usr/include/nss \**
<           **-I/usr/include/nspr**
---
>           -I$(sdkdir)/sdk/include
220c218
<               -fno-common **-fshort-wchar** -pthread \
---
>               -fno-common -pthread \

```
Now, you can build:
```
cd ~/weave
make sdkdir=/usr/lib/xulrunner-devel-1.9.0.6 xpi
```

Let me know if you run into issues building.

---

### Post by gecka on 2009-01-29
> **Temüjin said:**
> 
Now you have to edit the src/Makefile.
```
cd ~/weave/src
gedit Makefile
```

Here's the diff output (add the bolded stuff at the appropriate line numbers) :
```
163,165c163
<           -I$(sdkdir)/sdk/include **\**
<           **-I/usr/include/nss \**
<           **-I/usr/include/nspr**
---
>           -I$(sdkdir)/sdk/include
220c218
<               -fno-common **-fshort-wchar** -pthread \
---
>               -fno-common -pthread \

```


Seems Makefile file has changed. It is now 122 lines long. So build gives many errors

---

### Post by Yellow Pasque on 2009-02-13
> **gecka said:**
> Seems Makefile file has changed. It is now 122 lines long. So build gives many errors
The Makefile you need to edit is found in ~/weave/src (not ~/weave). Also note that the xulrunner version is now 1.9.0.6 if you updated to FF 3.06:
```
make sdkdir=/usr/lib/xulrunner-devel-1.9.0.**6** xpi
```

---

### Post by gecka on 2009-02-15
Thanks.

Here is 0.2.100

---

### Post by gecka on 2009-03-01
0.2.106

---

### Post by portis on 2009-03-03
64-bit is officially supported since Weave M3 v0.2.100 (February 11th, 2009):
   * Linux X86_64 support (tested on Fedora)

It works perfectly and upgrades smoothly. So no need to upgrade manually.

---

### Post by Yellow Pasque on 2009-03-03
> **portis said:**
> 64-bit is officially supported since Weave M3 v0.2.100 (February 11th, 2009):
   * Linux X86_64 support (tested on Fedora)

It works perfectly and upgrades smoothly. So no need to upgrade manually.

Thanks for the tip. I verified this on Sidux64 (Debian unstable). No need to edit the src/Makefile anymore.

---

