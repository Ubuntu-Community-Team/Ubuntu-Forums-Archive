---
title: "after booting : screen goes blank.."
date: 2006-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by avarice on 2006-05-11
I'm using a acer ferrari 4000, amd64 turion, ati radeon x700 128mb. I am able to install ubuntu without any problems,but for some reason after its loads the modules, the screen goes blank.

The 0s can load, as i've tried keying in my username and pw, i can hear login tones but just no display, is there anyway to solve this?. ty

---

### Post by methodx on 2006-05-18
i am having the same problem...i'm guessing its video problems also but i havent had time to mess with it.

---

### Post by Tadhg on 2006-05-18
i have the same problem. Its probably an xorg.conf problem. Haven't had time to investigate. To get you started, hit CTRL ALT and Backspace when your screen has gone blank and youll be able to log in without xserver. Than go to
sudo pico /etc/X11/xorg.conf and have a look though there.Its more or likely where the problem is.

---

