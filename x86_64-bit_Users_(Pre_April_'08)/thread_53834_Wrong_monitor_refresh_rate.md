---
title: "Wrong monitor refresh rate"
date: 2005-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gorge0 on 2005-08-02
Hi all,

I have a problem with starting xserver. Xorg is trying to set up monitor frequency much higher then my monitor can handle,over 150Hz. 

So I looked into xorg.conf and there was both hor. and vert. frequency limited to lower  values (60/75 -or something like that) than xorg is really setting up. Neither reconfiguring Xorg nor changing driver help me. 


Could someone help me please?
oh almost forgot : A64 3000+, GF6600, 17" AOC 7A+ (max 1600*1200 at 85 Hz)

---

### Post by Tamir on 2005-08-02
That's weird, maybe you could try reconfig your xserver.
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Gorge0 on 2005-08-02
I tried dpkg-reconfigure xserver-xorg several times ,but no luck.

Although I've just discovered that if I press CTRL+ALT+BACKSPACE after xserver started everything is working just fine...
Is there way to fix this so that I don't have to do it every time?

---

### Post by DancingSun on 2005-08-02
Can't you just select a lower refresh rate from the GUI screen resolution changer?  I know that if I **de-select** the "Make default for this computer only" checkbox, the resolution and refresh rate that I chose will be retained after reboot.  Whereas, if I checked that checkbox, it will revert to the "Modeline" entry in xorg.conf.

---

### Post by Gorge0 on 2005-08-02
Doesn't matter which refresh rate I choose, xorg always sets up HorizSync 196,6kHz and VertRefresh 126.7Hz...
It seems now that it's working fine if I choose "recovery mode" in GRUB (except some HAL error which I get after Gnome have started).

---

### Post by DancingSun on 2005-08-02
Try commenting out the refresh rate lines in xorg.conf.
I commented out mine, and it's detecting the monitor's factory refresh rate and resolution modes.

What's your modeline?

---

### Post by Gorge0 on 2005-08-02
Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -HSync +Vsync

Can you be a little bit more specific about the lines I should comment out ,I'm not sure what you mean...I have in xorg.conf just two lines which are related to refresh rate and these aren't commented

Maybe an example of these lines will help me

---

### Post by DancingSun on 2005-08-02
[QUOTE=Gorge0]Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -HSync +Vsync

Can you be a little bit more specific about the lines I should comment out ,I'm not sure what you mean...I have in xorg.conf just two lines which are related to refresh rate and these aren't commented

Maybe an example of these lines will help me[/QUOTE]

This is how mine look like:
```
Section "Monitor"
	Identifier	"Samsung SyncMaster 950p"
	Option		"DPMS"
#	HorizSync	30-90
#	VertRefresh	50-120
	Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
EndSection
```

You might want to change your modeline and see if it'll help.

---

### Post by Gorge0 on 2005-08-03
Changing modeline didn't solve anything...I compared the Xorg.O.log files from normal mode and recovery mode /where it's OK/ and I didn't find ANY differences, all same....

---

