---
title: "keybindings"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by hatefulthreatening on 2005-11-23
I'd like to make my capslock a control button. I'd also like to bind the left apple button to control and the right apple button to alt. Is this possible?

I tried to make capslock a control button in the kde and the gnome settings menu, but this didn't work on my ibook as it did on my x86 desktop. This is all an ibook g4 model that's about a year old. The capslock thing just doesn't work for some reason. And I can't seem to bind each apple key separately.

I made an identical post on the kubuntu ppc board a few days ago with not luck. I hope it's ok to repost over here.

---

### Post by frodon on 2005-11-24
When you run the "xev" command in a terminal and push the button do you get an output ? If yes it should be easy to create a shortcut. The output should looks like that : ```
KeyPress event, serial 28, synthetic NO, window 0x3000001,
    root 0x46, subw 0x0, time 3246433747, (79,19), root:(83,625),
    state 0x10, keycode 27 (keysym 0x72, r), same_screen YES,
    XLookupString gives 1 characters:  "r"
```Here 0x72 is the hexa value to use for the shortcut.

---

### Post by hentaidan on 2005-11-24
I use xmodmap ( [http://www.xfree86.org/4.2.0/xmodmap.1.html]("http://www.xfree86.org/4.2.0/xmodmap.1.html") ) and the outputs from xev to remap my keys.

I remapped the enter (? the one to the right of the right apple key) key as middle click with this:

```
xmodmap -e "keycode 108 = Pointer_Button2 Pointer_Drag2"
```

But for some reason its stopped working :???: I'm still trying to work out why...

Swapping Ctrl and Capslock seem to work fine for me (theres a thread above it), except for the LED on the key.


P.S. if you do use xmodmap, be careful not to remap any alphanumeric keys... I did (by accident..) and the screensaver came up and locked me out. Guess what, I had remapped a letter of my password to something else!

---

### Post by khc on 2005-11-24
[QUOTE=hentaidan]
Swapping Ctrl and Capslock seem to work fine for me (theres a thread above it), except for the LED on the key.][/QUOTE]

Do you use xmodmap to swap ctrl and capslock? I couldn't get it working, what's the command that you used?

---

### Post by hentaidan on 2005-11-25
No I haven't swapped the keys, but I'll play around and see if I can get it to work.

---

### Post by hentaidan on 2005-11-25
Had a quick play with xmodmap but I cant work out how to get swap the keys.

What happens when you use the setting in Keyboard preferences? I tried it on the live cd, and it seems to work fine.

This is the (relevant) output from xev:

Before ctrl/caps swap:

```

<output for control>
KeyPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x40, subw 0x0, time 184051, (172,-7), root:(1015,42),
    state 0x2, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x40, subw 0x0, time 184311, (172,-7), root:(1015,42),
    state 0x6, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
</output>

<output for caps lock>
KeyPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x40, subw 0x0, time 189848, (172,-7), root:(1015,42),
    state 0x2, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x40, subw 0x0, time 189848, (172,-7), root:(1015,42),
    state 0x2, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes:

PropertyNotify event, serial 30, synthetic NO, window 0x2c00001,
    atom 0x115 (XKLAVIER_STATE), time 189853, state PropertyNewValue

VisibilityNotify event, serial 30, synthetic NO, window 0x2c00001,
    state VisibilityUnobscured
</output>

```

After the ctrl/caps swap i get this output from xev:

```

<output for ctrl>
KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 311393, (166,-13), root:(991,36),
    state 0x2, keycode 37 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

PropertyNotify event, serial 29, synthetic NO, window 0x2e00001,
    atom 0x115 (XKLAVIER_STATE), time 311397, state PropertyNewValue

KeyRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 311623, (166,-13), root:(991,36),
    state 0x2, keycode 37 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes:
</output>

<output for caps lock>
KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 313982, (166,-13), root:(991,36),
    state 0x0, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 313982, (166,-13), root:(991,36),
    state 0x4, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
</ouput>

```

What does your ouput from xev look like? Do the keysyms change?

---

### Post by hatefulthreatening on 2005-11-25
Capslock only seems to generate an event in xev when I press the key down to enable capslock or when the key is released to disable capslock. There doesn't seem to be any event when I release the key when enabling capslock or when I press the key down to disable capslock. 

So the capslock key isn't behaving like any of the other machines. It's not generating *both* a keydown and keyup event like normal buttons or like capslock buttons on my x86 machine.

For the left and right apple keys, the xev events look identical. Does this mean I can't bind them to two different keys?

---

### Post by hatefulthreatening on 2005-11-25
Err, I'm actually slightly wrong.

The capslock generates *both* a keydown and a keyup event when I press the keydown to enable capslock. And it generates *both* a keyup and a keydown when I release capslock button to disable caps. This makes it useless as a control button...

The kde menu options tells me it's running this command to swap the buttons: setxkbmap -option ctrl:swapcaps

---

### Post by khc on 2005-11-25
[QUOTE=hatefulthreatening]Err, I'm actually slightly wrong.

The capslock generates *both* a keydown and a keyup event when I press the keydown to enable capslock. And it generates *both* a keyup and a keydown when I release capslock button to disable caps. This makes it useless as a control button...

The kde menu options tells me it's running this command to swap the buttons: setxkbmap -option ctrl:swapcaps[/QUOTE]

I use gnome, and gnome's keyboard setting for swapping ctrl/capslock doesn't work on my powerbook (it works on my x86 desktop, however)

Using setxkbmap -option ctrl:swapcaps, capslock now does nothing (except LED), and ctrl becomes the capslock.

---

### Post by hatefulthreatening on 2005-11-25
I found a solution online, but I really don't like it. It involves a kernel patch =(. I don't want to deal with compiling my own kernel and keeping track of upgrades and security updates myself.

[http://hans.fugal.net/yodl/blosxom.cgi/mac/caps.html](http://hans.fugal.net/yodl/blosxom.cgi/mac/caps.html)

Is this just some dirty hack? Is it worth requesting that the ubuntu team include something similar to this in their kernel releases?

Why did apple go and break something so simple?

---

