---
title: "G3 iMac 600mhz Blank screen with live CD"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thmanx on 2005-10-15
i am trying out Linux on my iMac, so i made a Live CD.
the CD does great untill after the unbuntu final flash screen w/ loading bar
after that loads,i get a never ending blank screen

i want to partition and install ubuntu ona  partition but iam afraid the same thing will happen if i  install it.

---

### Post by twongkee on 2005-10-20
have seen this:
[http://ubuntuforums.org/showthread.php?t=75604](http://ubuntuforums.org/showthread.php?t=75604)

for "step by step" another posting had slightly better instructions:

you need to go to "console" (text mode) and use an editor to change the X frequency settings....

for a new user, nano or pico may be a better editor,
for one familiar with linux, you can use  vi as your  editor.

so steps:
boot, and wait for the "startup sound" and the cd to  stop spinning... (blank screen in X)

1)goto console
hit CTRL-ALT-F1 and get a console prompt 
(note, i had a non apple wireless keyboard, and that didn't work, I had to dig up my original apple keyboard and hit
CTRL-OPTION-F1)

2)edit X config file
using "friendly editor" (google for keyboard movements)
[http://www.nano-editor.org/](http://www.nano-editor.org/)

sudo nano /etc/X11/xorg.conf

find the frequency settings and change:

[B]Section "Monitor"

    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 60-60
    VertRefresh 43-117

EndSection

[/B]

3) restart X
-- various ways
3a)a possible way:
(from another post)
kill the xserver (switch to X with ctrl-alt-F7 or CTRL-OPTION-F7 and hit ctrl-alt-backspace to kill it) and restarted with 'startx'.

3b)what I did, more complex but it worked for me:
q: anyone  know the default root  password?
I don't so I had to set it:
sudo bash
(you are now "root")
change root password:
**passwd**
it will prompt for a new password for root, change it and don't forget!

then you can type (since you are still root)
**init 1**
(and it prompts you for password)
this drops to debug/troubleshooting mode
then
**init 2**
restarts all back with X working...

---

