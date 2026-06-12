---
title: "Debhelper problem building freenx from sources"
date: 2006-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrisb on 2006-01-04
I follow the instructions on building freenx from source for amd64 ubuntu breezy. ( [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) )

I get the source downloaded but when I do "sudo apt-get build-dep nx freenx" it complains:
E: Build-Depends dependency for nx cannot be satisfied because no available versions of package debhelper can satisfy version requirements

It seems the source is dependant on debhelper version > 5, but I can only find a version 4.9.5 package.

Anybody know how/where I can obtain a debhelper > 5 package for ubuntu breezy amd64?

I don't mind building it from source package. 

Any help will make me glad :D 

Christian B

---

### Post by rth on 2006-01-10
I have the same problem and I'm looking for a solution.

Edit:

Here's what I get:
```
dpkg-buildpackage: source package is nx
dpkg-buildpackage: source version is 1.4.92+1.5.0-7
dpkg-buildpackage: source changed by Stefan Lippers-Hollmann <s.l-h@gmx.de>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5.0.0) libjpeg-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```

I have libjpeg62-dev but didn't see a libjpg-dev in Synaptic. I noticed that Dapper has debhelper 5.0.7 so far ([https://launchpad.net/distros/ubuntu/dapper/i386/debhelper/5.0.7ubuntu2](https://launchpad.net/distros/ubuntu/dapper/i386/debhelper/5.0.7ubuntu2)).

---

### Post by rth on 2006-01-10
If you download the .deb from the URL above, then you can do this to install it:
```
sudo dpkg -i debhelper_5.0.7ubuntu2_all.deb
```
I also installed libjpeg62-dev, but I get this error further along the install:
```
for i in *; do \
        if test -d $i  && test -f $i/Makefile; then \
                -/usr/bin/make -C $i clean; \
        fi; \
done
/bin/sh: -/usr/bin/make: No such file or directory
/bin/sh: -/usr/bin/make: No such file or directory
make: *** [clean] Error 127
Build command 'cd nx-1.4.92+1.5.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed
rth@u64:~/Desktop/freenxSource$ ls /usr/bin/mak*
/usr/bin/make  /usr/bin/makedepend  /usr/bin/make-memtest86+-boot-floppy
```
Funny, it looks like /usr/bin/make is there.

---

### Post by rth on 2006-01-13
Does the '-' before the /usr/bin/make mean anything?

---

### Post by rth on 2006-01-16
I've done some searching and I can't find anyone else with the same sort of issue. Anyone have any thoughts?

---

### Post by sjpwong on 2006-01-17
[QUOTE=rth]Does the '-' before the /usr/bin/make mean anything?[/QUOTE]

That looks like a dud.  I edited ./nx-1.4.92+1.5.0/debian/rules and removed it.

Until the next error emerged:

```
for i in *; do \
        if test -d $i  && test -f $i/Makefile; then \
                 /usr/bin/make -C $i clean; \
        fi; \
done
make[1]: Entering directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nxdesktop'
rm -f *.o crypto/*.o *~ vnc/*.o vnc/*~ nxdesktop rdp2vnc
make[1]: Leaving directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nxdesktop'
make[1]: Entering directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nx-X11'
/usr/bin/make -f xmakefile clean
make[2]: Entering directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nx-X11'
make[2]: xmakefile: No such file or directory
make[2]: *** No rule to make target `xmakefile'.  Stop.
make[2]: Leaving directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nx-X11'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/simon/src/freenx/nx-1.4.92+1.5.0/nx-X11'
make: *** [clean] Error 2
Build command 'cd nx-1.4.92+1.5.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed
```

Looks like this is going to be fun :( 

So next I went into the ./nx-1.4.92+1.5.0/nx-X11 directory and did a "make World".  That failed after a little while.  At least xmakefile was now in that directory.  (maybe there was a target for it I didn't look).

I then returned to my src root dir and tried again...

It's still building so I'll update this later...

---

### Post by sjpwong on 2006-01-17
Well, it finished building and after adding in some dependencies it has installed OK too :-)

Time for bed though so I'll be testing it further later.

Good Luck!

---

### Post by Zenbloke on 2006-01-24
Hi,
How did you get on with the install ?
I'm about to try your fix tonight, on my Kubuntu AMD64 Breezy 5.10 build.

Cheers

---

### Post by chrismutel on 2006-01-29
I was able to successfully compile from source (after help from above), and change my port number - when I try to connect from my windows machine, it authenticates, and opens full screen like it is loading gnome, and then sits there until I get a pop-up "no response from server." Any ideas?

Running 5.10, AMD64, clean install except for Apache2, firestarter, chkrootkit, and freenx.

Thanks

---

### Post by sjpwong on 2006-01-29
[QUOTE=chrismutel]...
Running 5.10, AMD64, clean install except for Apache2, firestarter, chkrootkit, and freenx.
[/QUOTE]

Did you open up the port in firestarter?  I haven't had time to do any further testing on my installation yet.

---

### Post by chrismutel on 2006-01-30
Yes - It authenticates (if the port isn't open, then you get an error message earlier in the process). Still stuck after trying random fixes...

---

### Post by mikalh on 2006-02-06
Have you selected "Enable SSH encryption of all traffic" in the client? Unless you do so, the X11 traffic goes over some higher port, and in that case you'd need to open it.

I've build the Kanotix freenx on Dapper AMD64, and after much messing around with where it thinks X is, it *almost* works: now everythings works as far as negotiation, then I just get

Error: Lost connection to peer proxy on FD#12.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry

with no other explanation *anywhere* at all.

I'm tempted to try building from svn, but I guess I have better things to do. I wonder when this will be in Ubuntu proper?

---

