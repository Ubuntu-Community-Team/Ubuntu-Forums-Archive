---
title: "4 quick questions"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by xslf on 2005-12-02
Hi all.
I have Breezy installed in a iMac G3 (400Mhz) and it works great. However, I do have a few little questions.

1) Is there a backports repository for PPC? I didn't see anyone mentioned.
2) I use the original mouse the came with the iMac (the single button round one). I do have F11 as middle click and F12 as right click, but I was wondering- is there any way to simulate the "click and hold for right click" behavier from MacOS?
3) I am using the original keyboard that came with the iMac. For some reason, the alt/option key isn't recognised: xev simply doesn't see it. The key does work properly under OSX. Any idea how to solve this? Since this is the only alt on the keyboard, I am stock without an alt key. Other keys work fine.
4) This keybord only has one delete/backspace key, mapped to backspace. Does anyone else use this keyboard? If so- what do you do for the missing delete key?

Thanks!

---

### Post by teaker1s on 2005-12-02
there is a mouse solution I think that there is a utility in repositories,
If you can't find a solution to the keyboard you can xmodmap and create your own keyboard layout search wilki for multimedia

---

### Post by Entity on 2005-12-02
[QUOTE=xslf]Hi all.
I have Breezy installed in a iMac G3 (400Mhz) and it works great. However, I do have a few little questions.

1) Is there a backports repository for PPC? I didn't see anyone mentioned.
2) I use the original mouse the came with the iMac (the single button round one). I do have F11 as middle click and F12 as right click, but I was wondering- is there any way to simulate the "click and hold for right click" behavier from MacOS?
3) I am using the original keyboard that came with the iMac. For some reason, the alt/option key isn't recognised: xev simply doesn't see it. The key does work properly under OSX. Any idea how to solve this? Since this is the only alt on the keyboard, I am stock without an alt key. Other keys work fine.
4) This keybord only has one delete/backspace key, mapped to backspace. Does anyone else use this keyboard? If so- what do you do for the missing delete key?

Thanks![/QUOTE]

1) [Yes]("http://ubuntuforums.org/showthread.php?t=40291") but no extras for PPC I think, you simply need to add the following to your /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

4) On my powerbook, Fn+Backspace = Delete

---

### Post by xslf on 2005-12-02
> there is a mouse solution I think that there is a utility in repositories,
Do you happen to know the name of it? 

> Yes but no extras for PPC I think
Thanks!
BTW, does anyone happen to know if there is an updated version of OpenOffice.2 for PPC?

> On my powerbook, Fn+Backspace = Delete
Thanks. Too bad that I don't have a Fn key. I'm trying to think of something else that isn't taken already.

---

### Post by teaker1s on 2005-12-02
Mouseemu/imwheel/Wmbutton which modify mouse-sorry i can't  find the exact one I found before I looked but I can't remember the name.
maybe someone else will know
[here]("http://lists.debian.org/debian-powerpc/2005/07/msg00060.html")
and the look at the followups

---

### Post by teaker1s on 2005-12-02
> On Sat, Jul 02, 2005 at 05:23:49PM -0700, nuno romano wrote:
> > How can I emulate a three-button mouse from
> > a macintosh one-button mouse?
found this it's debian so I should work posted 2005 so recent
>   $ grep mac_hid /etc/sysctl.conf
>   dev/mac_hid/mouse_button_emulation = 1
>   dev/mac_hid/mouse_button2_keycode = 87
>   dev/mac_hid/mouse_button3_keycode = 88
>
> (for F11 == middle and F12 == right)

I've found mouseemu quite useful - it also emulates a scroll wheel when
pressing alt and scrolling on the trackpad. Plus it can block the trackpad
while typing.

Added benefit: it all works on the generic input layer, with no special
kernel code involved. IIRC the kernel support for button emulation is
scheduled to be removed, much as I hate to see it go for historic reasons.

---

### Post by xslf on 2005-12-02
> for F11 == middle and F12 == right
I already have that.

I am looking for something that will give me right click on a long mouse click, in **addition to** the keyboard shortcuts.

---

