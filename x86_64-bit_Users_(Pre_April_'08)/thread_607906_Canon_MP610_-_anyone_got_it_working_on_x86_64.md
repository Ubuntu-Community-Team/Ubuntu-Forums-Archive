---
title: "Canon MP610 - anyone got it working on x86_64?"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbernardo on 2007-11-09
Hi,
I just bought a Canon Pixma MP610. I was hoping to at least getting it to print using the MP600 drivers, but it seems that they are only available for 32 bit, and have color problems at high resolution when used with the 610. Also, the scanner doesn't work at all.
Anyone got it to work (apart from using turboprint drivers)?

---

### Post by daritter on 2008-01-08
Hi, 
there are Canon-drivers for the MP610, but those are 32bit as well, directly on the canon-site:
[http://software.canon-europe.com/software/0028478.asp?model=](http://software.canon-europe.com/software/0028478.asp?model=)

Now the tricky part are is running 64bit: I managed to get my MP600 working under 64bit by extracting the rpms, copying some files around and set two links for libtiff and libpng. I left out everything I don't need: Just the cups-filter, printing-binary and PPD-file. Since the driver should be very similar, this might work for you with minor modifications:

First, I extracted the rpms
```

rpm2cpio cnijfilter-common-2.70-1.i386.rpm | cpio -ivd
rpm2cpio cnijfilter-mp600-2.70-1.i386.rpm | cpio -ivd

```

Then copy the needed files to proper locations: First, the cups-Filter:

```
sudo cp usr/lib/cups/filter/pstocanonij /usr/lib/cups/filter/
```
Then the closed-source binary along with its shared librarys
```
sudo cp usr/local/bin/cifmp600 /usr/local/bin/
sudo cp usr/lib/lib* /usr/lib32
```
And the configuration-files for the binary:
```
sudo cp -r usr/lib/bjlib /usr/lib
```
These need to be in /usr/lib/bjlib.  If these Files are not found or not readable, cifmp600 will abort saying "Error: invalid printer model" and printing will silently fail (Great error-message by the way, took me some time to figure that out. Tried to put these in /usr/lib32 as well)

And, at last the PPD-file, which i modified according to [ubuntuusers.de]("http://wiki.ubuntuusers.de/Canon-Drucker#head-d442123c5638494a2189df5fc28f7759e5287de0")
```
sudo cp usr/share/cups/model/canonmp600.ppd /usr/share/ppd/custom/
```

The driver needs the ia32-libs package and two symlinks to find libtiff and libpng (which one can see by running "ldd /usr/local/bin/cijmp600"):

```
sudo apt-get install ia32-libs
cd /usr/lib32
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libpng12.so.0.15.0 libpng.so.3
sudo ldconfig
sudo /etc/init.d/cupsys restart
```

Hopefully this is helpfull, cheers
daritter

---

### Post by JohnAspinall on 2008-01-23
Hi.  I'm attempting to follow (and modify) your clear instructions for an MP610 on Gutsy 64-bit.  I unpacked the 32-bit .deb file, and did the installation as you suggest.  There are several shared libraries to put in /usr/lib32 but your suggestion to run ldd on the driver was excellent - I can be confident that I got everything that it needs.

OK, so far so good.  But... When I print something, the printer wakes up, and then spools a blank page through.  Nothing else.  I have run the printer config tool to inform it of the "custom" ppd file.  One possibility is that I didn't correctly make the modifications to the ppd file that you point to.  (My German is non-existent, sorry.)  But surely *something* would appear!

I can run the driver at a terminal, and no "invalid printer model" message appears.
Looking for suggestions, thanks in advance.
 -John

---

### Post by daritter on 2008-01-25
Hello again,

I think that you should be able to print a Postscript-File using the driver itself, something like
```
/usr/local/bin/cifmp610 testpage.ps
```
If that works, there is a CUPS-Problem.

maybe it would help to set the CUPS-Loglevel to "debug" in /etc/cups/cupsd.conf:
```
# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning
```
and then monitor the /var/log/cups/access_log and error_log when printing to see if there are any errors

I attached a Patch for the canonmp600.ppd, perhaps this helps to verify your ppd.

Cheers and good luck
daritter

---

