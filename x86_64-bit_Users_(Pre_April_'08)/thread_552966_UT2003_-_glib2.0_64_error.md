---
title: "UT2003 - glib2.0 64 error"
date: 2007-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeym on 2007-09-17
Hi,

Is it possible to install UT2003 in Feisty 64 bit? I was following [this thread]("http://ubuntuforums.org/showthread.php?t=420743") and I got this error:

```

$ sudo sh linux_installer.sh
Password:
Copying to a temporary location...
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." /tmp/makeself10363 -check
 All good.
Uncompressing Unreal Tournament 2003 for GNU/Linux 2107tail: Warning: "+number" syntax is deprecated, please use "-n +number"
......................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Fatal error, no tech support email configured in this setup
The setup program seems to have failed on x86_64/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)

```

---

### Post by mikeym on 2007-09-17
I tried following a guide for creating a chroot to do it but it didn't seem to work.

---

### Post by mikeym on 2007-09-17
I've set up a 32 bit chroot using [this guide ]("http://ubuntuforums.org/showpost.php?p=3231948&postcount=219") and for some reason it still comes up with the same error!

Is it trying to detect my architecture or something?

---

### Post by Cappy on 2007-09-17
You can try
```
sudo apt-get install linux32
```

and then

```
sudo linux32 sh linux_installer.sh
```

And yes - the error is because it is trying to detect your arch

---

### Post by mikeym on 2007-09-17
That is WEIRD! 

The command you gave didn't work in my normal install but on the off chance I tried it from within **chroot** and it worked there! So the install seems to be proceeding.

---

### Post by azriel0184 on 2008-05-10
Setting this up on Hardy with x86_64

After much trial and error, here's what seemed to work, using info from here and [here]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003").

First, create a i386 chroot using [the instructions posted here.]("http://ubuntuforums.org/showpost.php?p=3231948&postcount=219")

Next, notice the deprecation notices in the previous posts? Well, since then tail has removed support for those deprecated options used in the original installer script. Guess what that means? Yep, you need to copy all three cd's to your hard drive. Pick somewhere that's accessible to your chroot (I used my home directory) and copy all the files on all three cd's to there.

IMPORTANT: At this point, after you copy every cd, make sure to give yourself write permission to the files so that when you copy the next cd any files that are in subdirectories will be able to be written!

Next, we need to extract the linux installer code and run the setup program. The following command will do that just fine. Remember to run them while chrooted.

```

$ tail -n +266 linux_installer.sh | tar -x
$ export SETUP_CDROM=`pwd`
$ echo "\#\!/bin/sh" > postinstall.sh
$ linux32 ./setup.sh

```

Follow along with the install program. When it's done there's one last thing that needs to be done. See how I wiped out the postinstall script? This script is also bugged because of changes in the last 5 years, and it's just a semi-nice, but still broken, interface to input your cd-key. You can use the following command to do the same.

```

$ echo "xxxxx-xxxxx-xxxxx-xxxxx" | tr a-z A-Z > /path/to/ut2003/System/cdkey

```

All done folks, enjoy!

Edit: After actually testing it, I can't get it to actually run, it keeps dieing with some very long backtraces. I'm not sure if it's possible to actually get it running, but this will get it installed properly, if someone gets it working, it might be nice to know how...

---

