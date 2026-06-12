---
title: "Can't watch encrypted DVDs"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Soda Ant on 2006-07-16
Totem doesn't want to play encrypted DVDs (which means just about any commercial DVD). It fails with the message "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I installed css using the script

/usr/share/doc/libdvdread3/examples/install-css.sh

The css libraries seem to be installed:

# find / -name libdvdcss\* -print
/usr/lib/libdvdcss.so.2
/usr/lib/libdvdcss.so.2.0.4


What's wrong? How do I fix it?

Thanks.

---

### Post by Jagot on 2006-07-16
Have you read the section here for AMD64 processors?

[https://help.ubuntu.com/community/RestrictedFormats#dvd](https://help.ubuntu.com/community/RestrictedFormats#dvd)

> The install-css.sh script will compile the libdvdcss2 library for you instead of downloading a prebuilt binary. Make sure you install the debhelper, build-essential and fakeroot packages first.

---

### Post by Soda Ant on 2006-07-17
> **Jagot said:**
> Have you read the section here for AMD64 processors?

[https://help.ubuntu.com/community/RestrictedFormats#dvd](https://help.ubuntu.com/community/RestrictedFormats#dvd)

Yes, I read that. debhelper, build-essential and fakeroot are needed to build the css library, so, yes, I have them all installed.

The css library builds successfully, and appears to be in the right place, but totem still can't play css encrypted DVDs.

---

### Post by Hallavej on 2006-07-17
I think the problem is Totem, not libdvdcss. I have had the same problem with Totem, but the dvds play fine vlc and mplayer. Did you try a different player?

---

### Post by ahaslam on 2006-07-17
I had this with Totem Gstreamer. Removing this and installing Totem Xine solved my problem.

Tony.

---

### Post by mysticrider92 on 2006-07-17
I found watching movies to be very challenging also. Try installing the libdvdread3 package through Syntapac (or you can use terminal if you want, I find Syntapac easier). I also found a book called Ubuntu Hacks that gives a lot of useful information on different things including media.;)

---

### Post by hajk on 2006-07-18
Mmm... I've never had any problem when following the instructions in the RestrictedFormats page of the wiki to the letter. So, why don't you just start at the top, and work your way down to the bottom, without skipping a single step (unless it says to do so for amd64).

---

