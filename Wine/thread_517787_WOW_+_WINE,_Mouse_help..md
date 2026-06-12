---
title: "WOW + WINE, Mouse help."
date: 2007-08-05
forum: Wine
---

### Post by Ceemee on 2007-08-05
Wine is installed, from the repo on the WineHQ page.
WOW is installed and running with 40+ FPS.

my issue is I play a hunter and I need to use the "click both mouse buttons to start running and move mouse to steer" to effectively kite mobs.  

it doesn't work.  

- when I click both mouse buttons together, it toggles auto-run.

- I keep running after I release the mouse buttons.

- The mouse movement does not steer the character as it would in windows, it merely moves the steel glove pointer around the screen as normal

I have NOT installed any specific mouse drivers.  I don't know if this would be the issue since both mouse buttons work just fine for intended uses in the game individually.

** relevant info -

> Ubuntu 7.04 i386
> Mouse is a Logitech G7
> WINE version is 0.9.42 (from the Ubuntu specific repo, as stated above)


if you need any further information, I'll provide as quick as I can.

Thanks for any help.

---

### Post by captainstarbucs on 2007-08-05
This should be able to help you:

Go into WoW's key bindings options

look for the "auto run" bind, i think its the very first option, now you should see the default is "middle mouse button", unbind that, and it SHOULD work, lets hope so. If you're playing on a laptop, and pressing both in at the same time triggers what basically is a middle mouse.

---

### Post by Ceemee on 2007-08-05
Thanks, that was it.  It was a keybinding issue.    I didnt think to check to see how all the buttons where being recognized on my mouse.  apparently anything outside the normal two are recognized as button 3.

I had bound the "browser back / thumb button" to autorun, not realizing that it was re-binding the mouse-move function as well.

thanks again.

---

### Post by phrozenb on 2008-04-26
I have a similar problem. I have binded autorun on my "browser back" button, which in windows is button 4.

"Browser back" button works well under ubuntu in Firefox, but it doesn't work in Wow. Does wine emulate only a 3 bttn mouse or something? Is there any way to change that?

---

### Post by McLeod Brennaman on 2008-04-26
As far as I can tell, Wine has support for 5-"button" functionality -to an extent.- One of the only problems I've personally had with using a mouse in Wine is getting modifier keys (meta, super, hyper, ctrl, etc.) stuck when moving the mouse off the virtual desktop, such as switching workspaces to change a song, moving the virtual desktop, or just letting the mouse slip out of it on accident. Not sure if these problems occur when not using the emulated desktop, I just find it more stable, so I use it.

I put the word buttons in quotes because mouse buttons can be confusing. In most cases, left is button 1, right is button 2, middle click is button 3, the mouse wheel up is button 4, mouse wheel down is button 5, and any other buttons are either enumerated in your /etc/X11/xorg.conf, supplied by a mouse driver, or ignored. The mouse wheel is the "z-axis" in xorg.conf, the first number being "up" and the second being "down."

AFAIK. Only been using Ubuntu exclusively for a few months, and only got computer-savvy a little earlier, so I'm still a newbie to both linux and wine.

If you want to mess around with mouse emulation, xorg.conf is the place to do it, and I wish I could help you there, but I'm sure there's forum posts somewhere on it. Wine -should- take X11's mouse cues. AFAIK.

---

### Post by phrozenb on 2008-04-26
ok, after a bit of research on this:
```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Buttons" "7"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

This seems to work just fine for WoW and now my autorun button is working on my mouse. However, when i try to use the back/forward buttons (on my mouse) for browsing in Firefox it doesn't work. In order to make them work in Firefox I have to go for:
```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Buttons" "7"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 8 9"
EndSection

```

But then again, that won't work in WoW

Any ideas how to get BOTH working?

---

### Post by McLeod Brennaman on 2008-04-28
There is probably an easier method, but all I can think of is a simple script  to switch between (rename) 2 xorg.conf files, one for WoW and one for everything else? Not sure if that would require restarting X, more than likely it would. Alternatively, you could try to find out a way to remap keybindings and mousebutton bindings in FF, but I seriously doubt there's a simple and easy way to do this. Have you tried opening FF in Wine, seeing if that makes a difference? That would help in figuring out whether it was a Wine or X issue, whichever has the buttons backwards. Understandable if you don't want to run through a full Window$ install of FF, though, as it would be necessary to run it with Wine.

---

### Post by elmaz on 2008-04-28
To phrozenb:

No you don't have to change /etc/X11/xorg.conf, just keep the mouse mapping.

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Buttons" "7"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```Then open your firefox, type [FONT=Courier New]about:config[/FONT] in URL bar then enter, change the settings as following:

```
mousewheel.horizscroll.withnokey.action = 2
mousewheel.horizscroll.withnokey.numlines = -1
mousewheel.horizscroll.withnokey.sysnumlines = false
```You may need to restart your X to take effect, and both will get working.

[http://ubuntuforums.org/showthread.php?t=770619](http://ubuntuforums.org/showthread.php?t=770619)

---

### Post by ribbon on 2008-05-03
> **elmaz said:**
> To phrozenb:

No you don't have to change /etc/X11/xorg.conf, just keep the mouse mapping.

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Buttons" "7"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```Then open your firefox, type [FONT=Courier New]about:config[/FONT] in URL bar then enter, change the settings as following:

```
mousewheel.horizscroll.withnokey.action = 2
mousewheel.horizscroll.withnokey.numlines = -1
mousewheel.horizscroll.withnokey.sysnumlines = false
```You may need to restart your X to take effect, and both will get working.

[http://ubuntuforums.org/showthread.php?t=770619](http://ubuntuforums.org/showthread.php?t=770619)

THANK YOU! Worked for me! :D

---

