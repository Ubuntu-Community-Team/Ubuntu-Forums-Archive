---
title: "vnc4server broken (libstdc++-libc6.2)"
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by Virtual_Ron on 2008-06-10
HI,

I've been using vnc4server for quite sometime now, and... well, I broke something.   Not sure what I did, but now it will not start.
Here's my vnc.log:

[PHP]Xvnc: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot ope
n shared object file: No such file or directory
xsetroot:  unable to open display 'vulcan:1'
vncconfig: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
xsetroot:  unable to open display 'vulcan:1'
xterm Xt error: Can't open display: vulcan:1
xset:  unable to open display "vulcan:1"
xset:  unable to open display "vulcan:1"
xsetroot:  unable to open display 'vulcan:1'
startkde: Starting up...
xprop:  unable to open display 'vulcan:1'
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kded: cannot connect to X server vulcan:1
DCOP aborting call from 'anonymous-7287' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kcminit_startup: cannot connect to X server vulcan:1
ksmserver: cannot connect to X server vulcan:1
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
xprop:  unable to open display 'vulcan:1'
startkde: Done.

[/PHP]

Looks like I busted some libraries or something.
I've uninstalled vnc4server and reinstalled.
I've tried to install libstdc++-libc6.2, but can't find it.

Any bright ideas?
THANKS!
Ron


[B]Kubuntu 8.04 AMD64bit
Hardy Heron
kernel: 2.6.24-18-generic
4 Gigs Ram
AMD64 X2 Dual 6000+
ATI Radeon X1200
ATI 8.476 video drivers
KDE 3.5.9[/B]

---

### Post by Kilz on 2008-06-10
> **Virtual_Ron said:**
> HI,

I've been using vnc4server for quite sometime now, and... well, I broke something.   Not sure what I did, but now it will not start.
Here's my vnc.log:

Looks like I busted some libraries or something.
I've uninstalled vnc4server and reinstalled.
I've tried to install libstdc++-libc6.2, but can't find it.

Any bright ideas?
THANKS!
Ron


[B]Kubuntu 8.04 AMD64bit
Hardy Heron
kernel: 2.6.24-18-generic
4 Gigs Ram
AMD64 X2 Dual 6000+
ATI Radeon X1200
ATI 8.476 video drivers
KDE 3.5.9[/B]

libstdc++-libc6.2-2.so.3 is not found in Hardy. That version of the library is found in Feisty and Gutsy packages. But I do not recommend you install those packages as they will overwrite a newer version found in Hardy that other applications may need. 
How are you installing vnc4server? What is the version that you had installed? Did you upgrade a Gutsy install to Hardy?

---

### Post by Virtual_Ron on 2008-06-11
> **Kilz said:**
> libstdc++-libc6.2-2.so.3 is not found in Hardy. That version of the library is found in Feisty and Gutsy packages. But I do not recommend you install those packages as they will overwrite a newer version found in Hardy that other applications may need. 
How are you installing vnc4server? What is the version that you had installed? Did you upgrade a Gutsy install to Hardy?

Hmm... thats not very hardy... :)

You are correct, I had installed it on Gutsy, and later did an upgrade to Hardy.   vnc4server still worked until a few days ago... something I installed broke it.  can't remember what.

Not sure what version it is, but I remember using the guide found on this forum... [http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

So... I should not expect to get it working again?
Could someone recommend another vncserver thats easy to set up?

Thanks,
Ron

---

### Post by Kilz on 2008-06-11
> **Virtual_Ron said:**
> Hmm... thats not very hardy... :)

You are correct, I had installed it on Gutsy, and later did an upgrade to Hardy.   vnc4server still worked until a few days ago... something I installed broke it.  can't remember what.

Not sure what version it is, but I remember using the guide found on this forum... [http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

So... I should not expect to get it working again?
Could someone recommend another vncserver thats easy to set up?

Thanks,
Ron

You may have to purge it , clear the apt cache, and then reinstall it. I would also recommend looking at your apt sources list to make sure all the gutsy repositories have been removed.

---

### Post by Virtual_Ron on 2008-06-11
> **Kilz said:**
> You may have to purge it , clear the apt cache, and then reinstall it. I would also recommend looking at your apt sources list to make sure all the gutsy repositories have been removed.

Thanks.   I purged it, cleared the cache, and re-installed it.
Still no go.  Gives the same errors as in my initial post.

If there is no way to get the libstdc++-libc6.2 back, should I just move on?

---

### Post by Kilz on 2008-06-11
> **Virtual_Ron said:**
> Thanks.   I purged it, cleared the cache, and re-installed it.
Still no go.  Gives the same errors as in my initial post.

If there is no way to get the libstdc++-libc6.2 back, should I just move on?

I have no idea what you would mess up if you did install the old library, you could fubar your system making it unusable.

---

### Post by Virtual_Ron on 2008-06-11
> **Kilz said:**
> I have no idea what you would mess up if you did install the old library, you could fubar your system making it unusable.

Well, I try to only fubar my system on ODD months, so I'm gonna pass!

Any recommendations as to a replacement vnc server program?

---

