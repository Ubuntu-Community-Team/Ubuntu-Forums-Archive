---
title: "[SOLVED] problems installing Adeona on 64-bit Hardy"
date: 2008-09-20
forum: x86 64-bit Users
---

### Post by stlouisubntu on 2008-09-20
[http://adeona.cs.washington.edu/](http://adeona.cs.washington.edu/)

I have been unable to install Adeona on my Acer Aspire 5100
laptop running 64-bit Ubuntu Hardy GNU Linux.

[http://adeona.cs.washington.edu/linuxinstallguide.html](http://adeona.cs.washington.edu/linuxinstallguide.html)

I have made sure that libssl-dev, OpenSSL, traceroute, and
cron, and build-essential are installed (apt-get confirmed that
the most recent version of each is installed.)

I even added the -m32 on the CFLAGS in the MAKEFILE (where I thought
I was supposed to.)

Can anyone help?  I am looking forwarded to having this application installing and working as I have read good reports about it.

Here is the output following sudo make install:

<code>
Starting Adeona installation...
make[1]: Entering directory `/usr/local/adeona'
gcc -Wall -m32 -D_ADEONA_BUILD_RELEASE_ -O2  /usr/local/adeona/common/
util.o  /usr/local/adeona/common/log.o  /usr/local/adeona/common/
options.o   /usr/local/adeona/crypto/encrypt.o  /usr/local/adeona/
crypto/pbkdf.o  /usr/local/adeona/crypto/hmac.o  /usr/local/adeona/
crypto/prg.o  /usr/local/adeona/crypto/auth_encrypt.o  /usr/local/
adeona/core/ctxtcache.o  /usr/local/adeona/core/sched.o  /usr/local/
adeona/core/state.o  /usr/local/adeona/core/update.o  /usr/local/
adeona/location/webcam.o  /usr/local/adeona/location/ipaddress.o  /usr/
local/adeona/location/landmarks.o  /usr/local/adeona/location/
traceroute.o  /usr/local/adeona/location/location.o  /usr/local/adeona/
location/accesspoint.o /usr/local/adeona/opendht/gateways.o /usr/local/
adeona/app/init.o -lm -lcrypto -o /usr/local/adeona/adeona-init.exe
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/
4.2.3/../../../libcrypto.so when searching for -lcrypto
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/
4.2.3/../../../libcrypto.a when searching for -lcrypto
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libcrypto.so when
searching for -lcrypto
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libcrypto.a when
searching for -lcrypto
/usr/bin/ld: skipping incompatible /usr/lib/libcrypto.so when
searching for -lcrypto
/usr/bin/ld: skipping incompatible /usr/lib/libcrypto.a when searching
for -lcrypto
/usr/bin/ld: cannot find -lcrypto
collect2: ld returned 1 exit status
make[1]: *** [/usr/local/adeona/adeona-init.exe] Error 1
make[1]: Leaving directory `/usr/local/adeona'
Could not build Adeona programs.
make: *** [install] Error 1
</code>

Believe it or not, I resolved this issue by doing the following (after much googling):

<code>
I have downloaded libssl0.9.8_0.9.8e-5ubuntu1_i386.deb (from Ubuntu launchpad) and extracted this and copied the missing files to the right place and created required soft links (all as root).
# mkdir /tmp/libssl
# dpkg -x libssl0.9.8_0.9.8e-5ubuntu1_i386.deb /tmp/libssl
# cp /tmp/libssl/usr/lib/libssl.so.0.9.8 /usr/lib32/
# cp /tmp/libssl/usr/lib/libcrypto.so.0.9.8 /usr/lib32/
# ln -s /usr/lib32/libssl.so.0.9.8 /usr/lib32/libssl.so
# ln -s /usr/lib32/libcrypto.so.0.9.8 /usr/lib32/libcrypto.so
</code>

That was from the following blog (for proper credit):
[http://tamastarjanyi.blogspot.com/2007/09/ubuntu-gutsy-64bit-wine-misses-ssl.html](http://tamastarjanyi.blogspot.com/2007/09/ubuntu-gutsy-64bit-wine-misses-ssl.html)

Then I tried sudo make install again and got the following 
error:

/usr/bin/ld:  skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libgcc.a

After more googling,
   sudo aptitude install gcc-multilib  cured that error.

Now the output following sudo make install is as follows

<code>
Starting Adeona installation...
make[1]: Entering directory `/usr/local/adeona'
gcc -Wall  -D_ADEONA_BUILD_RELEASE_ -O2 -m32  /usr/local/adeona/common/util.o  /usr/local/adeona/common/log.o  /usr/local/adeona/common/options.o   /usr/local/adeona/crypto/encrypt.o  /usr/local/adeona/crypto/pbkdf.o  /usr/local/adeona/crypto/hmac.o  /usr/local/adeona/crypto/prg.o  /usr/local/adeona/crypto/auth_encrypt.o  /usr/local/adeona/core/ctxtcache.o  /usr/local/adeona/core/sched.o  /usr/local/adeona/core/state.o  /usr/local/adeona/core/update.o  /usr/local/adeona/location/webcam.o  /usr/local/adeona/location/ipaddress.o  /usr/local/adeona/location/landmarks.o  /usr/local/adeona/location/traceroute.o  /usr/local/adeona/location/location.o  /usr/local/adeona/location/accesspoint.o /usr/local/adeona/opendht/gateways.o /usr/local/adeona/app/init.o -lm -lcrypto -o /usr/local/adeona/adeona-init.exe
collect2: ld terminated with signal 11 [Segmentation fault]
/usr/bin/ld: i386:x86-64 architecture of input file `/usr/local/adeona/common/options.o' is incompatible with i386 output
make[1]: *** [/usr/local/adeona/adeona-init.exe] Error 1
make[1]: Leaving directory `/usr/local/adeona'
Could not build Adeona programs.
make: *** [install] Error 1
</code>

Now I am at a loss and do not even know what to type
in for a google search.  I have been unable to get a respone
of any kind from the Adeona team (via posting on their forum
and direct e-mails to them.

Any assistance or ideas would be much appreciated.  By their 
installation notes, it does appear possible to install it 
on 64-bit linux.


Thanks,

stlouisubntu

---

### Post by kernelzilla on 2008-09-25
Hello!

I ran into the same problem, and found the solution:

Use [getlibs <link>]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to correctly install the 32 bit version of libssl:

getlibs -l libcrypto.a

make install will work after that!

---

### Post by stlouisubntu on 2008-10-01
Thanks for the response.  I tried your getlibs suggestion,
but I still get the following error

collect2: ld terminated with signal 11 [Segmentation fault]
/usr/bin/ld: i38686-64 architecture of input file `/usr/local/adeona/common/options.o' is incompatible with i386 output
make[1]: *** [/usr/local/adeona/adeona-init.exe] Error 1
make[1]: Leaving directory `/usr/local/adeona'
Could not build Adeona programs.
make: *** [install] Error 1

I think that your

getlibs -l libcrypto.a

suggestion would have solved the error I was getting as mentioned in my 
second paragraph of my original post, but I had already solved that one
by downloading and installing the libcrpto 32-bit libraries and making
the symbolic links as I indicated.

Thanks for the attempted solution anyway.

Any other ideas?  The other fixes I have already implemented may have messed things up, but I do not know how to undo them (or even if that
would help at this point.)

Any assistance or other ideas would be much appreciated.

---

### Post by Yellow Pasque on 2008-10-02
I would suggest running *make clean* and trying again. I'm currently trying to build it. I'll let you know how it goes.

EDIT: Did you ever run configure again after getting all the proper libraries?

---

### Post by Yellow Pasque on 2008-10-02
It built quickly on my system. If make clean doesn't work, just delete the entire adeona directory and re-extract it (the build process didn't install anything outside of the directory).

You do know that getlibs isn't installed by default? (the directions don't mention that). Get it here if you don't have it. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I added the line:
```
CFLAGS += -m32
```
right after
```
CFLAGS := -Wall
```

Also, make sure you have traceroute and ia32-libs installed:
```
sudo apt-get install ia32-libs traceroute
```

If you have any other problems, I can try and build you a .deb, but let's try and avoid that :)

---

### Post by stlouisubntu on 2008-10-05
Thank you.  Thank you!

Problem solved.  Great advice.  I really appreciate it.

---

