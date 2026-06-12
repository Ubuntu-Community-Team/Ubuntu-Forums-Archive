---
title: "Codec vid_iv50.xa"
date: 2008-09-09
forum: x86 64-bit Users
---

### Post by Hellaxe on 2008-09-09
Hello people:
this codec is missing from everywere.
I have the w64codecs but I thing this one is missing.
This is for playing the indeo 5 from intel (i think).
I've searched here and googled but..... no answers.
Can anyone tell me how to get it?
Thanks.

---

### Post by Thanoulis on 2008-09-09
Strange...i didn't encounter any video i couldn't play (64bit system), but a got neither w64codecs or vid_iv50.xa or any other *.xa file in my hard disk...are you sure this is the problem?

---

### Post by Hellaxe on 2008-09-10
Yes, I'm sure.

---

### Post by yacwroy on 2009-07-21
Is there still no way to play Indeo 5 movies on 64 bit?

I'm finding these videos everywhere, and it's damn annoying not to be able to play 10% of all movies.

I have compiled from scratch, see:
[http://ubuntuforums.org/showthread.php?t=739011](http://ubuntuforums.org/showthread.php?t=739011) (Compiling 32 bit mplayer on a 64 bit system?)
But MPlayer etc still can't find the Indeo 5 codec.

Has anyone got Indeo 5 working at all?

---

### Post by andrew.46 on 2009-07-22
Hi yacwroy,

> **yacwroy said:**
> Is there still no way to play Indeo 5 movies on 64 bit?

On an up-to-date 32 bit svn MPlayer I can only see the 32bit codecs:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -vc help | grep -i Indeo[/COLOR]**
ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]
[B][COLOR="Purple"]indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll][/COLOR][/B]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]

```

So I suspect on a 64bit system you may be in a bit of trouble.

Andrew

---

### Post by kostkon on 2009-07-22
Yes, *w64codecs* has very few codecs, especially when compared with the  *w32codecs* package that contains I think more than 100 codecs.

Nevertheless, if you are using a Gstreamer-based player then try installing the *gstreamer0.10-ffmpeg* package and see if that will make any difference.

---

### Post by Arup on 2009-07-22
There is not a single file that I have thrown at mplayer that has had it stumped, infact, I find mplayer's performance better than Windows Media Player even with Klite codec pack loaded. The rare instance mplayer has faltered specially with corrupted file, VLC has rescued it well and played it flawlessly. Suggest you check out VLC for your needs then.

---

### Post by yacwroy on 2009-07-23
Arup, are you using a 64-bit Ubuntu? because 32-bit can play them fine.
Have you tried any Indeo 5 videos?

[http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi](http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi)
If you can get this video to play in 64-bit Ubuntu, please tell me how you did it.

VLC cannot play Indeo 5 videos either.



w32codecs contains the Indeo 5 codec. w64codecs does not.
I'm having trouble forcing w32codecs to install on a 64 bit system.
I've found a few posts on this but they're all asking how to do it and nobody is giving answers.

---

### Post by glennric on 2009-11-14
Has anyone that has the amd64 architecture been able to get these videos to play?  I have compiled the svn mplayer, but it still can't do it.  It works fine on another computer with i386 architecture.  I am just curious if there is a patch against the current svn checkout of mplayer that will add this capability for amd64.

---

### Post by hshan on 2009-11-17
> **yacwroy said:**
> Arup, are you using a 64-bit Ubuntu? because 32-bit can play them fine.
Have you tried any Indeo 5 videos?

[http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi](http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi)
If you can get this video to play in 64-bit Ubuntu, please tell me how you did it.



9.10 amd 64... videos won't play for me either.

---

