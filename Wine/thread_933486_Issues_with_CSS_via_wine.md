---
title: "Issues with CS:S via wine"
date: 2008-09-29
forum: Wine
---

### Post by Afirmative_Action on 2008-09-29
Preface: I just switched to Ubuntu 8.04/wine 1.1.5 two days ago and CS:S is the only app that i have played with. It is possible that my issue is a simple one...

I have successfully installed Steam and I am able to run CS:S but the fps is EXTREMELY low (avg around 15). I did some research and found several possible fixes but my issues is that the commands don't seem to do any thing at all. For example, i tried to launch by typing the command: cd /home/rick/.wine/drive_c/Games/steam WINEDEBUG="fixme-all" wine Steam... all that happens is it takes me to the steam directory but nothing else.

I also tried to lower the DX level to 8.1 or 7.0 but I can't seem to get this to work in the terminal either. 

Any help would be greatly appreciated. 

nVidia 6800GT/Athlon XP 3200/1.0GB DDR/

---

### Post by Dark9204 on 2008-10-01
Hi.
I have an Nvidia EN8500GT silent magic. That i have overclocked to optimal settings, and installed a fan on it of curse.

I get around 80-100FPS in CS:S at simpsons_h (10 guys) in dxlevel 81  at 1024X768 default settings.
I got 50 FPS in the video stress test.

The first thing you should do is to updating your graphics drivers with EnvyNG. Do this by pasting sudo apt-get install envyng-gtk in your terminal.
Remember to uninstall your old driver first.
Note: the proprietary drivers that Ubuntu offers are outdated, the Envy drivers gave me a lot more performance.

To set launch tags in steam,[http://www.youtube.com/watch?v=r8hNRINpvc4](http://www.youtube.com/watch?v=r8hNRINpvc4)
type -dxlevel 81 in that box.

Or create a shortcut with this command: env WINEPREFIX="/home/your ubuntu user here/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -dxlevel 81

Remember for further use: Program.exe -attribute
oh, and BTW dont forget to disable your visual desktop effects.

---

### Post by Brynster on 2008-10-01
yup thats pretty comprehensive.

What you might have missed in his post though is the resolution. I have no reasonable explanation for this but it seems to run best @ 1024x768 for many people. 

my launch arguments are -dxlevel 81 -w 1024 -h 768

i get around 150-180 fps on an athlon x2 64 6000 a BFG 8800 gts oc and 2gb 800mhz DDR2

---

