---
title: "Hamachi on Gutsy 64bit"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by k2chris1983 on 2007-10-01
I was wondering if Hamachi will work under Gutsy 64bit and if so whats the work around?

---

### Post by Kilz on 2007-10-01
You might want to post to the Gutsy development sub forum.

---

### Post by k2chris1983 on 2007-10-01
K I post one there, but I thought if it was 64bit i just post here and see if anyone knew?

---

### Post by Kilz on 2007-10-01
> **k2chris1983 said:**
> K I post one there, but I thought if it was 64bit i just post here and see if anyone knew?

No harm done, its just that Gutsy is under development, and other users using Gutsy will probably know the answer to Gutsy questions. Those users can be found in mass in the Gutsy development section. This section is mainly for released versions.

---

### Post by John.Michael.Kane on 2007-10-01
> **k2chris1983 said:**
> I was wondering if Hamachi will work under Gutsy 64bit and if so whats the work around?
You can try compiling the non Pentium version on a Gutsy 64 install [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/)

---

### Post by k2chris1983 on 2007-10-02
> **SD-Plissken said:**
> You can try compiling the non Pentium version on a Gutsy 64 install [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/)

Thanks, i will give that a try today and see if it works.

---

### Post by k2chris1983 on 2007-10-02
Ok, i have installed both of them and the "hamachi-0.9.9.9-20-lnx.tar.gz" package is the first one i installed, but when i execute "hamachi" i get nothing back (I did the setup from README). When i install the "hamachi-0.9.9.9-20-lnx-pentium.tar.gz" I do get an error back:

```


hamachi: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory


```

So i installed the libssl0.9.7 from the "Synaptic Package Manager" and I see libssl0.9.8 is also installed. After installing it I still get the same error.

---

### Post by rdelcueto on 2007-10-09
Until today I thought it was not possible to run Hamachi on a 64bit Linux machine.
A minute ago I was browsing, and found that people running hamachi on Feisty weren't able to run it after upgrading to Gutsy. So there was this "fix" for people who upgraded to Gutsy. I tried it on my 64bit Gutsy computer, and it WORKED! =D

You might want to try it
I followed the instructions in the following link to setup my hamachi. _[HOWTO: Setup Hamachi VPN on Ubuntu]("http://www.computechgroup.com/?p=360")_
Before doing the "hamachi-init" part, just installed the upx-ucl-beta package from apt or synaptic.
Then open up a terminal, go to /usr/bin folder and type:
```
upx -d hamachi
```
Now proceed with hamachi setup... and everything should work.

Hope it helps! =)

-Hamachi Gutsy Fix Post: _[http://ubuntuforums.org/showthread.php?p=3414411]("http://ubuntuforums.org/showthread.php?p=3414411")_

---

### Post by karrotcake on 2007-11-04
Hi,

I was wondering if anybody has got this going on 64bit gutsy xubuntu?
Im having problems; ive run upx, which seems to work, re-run hamachi init, but all I can get  is  Logging in ....>..... failed. Its not a networking issue, i can run it from my laptop with no problems. tuncfg running in debug mode gives me this when i try to connect:

# tuncfg -d
tuncfg: accept() 5 0
tuncfg: open() 6 0
tuncfg: ioctl() 0 ham0
tuncfg: recv() 8 0

# ifconfig ham0
ham0      Link encap:Ethernet  HWaddr 00:FF:4C:B3:5A:21  
              BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:500 
              RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
#dmesg
[   89.510412] tun: Universal TUN/TAP device driver, 1.6
[   89.510417] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

Any help would be much appreciated; I've tried all I can think of; even if somebody could suggest another VPN service that I could use that would be a great help.

---

### Post by tonywhelan on 2008-03-20
> **k2chris1983 said:**
> Ok, i have installed both of them and the "hamachi-0.9.9.9-20-lnx.tar.gz" package is the first one i installed, but when i execute "hamachi" i get nothing back (I did the setup from README). When i install the "hamachi-0.9.9.9-20-lnx-pentium.tar.gz" I do get an error back:

```


hamachi: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory


```

So i installed the libssl0.9.7 from the "Synaptic Package Manager" and I see libssl0.9.8 is also installed. After installing it I still get the same error.
--------------------

I think the Hamachi download page has misleading info about downloads for AMD. It says use the pentium version of the software, but that will cause hamachi-init to produce the libcrypto.so.0.9.7 error message.

If you have an AMD, suggest don't download the lnx-pentium version, just the lnx version.

For the record I have an AMD64 bit machine but am running the 32bit version of Ubuntu Gutsy as the problems with no 64-bit Java were insurmountable (yes I know about the workarounds but they do not work for certain very specific java applets I have to use).

Go to [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/) and select the latest version (at present that's hamachi-0.9.9.9-20-lnx.tar.gz)

You will have to follow the instructions at [http://www.computechgroup.com/?p=360](http://www.computechgroup.com/?p=360) to make it work. Part 1 of those instructions is critical.

---

### Post by Cappy on 2008-03-21
> **tonywhelan said:**
> --------------------

I think the Hamachi download page has misleading info about downloads for AMD. It says use the pentium version of the software, but that will cause hamachi-init to produce the libcrypto.so.0.9.7 error message.


**Ubuntu 64-bit:**
```
sudo apt-get install ia32-libs
```
and
```
sudo ln -s /usr/lib32/libcrypto.so.0.9.8 /usr/lib32/libcrypto.so.0.9.7
```

**Ubuntu 32-bit:**
```
sudo apt-get install libssl0.9.8
```
and
```
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.0.9.7
```

---

