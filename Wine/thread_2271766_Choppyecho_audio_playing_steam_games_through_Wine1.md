---
title: "Choppy/echo audio playing steam games through Wine1.7"
date: 2015-04-01
forum: Wine
---

### Post by unrated2 on 2015-04-01
[COLOR=#000000]Hello all,[/COLOR]

[COLOR=#000000]I have a Asus c300ma-edu chromebook and installed xfce trusty via crouton. Once in, I grabbed software center and Mangler(for ventrilo). Then installed Wine1.7 and installed Steam through Wine. Steam in home streaming works perfect minus the sound. When streaming from my Windows 7x64 Ultimate machine, the sound is very choppy and echos, basically play on mute or not at all its so bad. I figured it might be WINE related so I wiped and re-installed xfce trusty but this time with the steam linux native client. Some games sound works fine but some still have a crackle instead of the choppy/echo. This is fine but most games don't stream well with the steam linux version. So now I am back on xfce 4.10 trusty (hope I'm saying this right) and trying to fix the sound produced in Wine.[/COLOR]

[COLOR=#000000]So some things I have tried, [/COLOR]
[COLOR=#000000]1. Installed gedit and changed [/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]default[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]-[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]fragment[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]-[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]size[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]-[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]msec[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace] = 10 to 5 in the etc/pulse/daemon.conf
2. changed from the default to [/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]alternate-sample-rate = 48000 and took out the ";"
3. Installed gnome-alsamixer as I hear if I can just switch to ALSA over pulse most issues are fixed
4. Removed pulseaudio to try and force ALSA to take over

Reboots in between each change but still nothing has touched the choppy/echo sound when playing a game through WINE. I am having fun with Linux but this issue is driving me up a wall only because I just don't know what to try next. Any one out there able to help a new linux user out?[/FONT][/COLOR][/COLOR]

---

### Post by jamesjogi08 on 2015-04-14
[COLOR=#000000][FONT=monospace]Installed gnome-alsamixer as I hear if I can just switch to ALSA over pulse most issues are fixed....!!!





____________________________________________
[/FONT][/COLOR][TABLE="width: 80"]
[TR]
  [TD="width: 80"]*Signature*[/TD]
[/TR]
[/TABLE]

---

