---
title: "compiz fusion on suse?"
date: 2007-10-07
forum: openSUSE and SUSE Linux Enterprise
---

### Post by mpgarate on 2007-10-07
I am trying to get compiz fusion running on suse. I was following the official opensuse wiki for installing compiz fusion, and now my screen is always black on boot (when I choose suse, im in ubuntu now)

I can see the mouse, but the rest is black. can anyone help?

---

### Post by kiran_aryan on 2007-10-07
Try pressing Ctrl Alt F1 from normal mode or try booting into fail safe mode and once you get the terminal, login and backup ur xorg.conf and edit it to change the driver to vesa. Save and exit and reboot. 

```

su
root's password:
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
vi /etc/xorg.conf

(Under "Device" Section, change value corresponding to "Driver" to "vesa" (instead of nv or nvidia or ati or intel). You need to press INSERT key to write values and then press ESC key to stop writing.Type :x to save and exit)

shutdown -r now

```

Once you get into normal mode -

1. If you have ATI or Nvidia card, install the respective drivers first. 

2. If you are using openSUSE 10.3, you can install Compiz Fusion with 1-click install available from the website: [http://en.opensuse.org/Compiz_Fusion](http://en.opensuse.org/Compiz_Fusion)

3. Then Enable Desktop Effects or open Compiz Fusion Settings from the Application Browser.

---

### Post by mpgarate on 2007-10-07
okay sorry I might need my hand held for this one...

I have an integrated nvidia card. for compiz fusion in ubuntu, I just install the nvidia-glx package. If I changed the line in my xorg to read 'vesa' using a terminal while in gnome, and then restarting after saving the file, would it work the same? and what yast package do I install for the vesa driver?

---

### Post by mpgarate on 2007-10-07
I gave it a shot, and now im getting

> mike@mike-desktop:~> compiz --replace
Xlib:  extension "GLX" missing on display ":0.0".
compiz: Trying '/usr/$LIB/libIndirectGL.so.1'
compiz (core) - Fatal: No composite extension
mike@mike-desktop:~> 


---

### Post by theonlyrealperson on 2007-10-10
I have the Nvidia integrated graphics too. You can install the proprietary blob here with the "one-click install":

[HTML]http://en.opensuse.org/Nvidia[/HTML]

But, you have to get by that black screen first, eh? When your screen goes black, hit ctrl+alt+backspace, then ctrl+alt+F1 to go to the command line. Login as root, and change your driver to vesa in xorg. 

i.e.:
```
nano /etc/X11/xorg.conf
```

Find where Suse has put in the "nv" or the framebuffer driver, and change it to "vesa".  Save it, and log in as your user. Type in startx and do the one-click install from the link above.

After you do the "one-click install", you'll have to change the driver from "vesa" to "nvidia". (For some reason it doesn't do it automatically on mine.) Do it after the install, but before you reboot.

Good luck!

---

### Post by mpgarate on 2007-10-10
I did as you say, and compiz will 'run' (does not crash) but shows no effects or window borders

---

### Post by kiran_aryan on 2007-10-11
did u try rebooting after u enable desktop effects? try changing the settings from compiz fusion settings from control center.

---

### Post by mpgarate on 2007-10-11
whoops! Now its workin! yay thanks

---

