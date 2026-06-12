---
title: "ID'ing a sound card with WINE"
date: 2007-12-06
forum: Wine
---

### Post by Conez0 on 2007-12-06
Hello there,
I installed Gutsy Gibbon (7.10) yesterday on my dell inspirion 1501 laptop.  Overall it went pretty smoothly, I had some issues, but fixed most of them.  There are two issues that remain, one of which i hope to solve here.

WINE will not detect my sound card for use, whenever i install a windows app, it warns me that there will be no sound.

The other issue, in case anyone has insight, is that firefox will not make sound.  What im referring to is flash based things, such as Youtube.  Im really not sure where else it should make sound, but I dont get sound when i watch youtube videos.

---

### Post by cogadh on 2007-12-06
The no sound in Flash issue is due to a problem with PulseAudio. You can fix it by using the PulseAudio sound server setup how-to here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server)
That may also correct your Wine sound issue.

---

### Post by Conez0 on 2007-12-06
no, unfortuatley that did not work

i still get no sound with either WINE or youtube

---

### Post by cogadh on 2007-12-07
Did you reboot after following the how-to? I don't think the changes take effect until you do that. I can't remember for sure, I actually switched to Kubuntu because of the issues I had with PulseAudio, though I am sure that how-to corrected the YouTube audio issue for me when I was still on Ubuntu.

---

