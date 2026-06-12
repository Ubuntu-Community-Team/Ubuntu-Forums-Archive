---
title: "Webcam not detected: mounts as device in the 'Places' menu ?!?"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by mªrty on 2009-03-20
I have an Intel pocket PC cam which has worked once in my 8.10 x86_64.
Gspca recognizes it, here's the DMESG output when I plug it in:
```
[25931.241043] Linux video capture interface: v2.00
[25931.283664] gspca: main v2.2.0 registered
[25931.288451] gspca: probing 8086:0630
[25931.290149] gspca: probe ok
[25931.290172] gspca: probing 8086:0630
[25931.290207] usbcore: registered new interface driver spca500
[25931.290224] spca500: registered
[25931.402888] usbcore: registered new interface driver gspca
[25931.402915] gspca: gspca driver 01.00.20 registered
[25931.874143] gspca: disconnect complete
martin@ubuntu64:~$ 
```
Once plugged in, I get a gui message saying that 'the volume could not be mounted' (i think from F-spot) and a link to the camera appears in my Gnome 'Places' menu & on the desktop. Neither Skype nor any other program can detect that a video device is connected, even after I right-click on the icon on the desktop and hit 'Unmount'.

Is the camera being detected as a hard drive? Any ideas what else I can check to figure this out?

---

### Post by mªrty on 2009-04-25
After **months** of trying to get my Intel Pocket PC cam to function as a webcam, I've finally found a solution!

[B][COLOR=Red]
[LIST=1]
[*]type 'gconf-editor' in console
[*]when gconf-editor opens, navigate to Apps-->Nautilus-->Preferences
[*]Untick "media automount" !
[/LIST]
[/COLOR][/B]

That's it :)

---

