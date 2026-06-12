---
title: "starcraft audio dropout"
date: 2008-11-10
forum: Wine
---

### Post by zero777zero on 2008-11-10
running starcraft through wine, ever since my upgrade to 8.10, i'm playing for 20min or so and the audio just completely drops. i restart and i'm good for another 20min.

---

### Post by RobOrr on 2009-06-19
Thought I'd bump this issue as it doesn't appear to be solved and having just installed starcraft I get the exact same issue. the game runs perfectly, and then after a short period of around 10 to 20 minutes of play, the sound (both music and fx) disappears completely. Upon exiting starcraft, the sound plays again for the last half a second or so as it quits.

wine version: 1.0.1
heres the terminal output:
```

fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f420,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3554
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
---@---:~/.wine/drive_c/Program Files/Starcraft$ 

```

has been tried with 98, 95, XP and Vista compatibility set.

---

### Post by RobOrr on 2009-06-19
have solved the problem by inserting the following registry key into wine:

HKCU > Software > Wine > Alsa Driver

and giving it a string to use direct sound hardware.

to do this, go to your home/.wine/drive_c/windows folder in terminal and run this command:

```
wine regedit.exe
```

navigate to the wine folder as above, right-click on it and select New > Key.
give this the name Alsa Driver (note space and capitalisation).

now to give this key a string value - select the Alsa Driver key, and on the right hand side right click and select New > String Value.
Name this string "UseDirectHW" and press enter. now doubleclick the string on the right and enter "yes".

There are plenty of other keys that can help wine out that cannot be created or altered in winecfg. go to the wine wiki (wiki.winehq.org) to find out about the others.


Hope this solves your problem, as it solved mine!

---

### Post by moonkey on 2009-07-02
> **RobOrr said:**
> 
Hope this solves your problem, as it solved mine!

Thanks! :D I was experiencing the same problem.

---

### Post by Th3_uN1Qu3 on 2009-07-03
You can also access regedit directly via Alt+F2, it makes things a bit faster. :)

---

