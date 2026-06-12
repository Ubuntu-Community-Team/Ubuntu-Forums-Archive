---
title: "Weird problem: Mouse loses ability to click"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by jchysk on 2008-12-16
I've just upgraded to 8.10 from 8.04 and everything seems to have gone smoothly except for one problem. My mouse, a Logitech G7, after a period of use suddenly loses it's ability to click.
It's really weird because when it happens if I switch user and go to the main login screen the mouse is able to click again, but if I log back in the mouse no longer works. If I log out completely and log back in the mouse works fine. 
It seems to take awhile before the mouse stops clicking, like a day or longer. I haven't noticed any particular programs that may be the cause. The only programs that have been running in each instance of the mouse losing it's clicking ability are Firefox and Pidgin.
The keyboard still works fine, and I can still see the mouse pointer and move it around when this happens.

Other things besides the 8.10 is I've upgraded the Nvidia restricted drivers to version 177. I'm running a Q6600 at 2.4GHz with Ubuntu 64-bit.

If anyone has any ideas or can help I'd really appreciate it. Don't hesitate to tell me things that may seem really obvious to most Ubuntu users, I'm really not very knowledgeable of the operating system.

---

### Post by John Jason Jordan on 2008-12-17
> **jchysk said:**
> I've just upgraded to 8.10 from 8.04 and everything seems to have gone smoothly except for one problem. My mouse, a Logitech G7, after a period of use suddenly loses it's ability to click.
It's really weird because when it happens if I switch user and go to the main login screen the mouse is able to click again, but if I log back in the mouse no longer works. If I log out completely and log back in the mouse works fine. 
It seems to take awhile before the mouse stops clicking, like a day or longer. I haven't noticed any particular programs that may be the cause. The only programs that have been running in each instance of the mouse losing it's clicking ability are Firefox and Pidgin.
The keyboard still works fine, and I can still see the mouse pointer and move it around when this happens.

Other things besides the 8.10 is I've upgraded the Nvidia restricted drivers to version 177. I'm running a Q6600 at 2.4GHz with Ubuntu 64-bit.

If anyone has any ideas or can help I'd really appreciate it. Don't hesitate to tell me things that may seem really obvious to most Ubuntu users, I'm really not very knowledgeable of the operating system.

This has been reported a lot with Intrepid. It does not affect me so I have not followed the issue closely. As far as I know it affects people using two screens. A launchpad bug report has been filed, but I don't have the URL handy and I don't know if there has been any resolution.

But at least I can tell you that you are not alone.

---

### Post by dcstar on 2008-12-17
> **John Jason Jordan said:**
> This has been reported a lot with Intrepid. It does not affect me so I have not followed the issue closely. As far as I know it affects people using two screens. A launchpad bug report has been filed, but I don't have the URL handy and I don't know if there has been any resolution.

But at least I can tell you that you are not alone.

This is probably going to annoy a lot of people, but my experiences of using Ubuntu since the very first version have taught me to **never** install the latest release until at least a couple of months after the release date.

My 8.04 LTS base system is still rocking along quite solidly and if I want any of the 8.10 features, I just fire it up in a VM.

---

### Post by grzemach on 2008-12-17
I was thinking about staying with 8.04 too, but 8.10 is working nice for me. Without this mouse issue. this is really annoying problem. But what can i do? only reset X-server and run my applications one more time.

Do you know any other solution for this (other than CRTL+ALT+Backspace), so i don't have to reset my X-server?

---

### Post by philinux on 2008-12-17
When it stops working have a look at the log files in system>admin>system log. There should be error messages relating to it.

---

### Post by jchysk on 2008-12-24
Dec 24 20:28:55 jchysk-desktop bonobo-activation-server (jchysk-12659): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ILU8vjff35: Connection refused

Dec 24 20:45:08 jchysk-desktop bonobo-activation-server (jchysk-13461): could not associate with desktop session: Failed to connect to socket /tmp/dbus-WJd6Cd29Ew: Connection refused

Dec 24 20:45:13 jchysk-desktop bonobo-activation-server (jchysk-13525): could not associate with desktop session: Failed to connect to socket /tmp/dbus-WJd6Cd29Ew: Connection refused

These are the messages from the system log that I think correlate with the mouse losing it's clicking ability. I hadn't had the problem in awhile. The last couple times it happened though I had multiple browsers of Firefox open on two separate monitors (I do run dual display). I thought this information might help someone figure out what's wrong. In the meantime I'll just try to keep only one browser open at a time.

---

### Post by John Jason Jordan on 2008-12-24
> **jchysk said:**
> These are the messages from the system log that I think correlate with the mouse losing it's clicking ability. I hadn't had the problem in awhile. The last couple times it happened though I had multiple browsers of Firefox open on two separate monitors (I do run dual display). I thought this information might help someone figure out what's wrong. In the meantime I'll just try to keep only one browser open at a time.

If you read through this thread you will discover that it has nothing to do with how many browser windows you have open. As far as I can tell absolutely the only people affected are those who are running two monitors. There is your problem. The fact that you had a browser window open on each monitor is irrelevant. It is that you had two monitors that is causing the problem.

---

### Post by jchysk on 2008-12-26
I decided to research this a little more and found that a lot of others have the same problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/290406](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/290406)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/296167](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/296167)

Reading through I found that people that switch to twinview from xinerama no longer have the problem.  Downgrading xorg works for some, downgrading from 8.10 to 8.04 seems to work. 
Many people, including me, are able to reproduce the bug by messing around with multiple instances of firefox or another browser.
I guess I'm lucky though where I only seem to trigger the bug every few days where a lot of people were having the problem every couple hours with only a couple annoying and tedious workarounds to fix it.
Didn't see anyone claim a real fix anywhere for this problem though.

Since it's not bothering me too heavily right now and I seem to be able to avoid it by going easy on the browsers, I'll just check back in like a month if the problem is still occurring and see if there's a fix yet. Or just hope an update I install along the way has fixed it.

---

