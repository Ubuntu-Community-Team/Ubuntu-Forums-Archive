---
title: "Trouble building ffmpeg with shared libs"
date: 2009-07-12
forum: x86 64-bit Users
---

### Post by Norst on 2009-07-12
I'm getting the following error when building the latest SVN of ffmpeg.

/usr/bin/ld: libavutil/avstring.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
libavutil/avstring.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavutil/libavutil.so.50] Error 1

From what I read and understand, I somehow need to tell it to build the avstring.o with the -fPIC flag. I have no idea how to do this. Also I can not find any reference to someone else having this issue. :(

I can build ffmpeg and it works fine if I don't use --enable-shared in the configure command. But I need the shared libs made so that I can build the latest mediatomb...

I'll admit I'm in a little over my head but that seems to be the best way to learn.

---

### Post by FakeOutdoorsman on 2009-07-12
1. Uninstall FFmpeg

2. Navigate to your FFmpeg svn directory and then run:
```
make distclean
svn up
```
3. Follow these instructions:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

4. When you get to "Install FFmpeg", skip this line:
```
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
```
and then add *--enable-shared* to your FFmpeg configuration line.  After you install FFmpeg, run the following command:
```
sudo ldconfig
```
This will update the links to your new shared libraries.  Did you still get the same error message?

---

### Post by Norst on 2009-07-12
lol, ok I have no idea why that worked!

I had done svn update before but for some reason svn up really worked. Both are the same thing are they not?

regardless, thank you very much, both ffmpeg and mediatomb got made correctly and media tomb now has the thumbnail support I was going for. I wish I could have the past 5hrs of my life back but I fear with the time I'd gain I'd lose the knowledge. Thx again.

---

### Post by FakeOutdoorsman on 2009-07-12
> **Norst said:**
> lol, ok I have no idea why that worked!

I had done svn update before but for some reason svn up really worked. Both are the same thing are they not?
Yes, *svn up* and *svn update* are the same, although I would guess the *make distclean* is what you needed to clean out any old, broken build attempts.
> regardless, thank you very much, both ffmpeg and mediatomb got made correctly and media tomb now has the thumbnail support I was going for. I wish I could have the past 5hrs of my life back but I fear with the time I'd gain I'd lose the knowledge. Thx again.
Glad I could help.

---

