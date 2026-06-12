---
title: "Printing from Adobe Reader 9.1.3"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2009-07-18
I am using Adobe Reader 9.1.3 on Jaunty x86_64, installed from Ubuntu
repositories via Synaptic. I am printing to a Laserjet 8000DN via
ethernet.

When I attempt to print multiple copies of a document I get only one
copy. 

Looking at the command that Reader is sending I can see why. The
command contains "-o Copies = x." I can change x to whatever I want by
selecting a different number in the GUI (you can't edit the line
manually in Reader 9.1). But it still prints only one copy. That is
because "-o Copies = x" is not valid lpr syntax. The correct syntax is
"-#x." And lpr ignores all commands that it does not understand.

However, I must have misunderstood something, because I can't believe
Adobe released Reader 9.1/Linux with such an obvious and major glitch.

I hope someone can enlighten me.

---

