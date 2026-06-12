---
title: "Canon drivers(bjfilter) finally working on amd64! IP1500, MP series and many others."
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Puru on 2007-10-27
Yatta!

Many canon printers work in linux with proprietary drivers only, mostly bjfilter, downloadable on canon page. Beyond ideological complains about this driver not being free software, the main matter is that only an i386 version has been released.

When I was on i386, I made my mp110 printer work following this

[http://ubuntuforums.org/showthread.php?t=248745&highlight=ip1500](http://ubuntuforums.org/showthread.php?t=248745&highlight=ip1500)

The same steps won't work on amd64: bjfilternor won't find the required libraries. I couldn't find a solution over the internet, I still needed winxp to print.

The solution is so simple: you've got to link libraries in /usr/lib32, not usr/lib! After that, the printer worked like a charm! Editng the .ppd file I could even print at high resolutions (1200 and 2400 dpi).

I found lots of people complaining they couldn't install this filter on their 64 bit systems, so I think this can come useful.

If requested, I can write a step by step tutorial as soon as I've got time and can repeat from scratch on a liveCD, for now be aware that it can be done!

---

### Post by paulmac on 2007-10-27
My ip5000 worked from the install of Gutsy.  This was very nice in that previous releases of Ubuntu did not  work.  A huge step forward in my view.  Keep up the good work.

---

### Post by rsambuca on 2007-10-27
Yes, if you have the time to let us know what you did, I would be very greatful!

---

### Post by GraFF on 2007-10-29
> **Puru said:**
> Yatta!

If requested, I can write a step by step tutorial as soon as I've got time and can repeat from scratch on a liveCD, for now be aware that it can be done!

That would be very appreciated. :)

---

### Post by johnts on 2008-01-19
> **GraFF said:**
> That would be very appreciated. :)

Hi Graff,

   newbie here ... any instructions to get my PIXMA working appreciated. Had installed turbo print drivers for evaluation but no sure how to delete those either.

Regards,
johnts

---

### Post by theharshone on 2008-02-05
could you write a tutorial for this? This is really helpful. I would like to use my printer under linxu without bootinginto windows

---

### Post by rocky_raccoon on 2008-04-20
Would you not tell us how you did it?

---

### Post by Puru on 2008-04-22
I'm very sorry people, believe me, I really had very few time.. :(

About Canon drivers, you have to download Suse drivers from canon website, here's an how-to from another thread.

> **uxworks said:**
> Let me share you with my Pixma ip1500 on Ubuntu (Dapper) experience...

At first I downloaded driver for Linux from Canon site - iP1500Linux.tar.gz
They say it works for SuSE but even on this it's not supported...blah blah ;-)

I extracted the archive
```
tar -xzf iP1500Linux.tar.gz
```
It contains files
```

iP1500/bjfilter-common-2.50-2.i386.rpm
iP1500/bjfilter-pixmaip1500-2.50-2.i386.rpm
iP1500/bjfilter-common-2.50-2.src.rpm
iP1500/bjfilter-pixmaip1500-lprng-2.50-2.i386.rpm
```
So I converted every i386 rpm with alien to debian
```

cd iP1500
sudo alien *i386.rpm
```
Then to install the deb files:
```
sudo dpkg -i *.deb
```
Everything went ok. I've already had all needed deps. If you are not that lucky and something says 'failed dependencies' try fixing it with apt-get install or apt-get -f install.


Now, you should convert the .rpm to .deb, that is, alien is the tool.. but the amd64 alien won't do this, returning that no 64_bit program is in the package. You need an i386 alien, you can either use a chrooted environment, or an i386 live cd to install alien and do the conversion.

Then you should install the i386 debs onto your amd_64 machine, this would require a "--force-architecture" option in the dpkg command line.. if I remember correctly bjfilter requires a very old version of libpng and won't be able to find the current one; just use a "--force-all" option and  continue happily! :)

Once installed, it still won't work: it needs libraries. If you run bjfilterpixmaip1500 from command line it will prompt what library is missing, I manually added simlinks or unpacked missing files into /usr/lib/32 (very important, this is the lib directory for 32-bit programs).

Actually you don't have to do the hard work, as I've found an utility, getlibs, wich automatically fixes missing 32bit library.

loook here

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

```
getlibs /usr/local/bin/bjfilterpixmaip1500
```

should do the trick.

Once you can run bjfilter from command line without any complaining, loading the filter into printer configuration should allow you to print.
The filter is installed in

/usr/share/cups/model/canonpixmaip1500.ppd

refer to this thread for additional tweaking (.ppd editing to allow higher resolution, but I suggest printing normally before).

[http://ubuntuforums.org/showthread.php?t=248745&highlight=ip1500](http://ubuntuforums.org/showthread.php?t=248745&highlight=ip1500)
I hope it works!

---

### Post by rocky_raccoon on 2008-04-22
It sort works, everything was fine until I got to the getlibs /usr/local/bin/bjfilterpixmaip1500 part.

Though I installed the getlibs package I got this output:

```
:~$ sudo getlibs /usr/local/bin/bjfilterpixmaip1500
No match for libcnbpcmcm214.so
No match for libcnbpess214.so
No match for libcnbpcnclapi214.so
No match for libcnbpcnclbjcmd214.so
No match for libcnbpcnclui214.so
No packages to install
```

What I did to solve this probles was to copy the missing library libcnbpcmcm214.so (which is the one that the command bjfilterpixmaip1500 claims to be missing) to /usr/lib32 by using the following commands:

```
$ sudo cp /usr/lib/libcnbpcmcm214.so /usr/lib32/libcnbpcmcm214.so
$ sudo cp /usr/lib/libcnbpcmcm214.so.6.11.1 /usr/lib32/libcnbpcmcm214.so.6.11.1
```

The second file may not be necessary (since bjfilterpixmaip1500 only claims  the first one missing) but I copied both anyway.

By now the printer should work but I recommend to tweak canonpixmaip1500.ppd by following step 7 here: [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500).

---

### Post by rocky_raccoon on 2008-04-22
Ok, Ill try to put this all together. Im a newbie, so if someone actually knows what is going on here and can write a better guide, please do it.

[SIZE="4"]**Installing cannon iP1500 on 64-bit Ubuntu**[/SIZE]

Start by getting an i386 ubuntu or debian, you can do this by runing ubuntu  i386 (32 bit) live CD. Then follow steps 1 to 4 from here: [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)

> 1. download the driver from Canon:

```
wget http://software.canon-europe.com/files/soft22415/software/iP1500Linux.tar.gz
```

2. Extract it:

```
tar -xzf iP1500Linux.tar.gz
```

3. Install alien and libxml1:

```
sudo apt-get install alien libxml1
```

4. Convert rpm to deb using alien:

```
cd iP1500 
sudo alien *i386.rpm
```

Now copy this files to a location you can access with your 64-bit ubuntu (any removable drive should do).

Return to your Ubuntu 64, preferibly turn your printer off (make sure it is on before you try to turn it off), **cd to the directory where you've copied the deb packages** and use command: ```
sudo dpkg -i --force-all *.deb
``` to install the packages in your 64-bit architecture.

Now run ```
bjfilterpixmaip1500
``` and note the missing libraries. Look for them in your computer (they'll probably be in /usr/lib/) and copy them to /usr/lib32/. (In case you can't find the files you may try step 6 described in the previously refered URL but in directory /usr/lib32/ instead. Then run bjfilterpixmaip1500 again to see if there are any missing libraries. Should there be, look for them and copy them to /usr/lib32.)

You may use ```
sudo cp <full file path here> /usr/lib32/<library name here>
``` or any other way you can think of to copy this files.

Alternatively you may try using the getlibs command described a couple of posts above this one (it did not worked for me though).

Now go back the URL where you followed the first 4 steps ([https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)) and follow step 7 to tweak the printer settings file.

> 
7. If you want to add quality and dpi options, edit the ppd file:

```
cd /usr/share/cups/model 
sudo cp canonpixmaip1500.ppd canonpixmaip1500.ppd.backup
gksudo gedit canonpixmaip1500.ppd
```

add the following lines:

```
*OpenUI *CNQuality/Quality: PickOne 
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality 
```

and replace

```
*OpenUI *Resolution/Output Resolution: PickOne 
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
```

by the following:

```
*OpenUI *Resolution/Output Resolution: PickOne 
*DefaultResolution: 600
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*CloseUI: *Resolution
```

Turn your printer on, it should work by now. You may want to restart CUPS as described in step 8 of cited URL.

I hope this works.

---

### Post by Puru on 2008-04-26
Yes, that's the way! Just to point out, the libs you copy from /usr/lib to /usr/lib32 are just the ones installed by the driver packages. They're actually 32bit libraries, but the installer doesn't know and installs them in /usr/lib, where only 64bit libs should go. That's just to say that usually, when missing a 32bit library you MUSTN'T copy it from /usr/lib but unpack the file from a 32bit archive. Also, getlibs fails the founding as they are proprietary library, not in repos.. should have thought..

Anyway, I love happy endings! :)

---

