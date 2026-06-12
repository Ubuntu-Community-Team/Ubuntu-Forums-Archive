---
title: "weird issues with sound, music\video playback after upgrade"
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by xtlosx on 2007-11-19
Greetings everyone, I have been having a weird issue lately with my gutsy amd64 install.  I have had it running since beta with no issues... It is a desktop machine...

So everything has been great, up until about a day ago.... I did the regular updates, and then I went to use audacious to play some music.. The first song plays, the next song.. .locks up and have to kill -9 it... VLC, I go to play a movie, I can't adjust the volume, but I can make it full screen, the when I un full screen, it locks up and I have to kill -9 it.........

Another weird observation I have made, when I go into preferences, sound, and then test sound playback or something, first beep goes off, I hit OK, then I try to test another one, and it locks up like audacious does after playing the first song.. It seems like the second time I try to use sound, it locks up the application using that sound stream....


I have tried to boot into past kernels in grub, to no avail.. has no one else experienced this.. it's just me??? Any ideas?

Thanks for everyones' help in advance!

---

### Post by xtlosx on 2007-11-20
another twist to this little issue.. someone suggested I try to just do sudo audacious and see if it works, and it does just like normal... sudo vlc as well plays video, i can resize, change volume nothing goes wrong..


just when I execute it as my user it freaks out... What the heck is going on?

---

### Post by Perfect Storm on 2007-11-21
Sounds like a hardware failure. Try run the memory test with the liveCD.

---

### Post by ramkumail on 2008-06-09
I dont know if it is still relevant but to me in audacious the issue got corrected after playing around with the type of audio output plugin to be used.

---

