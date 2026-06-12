---
title: "[SOLVED] Wine and Logitech Rumblepad for Fifa"
date: 2007-11-11
forum: Wine
---

### Post by El_Matthews on 2007-11-11
Gents

I have a cordless logitech rumblepad that works fine in the most of the cases. It's plug and play so I didn't install anything to make it work.

In games as need for speed it runs great with cedega. Now when I try it with fifa 08 or 07 with wine or cedega the cursor always goes up in the game. This makes it impossible to select anything in the menu and playing fifa with the keyboard is no fun at all.

I tried with jscalibrator but this makes it worse. 

Did anybody made fifa playable with a joystick?

Greetings

Matthews

---

### Post by El_Matthews on 2007-11-14
Nobody knows how to make this controller work correctly with wine?

---

### Post by uranus0206 on 2007-11-15
i have a joystick but not logitech,
although i can run the game and play, in the selection menu, it will keep moving
among every option but not confirm

but when in game it work correctly, but it will affect game fluency

---

### Post by Ferrat on 2007-11-15
If the game supports joystick/gamepad then you may need to map it in wine regedit 

> +-DirectInput
      |  |
      |  +->*<joystick name> = <axes mapping>
      |      [Linux only (js* devices). This maps axis of joystick "joystick name".  The "axes mapping" is comma
      |       separated list of "axes type"s - one for each joystick axes (hat-pov uses 2 axis).
      |       "axes type" is one of: X, Y, Z, Rx, Ry, Rz, Slider1, Slider2, POV1, POV2, POV3, POV4.
      |       To find the joystick name run 'WINEDEBUG=+dinput wine program.exe 2>&1 | grep joydev_enum_device'
      |       Example: "Logitech Logitech Dual Action"="X,Y,Rz,Slider1,POV1". (two "Logitech" is not a typo)]

Otherwise JoyToKey works great under wine and can map any buttons to any key more ot less and works ingame on wine games (tried with a few such as Guild Wars, GTA:SA, Legacy of Kain ect. trying to get the old Mortal Kombat 4 up right now) =)

---

### Post by El_Matthews on 2007-11-15
added the registry keys but problem persists. 

JoyToKey or qjoypad are not working in this case because the games detects the joystick already.

---

### Post by El_Matthews on 2007-11-21
Gents, 

did anybody had more success as I did?

Greetings

Matthieu

---

### Post by El_Matthews on 2007-11-23
It works now, don't ask me how or why but all ok now.

---

### Post by arigram on 2007-11-25
Can somebody guide me through activating my simple Logitech Precision gamepad into Wine's registry as mentioned above?

---

### Post by wapsi on 2008-02-12
I've the same problem. Please help us :) I want to play Fifa'08 on gnu/linux!

---

### Post by hangar_18 on 2008-06-08
same here.
actually its some software issue in fifa .. no patch of fix found yet :(

---

### Post by El_Matthews on 2008-06-24
I don't know if this is usefull but I play fifa08 with Cedega and my cordless rumblepad. Maybe you can test it with Cedega?

I had to configure the config file but once done this works very well.

---

