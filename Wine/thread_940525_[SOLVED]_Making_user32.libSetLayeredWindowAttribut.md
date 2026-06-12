---
title: "[SOLVED] Making user32.lib:SetLayeredWindowAttributes display transparent windows"
date: 2008-10-07
forum: Wine
---

### Post by Orange_and_Green on 2008-10-07
Hello everybody :)

A couple of years ago I made a little utility program for my girlfriend. I had to use visual basic (shame:oops:) because at that time her laptop's hardware was not supported by the linux kernel, so she would use only windows.

Now that she has become my wife\\:D/ I've finally managed to install Hardy Heron on it, and except for the microphone everything seems to be working fine now:guitar:

I used winetricks to install vb4 support, and actually my little program does start up too, which is really great:)

However, one feature that I thought was quite cool is not supported: namely, I had used the SetLayeredWindowAttributes function from the user32.dll library to make the window's background transparent. When run under wine, the transparent parts now appear as a big blocky ugly black box (I already tried disallowing the window manager to control & decorate the windows with no luck).

I should really port the whole thing into Gtk + cairo, but in the meantime, does anyone have a suggestion as to how I can make the transparency work in wine?
Or at least a good tutorial on cairo and transparent backgrounds? :p

Thank you for reading this post, and many thanks in advance for any help:KS

---

### Post by Orange_and_Green on 2008-10-08
**bump**

---

### Post by Orange_and_Green on 2008-10-09
Looking more closely at wine's output, I found a line reading "fixme:win:SetLayeredWindowAttributes(0x1002c, 0x00000000,0,1): stub!"

So I guess this answers my question... Oh well, too bad :( I guess I really need that tutorial quickly now...

A big thanks to all those of you who took the time to read this thread. SOLVED.

---

