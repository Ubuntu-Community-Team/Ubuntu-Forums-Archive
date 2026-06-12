---
title: "Encrypted DVD playback"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by z-two on 2007-06-13
Hello,
After reading endless threads to do with dvd playback on this forum I've come up with no solution to my problem.

I have installed what i believe to be all the nessessary packages for encrypted dvd playback and have playback of unencrypted dvds working perfectly.

I have tried installing libdvdcss2 using several methods. Firstly from the script that comes with libdvdread3. It compiled and installed successfully, but didn't work.

I then tried the one in the medibuntu repository. It again didn't work. I get the following output when playing encrypted dvds.

```

libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/matt/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000146
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00000146)!!
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000033f4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x000033f4)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00021821
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002fae0d
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 3
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/matt/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

```

I find it odd that it suggests at the top that the drive doesn't play dvds as it can definately read from unencrypted dvds.

I'll be very greatful for any help you can give.

Thanks in advance.

Matt.

---

### Post by John.Michael.Kane on 2007-06-13
What version of ubuntu are you using?


Have you looked over these two threads?
Feisty codec installs.
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

edgy codec installs
[http://ubuntuforums.org/showpost.php?p=2205606&postcount=3](http://ubuntuforums.org/showpost.php?p=2205606&postcount=3)


Also are you using the totem-gstreamer or totem-xine?

If your using totem-gstreamer please install totem-xine, and try replaying your movie.
```
sudo aptitude install totem-xine
```

---

### Post by z-two on 2007-06-14
Ahh sorry I forgot to mention that first time round.

I'm running fiesty (amd64) and using totem-xine.
I have tried the steps shown in the thread you posted a link to previously. So the version of libdvdcss2 i am currently running came from the medibuntu repository.
I have also tried vlc and mplayer to no avail.

Thanks

Matt

---

