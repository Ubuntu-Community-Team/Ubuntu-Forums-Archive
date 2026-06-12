---
title: "amazon downloader help"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by dogsipod on 2008-06-22
hello,

i want to install the amazon mp3 downloader so i can buy drm free music.  however it does not appear to support 64-bit.  i did some searching and found another thread on here where someone said the problem was fixed by installing lib32nss-mdns.  i did that via apt-get.  tried to intsall the downloader again and still got the wrong arch error. could someone please help...i really want high quality drm muscic.  i have a fresh install of 8.04 with the amd 64-bit version. thankyou.


also i like to use yum. i installed it and when i try and run i get this message. how can i fix it as well.
```
$ yum
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.5.2 (r252:60911, Apr 21 2008, 11:17:30) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

If you cannot solve this problem yourself, please send this
message to <yum@lists.linux.duke.edu>.
```

---

### Post by pixel :-) on 2008-06-22
**i want to install the amazon mp3 downloader so i can buy drm free music. **
Use bittorent. :lolflag:

**still got the wrong arch error.**
This will never going to go away,you must use
sudo dpkg --force-architecture -i your_32bit_pakage.deb

**i really want high quality drm muscic.**
Masochist,you discused me,you pervert.

**yum**
Don't use yum,it will conflict with apt-get.don't install anything with it.Heres the solution anyway[https://bugs.launchpad.net/ubuntu/+source/yum/+bug/238013]("https://bugs.launchpad.net/ubuntu/+source/yum/+bug/238013")

---

### Post by dogsipod on 2008-06-22
thanks for the help.  i will not use yum as it seems to be more of a hassle then it's worth.  i just really like the yum list option...there doesn't seem to be a apt-get equivalent...from what i read the man page.  Also bit torrent is not an option.  the force-arch option didn't seem to help. it output the following...
```
s$ sudo dpkg --force-architecture -i amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package amazonmp3.
(Reading database ... 142723 files and directories currently installed.)
Unpacking amazonmp3 (from amazonmp3.deb) ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amazonmp3

```

should i use apt-get to install the missing dependencies...or will this mess up my machine?

---

### Post by Cappy on 2008-06-22
Use
```
sudo dpkg --force-all -i amazonmp3.deb
```

then install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs /usr/bin/amazonmp3
```

---

### Post by dogsipod on 2008-06-22
thanks so much...working perfect right now!

---

### Post by chslaxcoach on 2008-08-17
Thanks so much for this.  I am a professional musician so this is a killer app for me and getting away from the iTunes Store is great.

There is one more thing I had to do to get this to work.  When the Amazon web interface asks you to install the MP3 downloader, there is a very small font link that says:

"If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser."

I also had to install this package

```

sudo aptitude install lib32nss-mdns

```

More info here:

[http://ubuntuforums.org/showthread.php?t=783567&highlight=can%27t+connect+amazon+mp3+downloader](http://ubuntuforums.org/showthread.php?t=783567&highlight=can%27t+connect+amazon+mp3+downloader)

Once I did those two things, I was golden.

Thanks again, folks.

---

### Post by MichiganMan on 2008-09-01
> **chslaxcoach said:**
> 
```

sudo aptitude install lib32nss-mdns

```


Ok, that's just bleeding weird.  

I've been struggling with this one too, even emailed my polite discontent to Amazon last week (given that the LTS of Ubuntu had been out for months now...) So I've been using the windows downloader with wine but thought to peruse the forums before I downloaded my latest purchase.  

Saw this thread.  Like others it suggested installing lib32nss-mdns.  Tried sudo apt-get install lib32nss-mdns, couldn't find package. (32 bit Hardy)  Went to Synaptic, nope, no lib32nss-mdns.  On a lark I tried the sudo aptitude install lib32nss-mdns. 

Aptitude made the difference.  Again couldn't find the package, but this time I got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "lib32nss-mdns"
Couldn't find any package whose name or description matched "lib32nss-mdns"
The following packages are unused and will be REMOVED:
  libboost-date-time1.34.1 libboost-iostreams1.34.1 libboost-signals1.34.1 
  libboost-thread1.34.1 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 819kB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 176985 files and directories currently installed.)
Removing libboost-date-time1.34.1 ...
Removing libboost-iostreams1.34.1 ...
Removing libboost-signals1.34.1 ...
Removing libboost-thread1.34.1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```

Huh, never saw that before... Reinstalled Amazon's Mp3 downloader and the dang thing worked flawlessly...

Effin magic.

I hate magic.

---

