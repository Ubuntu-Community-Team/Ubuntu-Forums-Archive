---
title: "Took the plunge... hit a rock. (ati question)"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by tracetheace on 2008-09-04
Alright, I installed ubuntu 8.04 just yesterday. I've been playing around with it and learning how to use the terminal. Great OS, anyways to the problem.

I'm using wine 1.1.3 to run steam and play counter-strike 1.6, but I'm having some issues and I believe they're linked to my video card drivers.
I have an X1950XT with catalyst 8.8 installed. When I got to launch counter-strike, my screen seems to split in two and de-interlace. Here's a picture I found of someone else having the same problem as myself.

[http://img356.imageshack.us/content.php?page=done&l=img356/5511/img00068yk3.jpg](http://img356.imageshack.us/content.php?page=done&l=img356/5511/img00068yk3.jpg) (I'm not useing a Dell monitor, I have an LG F900B. But I don't think it matters.)

Anyways, if anyone knows anything about this or wants me to specify something, I'll be more than glad to explain it a little more in depth.

Thanks.

---

### Post by causeitsme on 2008-09-04
First, check your hardware drivers. (System>Administration>Hardware Drivers)
Make sure you have ATI accelerated drivers checked and In Use

On another point, you don't have compizfusion running do you? I find I have to disable it anytime I want to game.

---

### Post by tracetheace on 2008-09-04
The ATi accelerated driver is checked and in use.
I used to have compiz installed, I also thought that maybe it was the culprit. So I did a full format + reinstall of ubuntu just to make sure.
Didn't seem to change anything.
--------------------------------
Also, as I was setting up ubuntu after the format. 

I tested counter-strike with no default drivers. (first boot drivers) 
Result -> counter-strike would run, no artifacts of any kind, but with VERY poor FPS.

Then I enabled the accelerated driver, without installing the ATi. I'm guessing by doing that it uses the xorg open sauce driver?
Result -> counter-strike would run with good fps, but the screen would flicker as I played showing the counter-strike main bg.

Then I installed the ATi 8.8 drivers, perhaps my method of installation wasn't correct? 
Method-> DL'ed the .run from ati site. 
right clicked on the ATi8-8driver.run and checked the 'allow executing as program' in the permissions tab.
Launched Terminal and logged in using 'sudo -s'
Dragged the ATi8-8driver.run into the terminal instead of typing it's path. Install seemed to proceed without any problems.
Result -> What you see in the picture from my fist post.

Hope that clears things up a little.

Also I can fix the screen by simply loggin out and back in again.

---

### Post by causeitsme on 2008-09-05
> **tracetheace said:**
> The ATi accelerated driver is checked and in use.
I used to have compiz installed, I also thought that maybe it was the culprit. So I did a full format + reinstall of ubuntu just to make sure.
Didn't seem to change anything.
--------------------------------
Also, as I was setting up ubuntu after the format. 

I tested counter-strike with no default drivers. (first boot drivers) 
Result -> counter-strike would run, no artifacts of any kind, but with VERY poor FPS.

Then I enabled the accelerated driver, without installing the ATi. I'm guessing by doing that it uses the xorg open sauce driver?
Result -> counter-strike would run with good fps, but the screen would flicker as I played showing the counter-strike main bg.

Then I installed the ATi 8.8 drivers, perhaps my method of installation wasn't correct? 
Method-> DL'ed the .run from ati site. 
right clicked on the ATi8-8driver.run and checked the 'allow executing as program' in the permissions tab.
Launched Terminal and logged in using 'sudo -s'
Dragged the ATi8-8driver.run into the terminal instead of typing it's path. Install seemed to proceed without any problems.
Result -> What you see in the picture from my fist post.

Hope that clears things up a little.

Also I can fix the screen by simply loggin out and back in again.

Sorry that didn't work out for you. Have you tried aticonfig in terminal?

I don't know if that'll help or not but that's the same as Catalyst Control Center in windows. You may find something in there to help.

Otherwise this is probably over my head and I'll just butt out now as I'm really just a noob.

---

### Post by tracetheace on 2008-09-05
Yeeeee. I took 1 look into there and high tailed it out. Sooo many lines to look through. Very scary for a noob like me.

I dunno, I'm going to keep trying cause I've been wanting to switch for so long. I'm just tired of windows. But even though linux is becoming much more user friendly, it's still difficult for a newb with some knowledge of computers to just jump in and feel at home. Imagine anyones parents, like people that have a hard time with windows....

I'm not giving up yet :D

---

### Post by tracetheace on 2008-09-05
According to this.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

My X1950 Series doesnt have 3D acced support on the radeon driver.
Is this true?

---

### Post by tracetheace on 2008-09-05
Ran into this guys post on a different forum.
theres some tweaking done in post #10.
[http://bbs.archlinux.org/viewtopic.php?id=51577](http://bbs.archlinux.org/viewtopic.php?id=51577)

Can anyone help me with this?

---

### Post by tracetheace on 2008-09-05
formatted and reinstalled.
Using Catalyst 8.4... works fine now.

---

