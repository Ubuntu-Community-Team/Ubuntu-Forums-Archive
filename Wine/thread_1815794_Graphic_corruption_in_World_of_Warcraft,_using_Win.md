---
title: "Graphic corruption in World of Warcraft, using Wine"
date: 2011-07-31
forum: Wine
---

### Post by xhepera on 2011-07-31
I am experiencing corruption of graphics in the game that has made it unplayable. The game loads and the login screen fine. The enter realm screen seems to be fine as well. But once I am actually in the game I'm experiencing overlaid text, distorted images, odd, jagged streaks of color (almost like light refracted through a prism), and grainy graphics that appear as the the images are being viewed through nubbled glass. This will also occur if I choose the "options" button from the login screen. The cinematic graphics play without a hitch. The problems happen whether I am using openGL or not.

This started, best I can tell, after I inadvertently updated from wine 1.2 to 1.3. However, I don't know for certain that Wine is the problem. I removed 1.3 and reinstalled 1.2. The only effect this appears to have had is that at first a bit of corruption (in the form of a white dot of light with another "ray" of light coming from it) was on the login screen. That's now gone, but the rest of the problems remain. I should add that I've been playing for close to a year now with no issues.

My specs are as follows: 
The machine is an HP laptop (8510p)
CPU: Intel Core2 Duo T7300 2 GHz
2 GB RAM
Ubuntu 10.04 lucid
linux 2.6.32-33
ATI Radeon HD2600
I am using the proprietary drivers.

I'd appreciate any help or pointers to resolve this.
Thanks!

---

### Post by Tweak42 on 2011-08-01
Usually when what was working suddenly starts having graphical problems it's either caused by a new wine version or new graphics drivers.  For Wow it can also be from a major patch, but if it worked from 4.0+ that shouldn't be the case.  If you haven't already, try rolling back your graphics drivers one release or two.

---

### Post by xhepera on 2011-08-02
> **Tweak42 said:**
> Usually when what was working suddenly starts having graphical problems it's either caused by a new wine version or new graphics drivers.  For Wow it can also be from a major patch, but if it worked from 4.0+ that shouldn't be the case.  If you haven't already, try rolling back your graphics drivers one release or two.

Thanks for the reply. I checked and I've actually not updated the drivers since June of last year. I'm using ver. 10.8. Might it be possible that I need to update to a current version?

---

### Post by Tweak42 on 2011-08-02
> **xhepera said:**
> Thanks for the reply. I checked and I've actually not updated the drivers since June of last year. I'm using ver. 10.8. Might it be possible that I need to update to a current version?

Definitely look into upgrading the video drivers.  AMD has been pretty active in developing them and much can happen in a year.  Another thought occurred to me, a kernel update might also have tripped off the corruption problems.

---

### Post by xhepera on 2011-08-02
> **Tweak42 said:**
> Definitely look into upgrading the video drivers.  AMD has been pretty active in developing them and much can happen in a year.  Another thought occurred to me, a kernel update might also have tripped off the corruption problems.

Again, thanks for the advice!

I'm going to have to mark this as "solved," or at least resolved. I was just about to post when I read your reply. The strangest thing happened. I opened the game to see if I could get a screenshot of the corruption. While I was on the login screen I did a prt sc keypress, then decided (for reasons unknown, even to me *g*) to click the "Manage Account" button. The graphic issues stopped at once. I've entered and left the game twice now and all seems fine. I've been struggling with this for a couple of weeks and I have no explanation as to how or why it fixed itself. 

If it happens again, you've given me some things to consider. Thanks much!

---

