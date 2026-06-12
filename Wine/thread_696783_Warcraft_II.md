---
title: "Warcraft II"
date: 2008-02-14
forum: Wine
---

### Post by mistaWAC on 2008-02-14
So I looked around on the forums and couldn´t really find anything that applied to my situation.  I´m running a dual boot between XP Pro with every new update as well as Ubuntu 7.10.  I installed Warcraft III and The Frozen Throne onto the Windows partition while in XP and tested it - works fine. I now have WINE installed and here is how I atmpted to start W3:TFT:

>> Navigate to the dos_devices folder in my .wine folder
>> Navigated to the Warcraft III folder in Program Files (the D: points to the windowsxp partition which I have mounted here)
>> I attempt to start Warcraft III.exe or Frozen Throne.exe and they both freeze at the splash screen giving some weird errors in the terminal
```

err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f7d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3dc,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x3c00003
  Serial number of failed request:  93
  Current serial number in output stream:  102
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  10 (X_UnmapWindow)
  Resource id in failed request:  0x3800001
  Serial number of failed request:  41
  Current serial number in output stream:  45

```

Any help on setting up W3 with this situation please?

---

### Post by Alpha7 on 2008-02-14
My thought would be that need to install WC3 from inside of Ubuntu with wine so it can be recognized as a program with wine correctly and written to the registry. Just trying to run the game doesn't do this as far as I know.

---

### Post by Sugi on 2008-02-14
Your title reads as "Warcraft II"  not warcraft 3, because frozen throne is warcraft 3.  I don't think you meant dark portal.  did you?


Anyways, Warcraft 3 broke after wine version 0.9.51 (anything before should work, but you need to use 0.9.51)
(these versions do not work with Warcraft 3 (0.9.52, 0.9.53, 0.9.54, 0.9.55)

You can either remove wine and install 0.9.51 (it's tested to work.  it works for me under 0.9.51)
$sudo apt-get remove wine
go to winehq website and download 0.9.51
[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

or

you can also consider installing playonlinux.com  I am currently using it for all my games that require older version of wine.
[http://www.playonlinux.com]("http://www.playonlinux.com")

Sugi

---

### Post by FrozenFox on 2008-02-14
> **Sugi said:**
> 
(these versions do not work with Warcraft 3 (0.9.52, 0.9.53, 0.9.54, 0.9.55)



Warcraft 3: Frozen Throne with the latest patch works just fine for me on 0.9.55, including netplay..

---

### Post by Sugi on 2008-02-14
I have read 0.9.51 was ideal for best performance.  What version of Warcraft 3 & Frozen Throne are you using?

Sugi

---

### Post by mistaWAC on 2008-02-14
I´m going to try installing it via WINE rather than running it from my XP partition.  What the fellow up top said about that makes sense.  I´ll keep y´all posted..

And thanks a ton for the help..

---

### Post by FrozenFox on 2008-02-15
> **Sugi said:**
> I have read 0.9.51 was ideal for best performance.  What version of Warcraft 3 & Frozen Throne are you using?

Sugi

For performance that works just as well as anything for me, I used wine 0.9.55, wc3:ft 1.21b, and add -opengl to the end of the command or shortcut to load the game. IE, the shortcut in my start menu is:

env WINEPREFIX="/home/fox/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl

Of course, 
wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl

will do the same thing if you don't have multiple wine copy thingos laying around.

The only glitch i have is that the brightness or gamma or whatever won't change, but that's a minor issue.

P.S., Sugi: Is that signature supposed to be "all but one ARE" linux? ie there are 4 linux machines and 1 non-linux machine? That's a little strange for a signature if you meant as it says right now. :)

---

