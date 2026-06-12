---
title: "wma version 9 support"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by hypersoar on 2008-06-22
WMA version 9 won't play on my computer. I've looked around, but I can't find out how to install the codec. I have 64 bit Hardy Heron.

---

### Post by Nepherte on 2008-06-22
Enable the medibuntu repositories, see this link for more information on how to do that: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After enabling the repo, install the w64codecs package:
```
sudo apt-get install w64codecs
```

---

### Post by nikgare on 2008-06-22
Are you sure that the file isn't DRM'd?

---

### Post by pixel :-) on 2008-06-22
Thies codecs wont help,it has already been revert engineered.

In general wmv,work?They are almost always of version 9.

it's drm?
it's WMA Pro?


Try it in windows under virtualbox.

---

### Post by soundengine355 on 2008-06-29
I've tired the w64codec and it has not worked, I've gone back to the 32bit version.

---

### Post by go_beep_yourself on 2008-09-15
> **soundengine355 said:**
> I've tired the w64codec and it has not worked, I've gone back to the 32bit version.

w64codecs doesnt play the wma9 file for me either. How did you make the w32codecs work? If w32codecs worked, then why did you remove it the first time?

---

### Post by cotcot on 2008-10-05
w32codecs doesn't work either.

---

### Post by Kilz on 2008-10-05
> **cotcot said:**
> w32codecs doesn't work either.

Thats because regardless of it being w64 (a 64bit package) or w32 ( a 32bit one) neither will play [DRM]("http://en.wikipedia.org/wiki/Digital_rights_management")'d files in linux. Its one more bad codec from Microsoft that is designed not to play on Linux. 
Changing the version of Ubuntu will be a lot of work with no gain.

---

### Post by spybart on 2008-10-24
I had the same problem and after installing the w32codecs I discovered that I could play the file on MPLayer.

---

### Post by DPic on 2009-02-11
I am in jaunty and trying to get this to work. Videos downloaded through miro apparently use WMA 9 for audio so the videos play with no sound. I have the gstreamer codecs installed but they apparently don't support it (yet?). The most surprising to me is that even vlc doesn't play it. If VLC can't, who can!?

---

