---
title: "Someone please help- Beryl problem"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by datelus on 2006-12-04
Hello.
I hope someone could help me.
So the problem is- i installed beryl on my AMD64 and somethings not right.
I have the supported nvidia card and everything s ok with the drivers, but when i type beryl-xgl it displays

```

datelus@datelus-desktop:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl-xgl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl-xgl: GLX_EXT_texture_from_pixmap is missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :0.0


```

and the windows become unusable, jet still can copy.

so please someone help me. Switched to ubuntu and im happy and all, but this is the problem.

btw-  beryl settings maneger in preferences works, (in system->preferences)
Thanks ;)

---

### Post by hainesr on 2006-12-04
> **datelus said:**
> 

```

datelus@datelus-desktop:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl-xgl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl-xgl: GLX_EXT_texture_from_pixmap is missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :0.0


```


I think the NVIDIA drivers are the problem here. Which version are you using? You need to be using the latest beta to get the GLX_EXT_texture_from_pixmap extension that beryl needs.

These threads might be able to help:
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=howto+xgl+beryl]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=howto+xgl+beryl")
[http://www.ubuntuforums.org/showthread.php?t=268036&highlight=howto+xgl+beryl]("http://www.ubuntuforums.org/showthread.php?t=268036&highlight=howto+xgl+beryl")

As a quick test try:
```
$ glxinfo | grep -i pixmap
```
If the output is blank you don't have the right extension.

Hope this helps,
Rob

---

### Post by datelus on 2006-12-04
thanks for reply.
So i did everything like in that howto, and i have latest drivers ( new spash screen nvidias wii ) so i start bery-manager and compiz runs real slow, beryl dosent run at all ( black screen ) ( i selected them by the icon )
so now what should i do? :-k
btw- i dident add the BusID		"PCI:1:0:0" to the xorg.conf  no problem there?

---

### Post by hainesr on 2006-12-04
> **datelus said:**
> thanks for reply.
So i did everything like in that howto, and i have latest drivers ( new spash screen nvidias wii ) so i start bery-manager and compiz runs real slow, beryl dosent run at all ( black screen ) ( i selected them by the icon )
so now what should i do? :-k

Hmm. You've got further than me, I'm afraid. I was holding back from installing all this stuff until NVIDIA put the pixmap extension into the release driver. I do quite a lot of development of OpenGL apps and I need to stick to the solid releases really.

> **datelus said:**
> btw- i dident add the BusID		"PCI:1:0:0" to the xorg.conf  no problem there?

It might be worth putting it in, but make sure you get it right. On my machine it is there as:
```
BusID           "PCI:2:0:0"
```

To find out, type lspci at a terminal and look for your graphics card. Mine looks like this:
```
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0291 (rev a1)
```
and it's the first set of numbers (02:00.0) that give the bus id.

Also, make sure you've also got:
```
Option "RenderAccel" "true"
```
in your "Device" section!

Cheers,
Rob

---

### Post by datelus on 2006-12-04
hmm ill try. now something went completely  wrong and i had to remove all the drivers and then install the normal ones again. ( only thing- splash screen is newone and nvidia settings) and  i thought  maybe it could be easier to install xgl. as i heard beryl is not so stable.

---

### Post by Azakus on 2006-12-04
Actually, I had this problem too until I got rid of XGL. I am now running Beryl on the AIGLX built-in on the nVidia 1.09XX drivers and It's working great now.

---

### Post by datelus on 2006-12-05
so i should get rid of all xgl on my system? ill try to do that using synaptic. And then try again with beryl. ?
my xorg.conf gets broken about 3 times a day, so its fun to fix it all the time :o

---

