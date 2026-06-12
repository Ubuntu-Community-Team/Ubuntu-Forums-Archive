---
title: "black screen after resume from suspend 9.04"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by ubuntubrian on 2009-04-28
Toshiba Satellite laptop
Ubuntu 9.04
I have checked this problem and found that there are any number of issues with Jaunty not properly resuming from sleep. I just upgraded from Intrepid where sleep and resume worked almost perfectly. Now in Jaunty I can suspend but when resuming I can see the laptop wakes but there is no screen-just black. I have edited /etc/default/acpi-support any number of ways that I have found posted to no avail.
If I run the command:
echo -n mem > /sys/power/state
The laptop suspends and will resume but without trackpad, keyboard or mouse (usb) and I have to reboot.
demsg shows no problems at all, just a successful suspend. No resume messages however.

Anyone getting this to work?

Thanks!!

---

### Post by ubuntubrian on 2009-04-28
I found a workaround by installing the "uswsusp" package which contains the s2ram app. I found out about this at  [http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box](http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box)

and after installing it I can suspend with ```
s2ram -f
``` and resume by touching the power button. The only thing is that I wish I resumed to a password screen instead of the session I was in when I suspended the box. Maybe there's a way yet......

---

### Post by jonoinsa on 2009-05-11
I have the same problem with my Toshiba Tecra P5, suspend/hibernate used to work 100% in 8.10. In 9.04 I can hibernate but not suspend, but found that I can suspend after i've hibernated once? How weird is this?

Bothers met when I do an "upgrade" and there's a whole heap of stuff broken, and i've also had several "freezes" over the last 2 weeks with 9.04 installed, 8.10 no freezes.....

---

### Post by ubuntubrian on 2009-05-11
Yeah, it is a pain. I'm still using the command above but would like the system option to work...
Maybe in an update some day.

---

### Post by Eppux on 2009-05-11
Got a MSI VR601 and got exactly the same problem. I'll just won't suspend it, till an update comes out :P

---

### Post by pixel :-) on 2009-05-11
> **ubuntubrian said:**
> I found a workaround by installing the "uswsusp" package which contains the s2ram app. I found out about this at  [http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box](http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box)

and after installing it I can suspend with ```
s2ram -f
``` and resume by touching the power button. The only thing is that I wish I resumed to a password screen instead of the session I was in when I suspended the box. Maybe there's a way yet......

You can script that, no? And set it up as a button on the panel or menu?

---

### Post by jayanramesh on 2009-05-11
"Suspend"is not working properly in jaunty-same prob. I have.

---

### Post by ubuntubrian on 2009-05-11
I did set up the sleep as a buton. Resuming to a password screen is beyond me.....

---

### Post by pixel :-) on 2009-05-11
after a quick search

xscreensaver-command -lock

It works? i don't want to install it



Oh great, i tested s2ram -f and its the same, black screen at wake up. So people be carefull

---

### Post by colnizster on 2009-05-13
hey i have a satellite l305 and was experiencing the exact same problems. i solved it with this - 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/336158]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/336158")

scroll to the last post on the page. it worked for me! i just sucessfully suspended twice in a row with no glitches. let me know if it works for you.

---

### Post by DiodePorridge51b on 2009-07-06
Hello

I followed the instructions on the link provided by colnizster above and it worked for me (altering the model number because I have a Satellite L300). Thanks!

One caveat - you have to make sure you specify the new "quirks" towards the end of the Satellite section in the .fdi file and not the beginning otherwise it will be overwritten by other quirks (I suspect, in particular, for the L30).

This page was useful for debugging the process:
[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-try.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-try.html)

Peace

---

### Post by ubuntubrian on 2009-07-07
The fix worked perfectly on my L305 just as posted.

---

