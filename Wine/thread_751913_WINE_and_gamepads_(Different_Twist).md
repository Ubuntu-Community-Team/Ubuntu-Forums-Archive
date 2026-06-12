---
title: "WINE and gamepads (Different Twist)"
date: 2008-04-11
forum: Wine
---

### Post by reponzo01 on 2008-04-11
Sadly, I have been all over this forum and the Internet searching for an answer to this. But alas, to no avail. And I know others are experiencing the same problem trying to get gamepads to work under WINE. WINE sees the gamepads but somehow does not map either buttons or axes correctly.

My issue is this: All of my buttons work except Up and Left. Nothing at all happens with those. The gamepad works perfect under native Linux apps. Oh, and for some reason, under WINE, my gamepad works better when connected to a rear USB port instead of a front one :confused:

Now here's the new spin I wanted to try out. I figured, if I was in native Windows, using the Control Panel, I resolved many a gamepad issues in my day. What if I could run control panel under WINE and calibrate my gamepad internally within WINE?

Now, running the Control Panel under WINE is easy
```
cd .wine/drive_c/windows/system32
wine control.exe
```

Granted, it doesn't display properly because of a ton of missing dlls but that's besides the point. To run just the joystick section:

```
wine control joy.cpl
```

However, I get the following error:

```
fixme:dinput:IDirectInputAImpl_QueryInterface Unsupported interface !
```

And in WINE, an error box shows up saying "Necessary support files not found."

I'm sure it has something to do with missing dlls. Whatever I need, I can pull from my Windows installation.

Would anyone, by chance, know what dlls I need?

Thanks!!

---

### Post by Ferrat on 2008-04-11
there is a way 

[http://ubuntuforums.org/showthread.php?t=610527&highlight=wine+joytokey](http://ubuntuforums.org/showthread.php?t=610527&highlight=wine+joytokey)

I got it working with a xbox pad, but it's a joytokey solution and might not be what you want?

---

