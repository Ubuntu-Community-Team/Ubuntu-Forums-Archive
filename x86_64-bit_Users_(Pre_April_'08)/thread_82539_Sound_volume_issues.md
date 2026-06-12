---
title: "Sound volume issues"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Netherfox on 2005-10-26
My sound volume is entirely too low for programs like Amarok and Gxine. Has anyone else had problems like this?

---

### Post by erez1012 on 2005-10-27
click double on the spaeker (volume controll)
go to preference
select power amplifier

---

### Post by Entity on 2005-10-27
On my Powerbook, I had to uncheck the DRC option in the Switches tab (You'll need to previously enable the DRC track in the Volume Control Preferences in order to be able to access the option) in order to play sound "loudly" through the powerbook's speakers.

---

### Post by Netherfox on 2005-10-27
erez1012: 

I did not find that option in my sound preferences.

Entity:

Are you sure that that option came checked by default because on mine it did not and i thought that powerbooks would be the same. Either way, checked or unchecked it's still not working for me 

Thanks for the input though

---

### Post by Entity on 2005-10-28
Well I think it depends on whether you had PC speakers plugged in or not.

---

### Post by tmeier on 2005-11-08
On my tibook, I had to go into the Volume control panel, then under file had to change devices to ALSA mixer.  I then had the options that were mentioned previously in this thread, and now my sound works fine.

---

### Post by calum on 2005-11-08
[QUOTE=Netherfox]My sound volume is entirely too low for programs like Amarok and Gxine. Has anyone else had problems like this?[/QUOTE]

Low volume was certainly an issue on earlier PPC versions of Ubuntu... IIRC it's usually solved by running alsamixer and raising the levels of either the PCM1 or DRC channels.

---

### Post by MonolithTMA on 2005-12-16
I can get the sound loud, but it distorts at higher volumes. I haven't tried alsamixer yet. I'll try it tonight.

---

### Post by hobbestec on 2005-12-20
Thanks Entity, that worked for me.  Went to the gnome-volume-control preferences and turned on the DRC checkbox.  Then I had to exit and open the gnome-volume-control again and go to the switches and it showed the DRC switch, and I turned it off.  The sound output is really loud, so I moved the volume meter to about half way down, then it comes out at normal levels.

---

