---
title: "Creative Soundblaster Xi-Fi Fatal1ty Drivers"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ohmycar on 2008-01-23
So I made a post a long time ago about discovering that the drivers Creative released for linux were only for 64-bit operating systems. So I installed the 64-bit version of 7.10 and downloaded the .tar.gz driver file. This is what I did:

```
ashkan@ashkan-desktop:~$ tar -xzvf /home/ashkan/Desktop/XFiDrv_Linux_US-1.04.tar.gz
XFiDrv_Linux_US-1.04/
XFiDrv_Linux_US-1.04/Readme.txt
XFiDrv_Linux_US-1.04/License.txt
XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
XFiDrv_Linux_US-1.04/installer
XFiDrv_Linux_US-1.04/Disclaim.txt
ashkan@ashkan-desktop:~$ cd XFiDrv_Linux_US-1.04
ashkan@ashkan-desktop:~/XFiDrv_Linux_US-1.04$ ./installer
This product only support 64-bit Operating Systems
Setup will now exit

```


Anyone run into this problem before or have any suggestions on what I should/can do about it? I am 100% sure I am running the 64-bit version of 7.10, is there a way I can double check? Thanks.

- Ash

---

### Post by CheShA on 2008-01-23
quick and dirty way might be to 

```

cd /
ls -la
```

And see if you have a link:

```
lrwxrwxrwx   1 root root     4 Nov 17 19:41 lib64 -> /lib
```

or a better, more cromulent way would be to examine the output of 
```
uname -a
```

Here's mine, letting me know I'm running a realtime patched kernel for **x86_64** :
```

Linux chesha 2.6.22-14-rt #1 SMP PREEMPT RT Tue Dec 18 06:37:06 UTC 2007 x86_64 GNU/Linux

```

---

### Post by ohmycar on 2008-01-23
I did

```
uname -m
```

and it said x86_64

So, I know for a fact I am running the 64 bit version.
Anyone have any idea why I get that error then?
My system spec's are in my signature if that helps at all. Thanks.

- Ash

---

### Post by CheShA on 2008-01-23
Well I don't know TBH but I'd guess that not putting "sudo" before ./installer could cause all sorts of wierd and wonderful messages.  (I'd be a bit disappointed if Creative hadn't written it to throw a proper permissions denied error though really)

---

### Post by ohmycar on 2008-01-24
yeah even with sudo it does no good.

```
ashkan@ashkan-desktop:~$ cd XFiDrv_Linux_US-1.04
ashkan@ashkan-desktop:~/XFiDrv_Linux_US-1.04$ sudo ./installer
This product only support 64-bit Operating Systems
Setup will now exit

```

This is quite annoying, I am using the built in soundcard on my motherboard for the time being. :( thanks creative! Anyone know of any third-party drivers that might be available? I tried googling some but the number one result is a thread that I posted lol.

---

### Post by tehmatticus on 2008-01-24
I believe the setup utility uses uname -i to determine the architecture, which will report unknown on ubuntu for some reason.  You can edit the installer to make it use uname -m instead, which will report x86_64 as you said.

---

### Post by ohmycar on 2008-01-24
Ok so changing it to -m worked , but now I come across a new brick wall in my attempt to install this driver. After going through the long agreement and read me files in the terminal the installation finally begins, but this is what happens:

```
Installation is in progress. Please wait...


tar: XFiDrv_Linux_US-1.04: time stamp 2009-09-19 23:31:00 is 52216622.93502055 s in the future
/opt/Creative/XFiDrv_Linux_US-1.04
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'.  Stop.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'.  Stop.
Installation Unsuccessful

```

I tried looking for the config.log but I did not see it in my home folder or in the driver folder.

---

### Post by njparton on 2008-01-24
The 64 bit X-FI drivers released thus far are not compatible with ALSA and therefore cannot be compiled under or work with gutsy.

I'm suffering because of this too :(

I wish creative would get there act together. Not even a half-hearted effort so far...

You may be able to do it with a custom kernel, see here:

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by tehmatticus on 2008-01-24
ohmycar: The reason it failed again this time is because you do not have a compiler installed. 

```
sudo aptitude install build-essential
```

That should get you set up with the correct build environment.

However, I recommend you follow the guide over at: [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by Yellow Pasque on 2008-01-24
I recommend you sell your X-fi to some clueless Windows user and get a soundcard made by a company that supports open-source. Something with a CMI8788 or Envy24 chip should give you comparable sound quality.

---

### Post by tehmatticus on 2008-01-25
And I recommend that you drop your haughty attitude and take your trolling to another forum.  This is a support forum to handle people's problems.  Some of us do dual boot and may want to use our sound cards in windows AND linux.

Please, don't waste our time with your dribble unless you have something meaningful to add.

---

### Post by Yellow Pasque on 2008-01-25
> Some of us do dual boot and may want to use our sound cards in windows AND linux.
My apologies. Haughtiness removed. However, my recommendation was practical and still stands.
> I recommend you sell your X-fi to **a** Windows user and get a soundcard made by a company that supports open-source. Something with a CMI8788 or Envy24 chip should give you comparable sound quality.

---

### Post by ohmycar on 2008-01-25
LoL nice suggestion. heh Well I will try out that guide and post what happens. sigh , thanks Creative!

---

### Post by ohmycar on 2008-01-25
Well, I followed the guide and did what it told me to do, but of course ran into some problems. it is a little late and I will try to figure this out later. I greatly appreciate all the help. Thanks guys!

---

