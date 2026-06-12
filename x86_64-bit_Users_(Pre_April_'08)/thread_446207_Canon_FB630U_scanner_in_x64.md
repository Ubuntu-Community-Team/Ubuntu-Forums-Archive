---
title: "Canon FB630U scanner in x64?"
date: 2007-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fraoch on 2007-05-16
I know this is an old scanner, but it works just fine on my 32-bit machine.

On my 64-bit machine it's recognized and xsane runs, but nothing happens when I try to preview or scan.  The scanner does nothing and the xsane GUI boxes hang.

I've followed threads on scanner problems but seeing as it works fine on my 32-bit machine it must be something else.  Is there a module I'm missing?  It couldn't be an issue with the 64-bit kernel?

Thanks for any advice.

---

### Post by John Jason Jordan on 2007-05-16
> **Fraoch said:**
> I know this is an old scanner, but it works just fine on my 32-bit machine.
On my 64-bit machine it's recognized and xsane runs, but nothing happens when I try to preview or scan.  The scanner does nothing and the xsane GUI boxes hang.
I've followed threads on scanner problems but seeing as it works fine on my 32-bit machine it must be something else.  Is there a module I'm missing?  It couldn't be an issue with the 64-bit kernel?
Try this experiment: Boot to a Dapper amd64 live CD and see if it will work. If so, the problem is a change in the later kernel used in Feisty. They added something about USB-suspend (I know I have not remembered that very accurately), but it makes the USB port not work with scanners. 

I have a Canon Lide-30 that worked fine with Ubuntu amd64 since I bought it back in the days of Breezy all the way through Edgy. But after upgrading to Feisty, it no longer works.

Luckily I seldom need it, so what I do as a workaround is boot to a Knoppix 5.0 (not 5.1) live CD. The Knoppix live CD makes it easy to get a root prompt so I can mount my regular filesystem, and the scanner works with it as well. I finish my scanning, save the results to files in my filesystem, then reboot back into Feisty.

Hopefully there will soon be a fix. There are a lot of people with USB scanners affected by this issue and the bug report was filed shortly after Feisty went final.

If the experiment does not resolve the issue, then you have a different problem.

---

### Post by Fraoch on 2007-05-17
> **John Jason Jordan said:**
> Try this experiment: Boot to a Dapper amd64 live CD and see if it will work. If so, the problem is a change in the later kernel used in Feisty. They added something about USB-suspend (I know I have not remembered that very accurately), but it makes the USB port not work with scanners. 

I have a Canon Lide-30 that worked fine with Ubuntu amd64 since I bought it back in the days of Breezy all the way through Edgy. But after upgrading to Feisty, it no longer works.

Luckily I seldom need it, so what I do as a workaround is boot to a Knoppix 5.0 (not 5.1) live CD. The Knoppix live CD makes it easy to get a root prompt so I can mount my regular filesystem, and the scanner works with it as well. I finish my scanning, save the results to files in my filesystem, then reboot back into Feisty.

Hopefully there will soon be a fix. There are a lot of people with USB scanners affected by this issue and the bug report was filed shortly after Feisty went final.

If the experiment does not resolve the issue, then you have a different problem.

Yup, this was it.  I didn't have an x64 Dapper but I had a 32-bit Dapper, and my scanner came to life again.

Thanks!

I'll have to do some work and investigation to see if I can mount at least one of my drives from within a root prompt of the Dapper live CD.  I could then scan from the command line with sane-canon630u.

---

### Post by John Jason Jordan on 2007-05-17
> **Fraoch said:**
> Yup, this was it.  I didn't have an x64 Dapper but I had a 32-bit Dapper, and my scanner came to life again.

Thanks!

I'll have to do some work and investigation to see if I can mount at least one of my drives from within a root prompt of the Dapper live CD.  I could then scan from the command line with sane-canon630u.
As I recall, it is not easy to get a root prompt with any Ubuntu live CD. But on Knoppix you just click on the penguin to get a root terminal. In fact, as I recall last time I used it, Knoppix automatically mounted all the hard drives it found. And it has both Xsane and Kooka for scanning. Just be sure to use Knoppix 5.0, not the current 5.1. The 5.1 version has too new a kernel so it has the same scanning problem.

I keep a Knoppix CD in my backpack, on my desk at home, and another one in my locker at the university. 'Cause ya never know.

---

### Post by teravolt on 2007-05-26
A fix / workaround can be found at...
[http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html](http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html)

I used it successfully with a Canon LIDE 30.

:)

---

### Post by Fraoch on 2007-05-26
Thanks - had high hopes for it but it hung at step 4.

Step 4 seems to leave the scanner in a confused state.  Although it's still listed in lsusb, it can't be found by scanimage -L anymore.

So close - on second try my scanner makes a bit of noise but seems to seize up.  It can now be re-detected by scanimage -L but it still won't scan.

Ah well.  I'll wait for a kernel fix.:(

---

### Post by eMuNiX on 2007-05-29
> **teravolt said:**
> A fix / workaround can be found at...
[http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html](http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html)

I used it successfully with a Canon LIDE 30.

:)
Thanks sudo apt-get install scanbuttond was enough to get this working again, excellent :)   Running a Canon Lide20 BTW.

---

### Post by John Jason Jordan on 2007-05-29
> **eMuNiX said:**
> Thanks sudo apt-get install scanbuttond was enough to get this working again, excellent :)   Running a Canon Lide20 BTW.
I was hoping that the kernel ugrade a couple days ago would have fixed this, but no such luck. However, installing scanbuttond helped. I found that scanbuttond does not start automatically, but then, I don't really need it running all the time anyway -- I scan very infrequently. When I do scan I usually use Kooka, and sometimes Xsane, so I just edited the menu items for them and added "scanbuttond" in front of each one.

---

### Post by viktor.ilijasic on 2007-09-14
This is completely offtopic, but as it is mentioned here, I hope no one would mind a quick comment...

> **John Jason Jordan said:**
> As I recall, it is not easy to get a root prompt with any Ubuntu live CD.

This is not exactly true. :)

Go to console and type:

$ sudo su -

(without the "$" character, of course.)

And you have console as root as you can get. ;)

Viktor

---

### Post by Fraoch on 2007-10-19
Incidentally this has been fixed in Gutsy, at least for i386 (which I incorrectly reported was working properly).  I will be holding off upgrading my x64 machine due to a disastrous upgrade failure on my i386 machine.

---

### Post by Fraoch on 2007-10-27
Ugh jeez.

It doesn't work in 7.10 x_64 for me...it manages to jog the scan head but it seems to get stuck.  Works fine in the 32-bit 7.10.

---

### Post by der_vegi on 2007-12-25
I have the same problem here running Gutsy on my Inspiron 530n installed from the Dell Iso. When my scanner refuses to work, for example with 'scanimage -T', I can hear a very very high (barely audible) sound, though. Strange...
As it works on my notebook with Hardy Alpha, I am downloading this kernel right now.

There is also a bug report: [https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/118843](https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/118843)

---

