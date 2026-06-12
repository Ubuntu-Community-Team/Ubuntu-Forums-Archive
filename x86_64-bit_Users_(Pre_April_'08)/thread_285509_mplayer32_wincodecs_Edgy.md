---
title: "mplayer32 wincodecs Edgy"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by prosario_2000 on 2006-10-26
Ok... I have a problem:

I'm trying to install mplayer32 on my AMD64 after I upgraded it from Dapper to Edgy. I try to install the package:  mplayer32_1.0pre7-1_amd64.deb.  But it gives me the following error:

(Reading database ... 258607 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb

Does anyone know a solution to this problem?  I will be very grateful.

---

### Post by fabertawe on 2006-10-27
I'm not sure about your lib error but so far VLC has played everything I've thrown at it, including WMV. My MPlayer32 browser plugin appears broken now anyway, I've yet to look into this.

Paul

---

### Post by fabertawe on 2006-10-27
[This]("http://www.ubuntuforums.org/showthread.php?t=202537&page=40") may help actually (post #392). Presumably you didn't have it installed under Dapper?

Disregard what I said in my last post about MPlayer32 as it **is** still working on Edgy. Having checked 'Preferences->System->Sound' I found 'Default Sound Card' was set to my onboard audio (which I have disabled) instead of my Audigy2 EX :rolleyes:  Weird thing is though that it was only audio in the browser (Swiftfox) that was affected and everything on the desktop was fine :-k 

Paul

---

### Post by kuja on 2006-10-27
Hmm, so they fixed the MPlayer32 in edgy? Interesting. Oh well, I find it best to stick with the 64-bit MPlayer now that it has WMV support. (as of the release candidate)

---

### Post by Hallavej on 2006-10-28
To answer the question: Just remove ia32-libs-openoffice.org (sudo apt-get remove ia32-libs-openoffice.org). You dont need it anymore, because ooo is a native 64 bit application in edgy.

---

### Post by fabertawe on 2006-10-28
> **kuja said:**
> Hmm, so they fixed the MPlayer32 in edgy? Interesting. Oh well, I find it best to stick with the 64-bit MPlayer now that it has WMV support. (as of the release candidate)

So are you using the 64bit MPlayer browser plugin in a 64bit browser?

Paul

---

### Post by Raphraphou on 2006-10-28
Do you know if Mandriva 2007 does the multi-arch ? I'm tired of having problems with my Edgy (and others) 64bits...

---

### Post by kuja on 2006-10-28
> **fabertawe said:**
> So are you using the 64bit MPlayer browser plugin in a 64bit browser?

Paul
Using a different plugin - kmplayer-konq-plugin.

---

### Post by kuja on 2006-10-28
> **Hallavej said:**
> To answer the question: Just remove ia32-libs-openoffice.org (sudo apt-get remove ia32-libs-openoffice.org). You dont need it anymore, because ooo is a native 64 bit application in edgy.
I wouldn't be so jumpy to remove it really. There are some things in that package that, IMO, shouldn't be as they're really more general things that may be needed by other 32-bit programs.

---

### Post by Kilz on 2006-10-28
> **Raphraphou said:**
> Do you know if Mandriva 2007 does the multi-arch ? I'm tired of having problems with my Edgy (and others) 64bits...

I dont know about Mandriva, but SuSE has fantastic multiarch support. The problem is the 10.1 version has other problems. But 10.2 will be released in Dec :KS

---

