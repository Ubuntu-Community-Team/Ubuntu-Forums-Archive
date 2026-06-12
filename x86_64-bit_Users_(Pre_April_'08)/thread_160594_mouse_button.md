---
title: "mouse button"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-04-15
how can I make the mouse button useful?

on OS X, I could use it with the crtl button to bring up a 'right-button' menu. I can't find any such combination on ubuntu. Am I missing something?

Max.

---

### Post by dpny on 2006-04-15
[QUOTE=davidmaxwaterman]how can I make the mouse button useful?

on OS X, I could use it with the crtl button to bring up a 'right-button' menu. I can't find any such combination on ubuntu. Am I missing something?

Max.[/QUOTE]

On my laptop, F11 is mapped for middle click and F12 for right click.

---

### Post by davidmaxwaterman on 2006-04-15
[QUOTE=dpny]On my laptop, F11 is mapped for middle click and F12 for right click.[/QUOTE]

Ah ha! Right you are :)

(How odd - I wonder why they didn't do the same as on OS X).

Thanks.

Max.

---

### Post by 3rdalbum on 2006-04-16
You can also get a cheap two/three button PC mouse, but you'll need to turn down its response in Ubuntu otherwise it'll feel like you're running Windows :-)

---

### Post by aimislame15 on 2006-04-16
> You can also get a cheap two/three button PC mouse, but you'll need to turn down its response in Ubuntu otherwise it'll feel like you're running Windows 

good posting :P

---

### Post by jdp on 2006-04-18
Multibutton scroll wheel mice generally work great in OS X as well...

---

### Post by madk on 2006-04-19
If you edit /etc/sysctl.conf so that it says:

dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 97
dev/mac_hid/mouse_button3_keycode = 100

you can use Fn+CTRL for middle click and Fn+ALT for right click; I find it a lot more convenient than using F11 and F12.

---

### Post by Churusaa on 2006-05-09
You can also get Mouseemu and edit /etc/default/mouseemu to look like this to make the mouse behave as it does in OSX:

```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272"         # Cmd + click
RIGHT_CLICK="-right 29 272"        # Ctrl + click
#SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 0" # block mouse for 300ms after a keypress

```

---

