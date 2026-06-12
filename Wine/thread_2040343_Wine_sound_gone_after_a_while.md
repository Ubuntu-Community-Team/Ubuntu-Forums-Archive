---
title: "Wine sound gone after a while"
date: 2012-08-10
forum: Wine
---

### Post by slenderontheline on 2012-08-10
Hey, 
 
My wine sound stops working correctly after a while, and killing pulse-audio makes it work, but I need to do it all the time. Is there any workaround to fix this? 
 
Thanks, 
Slenderontheline

---

### Post by Vakman on 2012-08-10
>  Make sure mmdevapi.dll is enabled in winecfg. Disabling it was previously recommended as a workaround for sound problems in many games, but it is no longer needed and in current Wine will prevent sound from working. 
Note to PulseAudio users: The unofficial "winepulse" driver that some distros include in their packages is not a part of plain Wine and is not supported here.

Source: [http://forum.winehq.org/viewtopic.php?t=12941](http://forum.winehq.org/viewtopic.php?t=12941)

Also, what version of Wine are you using?
To check:
```
wine --version
```

---

### Post by slenderontheline on 2012-08-17
Thanks for the response, and sorry for the late reply. 
 
I'm with wine 1.4, and there's no option for enabling mmdevapi.dll.

---

### Post by Vakman on 2012-08-20
> **slenderontheline said:**
> Thanks for the response, and sorry for the late reply. 
 
I'm with wine 1.4, and there's no option for enabling mmdevapi.dll.

Yeah, that is pretty old help I believe. I was just trying to suggest anything and get some more info, at least wine version to help others help you.

---

