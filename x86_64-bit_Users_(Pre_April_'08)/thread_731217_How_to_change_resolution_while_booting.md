---
title: "How to change resolution while booting?"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by munceenuts on 2008-03-21
I was having trouble installing ATI Drivers so I tried a bunch of things and rebooted and when it started up again it said that it was running in low-graphics mode and that I need to change the settings.

I run 1600x1200 in Windows XP so I tried doing that for Ubuntu but I guess I need to correct drivers for my video card. When I restarted another time it shows the login screen scrunched up to the top half but you can't do anything because there are static marks all over it, especially on the bottom.

My main question is:

How can I change the resolution back to 1280x1024 before entering the login window?

Or how can I change it in the terminal? Because I got lucky and opened it up when the screen was messed up, but didn't know what to do to change it.

EDIT:

Here's what it looks like

[IMG]http://img143.imageshack.us/img143/9450/picture195mk0.jpg[/IMG]

---

### Post by DSn0wMan on 2008-03-21
You can reconfigure it from the comand line. This link describes the process pretty well. [http://psychocats.net/ubuntu/xorg](http://psychocats.net/ubuntu/xorg)

---

### Post by Yellow Pasque on 2008-03-21
You can use the xrandr command if you can get the terminal open again.
```
xrandr -s 1024x768
```

---

### Post by munceenuts on 2008-03-21
> **Temüjin said:**
> You can use the xrandr command if you can get the terminal open again.
```
xrandr -s 1024x768
```

Thanks, but I tried that and it just made that top part of the picture I posted bigger, but looks exactly the same.

So now it can't be the resolution. I guess it's something with the drivers.

Any other suggestions?

---

### Post by DSn0wMan on 2008-03-21
running sudo dpkg-reconfigure xserver-xorg from the command line will give you a nice little text based wizzard to walk you through reconfiguring your driver and display resolution amoung other things. Refer to the link I posted above.

You might also want to do some research on what driver works best with your video card before reconfiguring it.

---

### Post by munceenuts on 2008-03-21
> **DSn0wMan said:**
> running sudo dpkg-reconfigure xserver-xorg from the command line will give you a nice little text based wizzard to walk you through reconfiguring your driver and display resolution amoung other things. Refer to the link I posted above.

You might also want to do some research on what driver works best with your video card before reconfiguring it.

What command line? I tried doing that in the Grub menu and the terminal and nothing happened.

And that link only works if I can actually see and use my desktop, but thanks.

---

### Post by munceenuts on 2008-03-21
I just installed it yesterday so I'm just going to reinstall it. 

I wanted to see if there was a simple answer but I didn't have too many settings saved already so I'll just install it again.

---

### Post by munceenuts on 2008-03-21
> **DSn0wMan said:**
> running sudo dpkg-reconfigure xserver-xorg from the command line will give you a nice little text based wizzard to walk you through reconfiguring your driver and display resolution amoung other things. Refer to the link I posted above.

You might also want to do some research on what driver works best with your video card before reconfiguring it.

I just reinstalled Ubuntu and followed the instructions in that link and now I have the same problem.

It worked and it said that xserver would load every time I booted up and then it told me to log out and when I logged out I got the same thing as in the picture above.

Is there a way to disable that without using the terminal?

---

### Post by DSn0wMan on 2008-03-22
What video card do you have, and what driver are you using? If you need to bring up a terminal you should be able to do so by pressing ctrl+alt+F1

---

### Post by munceenuts on 2008-03-22
I have an ATI Radeon 9550. I was using the drivers Ubuntu came with. I just installed 8.04 and sadly faced another problem.

This time I had an error with Gnome Daemon crashing. It would boot into the desktop and give me an error and would change the fonts and themes, but I'd still be able to use it, but now it gives me a black screen after the error.

---

### Post by bailbath on 2008-03-22
Use the rescue option in the grub menu it will give you the options you need. If you want a more stable experience try using ubuntu 7.10 or waiting till 8.04 is released in April. Using a beta operating system will always throw up a problem or two.Do some research on your hardware within this forum and you may find answers to problems before you get the problem!!
All the best.
IAN

---

### Post by munceenuts on 2008-03-24
I just ended up reinstalling it lol. I'm trying to keep this one intact until the final release though. My problem seems to be with xserver-xgl, it always gives me problems.

---

### Post by Yellow Pasque on 2008-03-27
Do not use XGL. Use the open-source radeon driver, which will do desktop effects without XGL.
[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

---

### Post by bestguy on 2008-03-27
hi 

first switch to a terminal ALT + F2....

login and use

sudo aticonfig --initial -f

this will reset your driver config

then reboot

---

