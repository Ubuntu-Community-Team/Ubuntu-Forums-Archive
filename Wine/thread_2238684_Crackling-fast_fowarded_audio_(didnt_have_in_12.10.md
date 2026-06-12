---
title: "Crackling-fast fowarded audio (didnt have in 12.10, now in 14.04)"
date: 2014-08-09
forum: Wine
---

### Post by ci1616 on 2014-08-09
In a couple of my games at some points the audio will start crackling, become really distorted, and fast forward. In the games I'm experiencing this in I've NEVER had this problem in ubuntu 12.10. I just upgraded to 14.04 a couple days ago and I now have this issue. This is only happening in select wine games, and I've not had this issue outside of wine. I've done extensive searches for the past couple of days, and I've tried numerous fixes, but none have worked so far. 

So far I've tried:
-installing the most recent realtek audio drivers from the realtek website
-Installing the latest linux kernal (3.16)
-Adding "[COLOR=#333333][FONT=monospace]options snd-hda-intel vid=8086 pid=8ca0 snoop=0" in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/modprobe.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/alsa-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]base.conf
-Changing settings to "[/FONT][/COLOR][COLOR=#000000][FONT=bitstream vera sans]have Pulseaudio on your system and still have wine directly use ALSA, instead of going through the ALSA plugin of Pulseaudio"  ([/FONT][/COLOR]http://wiki.winehq.org/WineAndPulseaudio)
-Changing a line to this "[COLOR=#000000]default-fragment-size-msec = 5" in [/COLOR][COLOR=#000000]/etc/pulse/daemon.conf
-one last thing I can't remember, but it involved modifying [/COLOR][COLOR=#000000]/etc/pulse/default.conf

I am getting really, really frustrated as I've been at this for days and this "upgrade" has made me unable to enjoy the games I want to play when I had 0 issues on 12.10. I would be EXTREMELY grateful to anyone who can help me fix this issue!

Thanks 


[/COLOR]

---

