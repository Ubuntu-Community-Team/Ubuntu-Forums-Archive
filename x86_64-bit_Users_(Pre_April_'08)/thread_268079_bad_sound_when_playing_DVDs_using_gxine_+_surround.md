---
title: "bad sound when playing DVDs using gxine + surround sound"
date: 2006-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tszanon on 2006-09-29
Hi people,

As the title says, I'm having a problem when I try to play DVDs (commercial movies) using gxine with surround sound (5.1).

If I try using stereo sound, everything is fine: video is ok, sound is ok. But if I choose surround sound, the sound becomes bad, with some white noise in the back and the sound alternates between 'bad sound' and 'no sound at all' a few times per second.

I don't remember well, but I think it started after I upgraded from Ubuntu 5.10 to 6.06. Well, the fact is: I used to play DVDs when I still used Breezy, then I spent some months without playing any DVD, and now that I'm using Dapper, I tried again to play DVDs, but this issue doesn't let me use surround sound.

I must say that the sound is not out of sync, it just becomes so bad that I'm forced to stick to stereo sound.

I tried changing many of the sound settings in gxine, but nothing seems to help. I don't know what happened, nor how I can fix it.

The sound system works fine. It surely is a software-related problem. I believe that something is misconfigured - whatever it may be.

If you have any idea on how to fix the problem, please share! :)

---

### Post by lrrr on 2006-10-05
I've been having the same sorts of problems in gxine. Totem [using the totem-xine package instead of totem-gstreamer] seems to work just fine, though. Maybe it's just the current version of gxine.

---

### Post by tszanon on 2006-10-05
Thanks, I'll try it when I arrive home.

---

### Post by JGuru on 2006-10-05
You can install either **MPlayer** or **VLC** or both to play VCD/DVDs.
 Both are very good Media Players. Just give it a try. Your problem will be
 solved.

---

### Post by tszanon on 2006-10-05
I tried using Totem-xine. It worked! :D 
I just remembered that this problem used to happen even when playing divx movies (AC3). Using totem-xine, there's no problem. :D :D 

Now, I'm gonna search for an option in totem that lets me change the language in the DVD menus to PT-BR.:p 

Thanks to both of you!

---

