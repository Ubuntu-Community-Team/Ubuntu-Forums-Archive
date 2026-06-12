---
title: "How do I change my screen resolution to 1200 x 800?"
date: 2007-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by krazy1912 on 2007-09-13
I checked screen resolution, but it wasn't listed.

---

### Post by John.Michael.Kane on 2007-09-13
> **krazy1912 said:**
> I checked screen resolution, but it wasn't listed.

Resolution methods.adjust for which gpu your using.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Note: Make sure to have your lcd/crt manual, As you will need to refer to it for certain settings.

Another note For 50hz refresh rate issues with "nvidia based gpu's". You can disable Dynamic Twin View in /etc/X11/xorg.conf. Add the below option to xorg's card device section to turn it off.
```
Option "DynamicTwinView" "False"
```

---

### Post by christuckeruf on 2007-09-13
in root (or using sudo I guess...personally I like being root)
#cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

#gedit /etc/X11/xorg.conf

When the file opens in gedit go to the section called: Section "Screen".  There it should list lines such as:

SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"

Add your resolution after the string modes and surround your entry with quotes.

Save the file and restart x

---

