---
title: "[SOLVED] OK how to play media files in 64bit 8.10 straight up skinny"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by radtek on 2008-11-09
I managed to get them playing in the 'beta' version of 64bit though video & visualizations seemed to jerk along.

I installed the regular release of 8.10 64bit

I did the Mediaubuntu thing and I can play streaming mp3's in rythymbox- I was prompted to install the codecs in totem when I tried to use it. I installed extra codecs through add/remove programs.

Totem acts like it wants to play media files but just closes... Same with VLC.

What gives...?

How do I reconcile this?

---

### Post by Sef on 2008-11-09
> I did the Mediaubuntu thing and I can play streaming mp3's in rythymbox- I was prompted to install the codecs in totem when I tried to use it. I installed extra codecs through add/remove programs.


I would uninstall the codecs the prompt ones, you can do from Add/Remove.  I'd have to research on the best way to remove the medibuntu ones.    Once uninstalled, then just install the ones from Add/Remove.

I will update if I find how to uninstall Medibuntu's safely.

---

### Post by radtek on 2008-11-10
Sorry I'd have replied yesterday but there seemed to be a problem with the forum loading.

I may just solve the medibuntu problem by reinstalling. Doesn't take much time to do.

The funny thing is I did "just install" from Add/Remove originally. Didn't seem to work. I'll try again. Is there a particular order to this? Should I do the initial update to the system first or wait till after I install the codecs?

Thanks

---

### Post by cariboo on 2008-11-10
I just install the ubuntu-restricted-extras meta package from the repositories and libdvdcss2 from the medibuntu repositories. This allows me to play almost any type of audio/video file.

Jim

---

### Post by radtek on 2008-11-10
Which meta-package?

Is it one of these? 

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Or something along the lines of this?

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

[Edit]

Duh... I knew this already about the repos... Still any further advice is welcome.

I've switched servers from the US to the Main. For some reason I always seem to get better results from the main server and I don't trust the one in my own country.

---

### Post by C. Wizard on 2008-11-10
VLC, Videolan, since version 0.9.2 is self-contained and requires no external codecs. It has played everything I've thrown at it so far.
Unfortunately, since updating some files this last Friday from the repositories, VLC has stopped working for me.
However, gxine is a good substitute.

---

### Post by radtek on 2008-11-11
Nothing was working. Movieplayer would crash as soon as it tried to play a file.

But I figured it out. I had to enable the restricted ATI graphics (FGLRX) drivers. Then I can play video. It still jerks every 2-3 seconds but it works.

I really didn't care to have the ATI driver running- but I'll sacrifice for now.

Installed the restricted extras, libdvcss2 from the medibuntu repos then did a system update.

Thanks

---

