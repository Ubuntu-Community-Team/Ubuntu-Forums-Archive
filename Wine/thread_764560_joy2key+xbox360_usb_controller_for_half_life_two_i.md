---
title: "joy2key+xbox360 usb controller for half life two in WINE"
date: 2008-04-24
forum: Wine
---

### Post by 99bluefoxx on 2008-04-24
so i found a xbox360 controller with an USB adaptor for $4 and bought it, thinking ide use it in WINE to play half life two
found a program joy2key to make it input equivilant keystrokes, but have no idea how it use it
the idea is use the left analog for movement[w/a/s/d], the d-pad [up=0 down=c left=9 right= - ], the left analog for mouse movement[up=same as moving mouse away from self, down = mouse towards self, so on], then the buttons: y=f, a=spacebar, b=e, x=q, xbox=~, start=esc, back= pause/break, LB=mouse wheel down, RB=mouse wheel up, LT=right mouse button, RT=left mouse button
and you get the idea
my controller shows as /dev/input/js0, i made a link to it as /dev/js0, but beyond that i cant get joy2key to work
i tried just using it and only left analog worked for looking around, which i dont want it to do :\
any help here would be great, thanks

---

### Post by jaygo on 2008-07-15
I'd skip the joy2key program and work on mapping the input from that controller. Look into modifying your xorg.config, maybe using xmodmap, and testing what output each button on your controller gives using that one terminal command ... all I remember is that it listens to all of your input devices and reports what they give in "machine language".

You could also try mapping the joystick buttons/dpad directly in HL2. Something like Options > keyboard > move forward : [press up on your dpad].

Report back if you figure it out.

GLHF

---

### Post by zephyrus17 on 2008-09-04
Sorry, but running "xev" in the Terminal doesn't work. It doesn't recognise my buttons. I'm using Arch linux, by the way.

---

