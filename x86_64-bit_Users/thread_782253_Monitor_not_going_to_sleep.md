---
title: "Monitor not going to sleep"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by hvacr on 2008-05-04
I am running Hardy 64. I cannot get my display to go to sleep after ten minutes. No matter what I set the slider to in the power management section, the display never goes to sleep. Has anyone else ran into this.

This is a desktop system with an ATI graphics card. In gutsy, you could never seem to stop the display from sleeping.

---

### Post by hvacr on 2008-05-06
No one else but me having this problem?

---

### Post by Ryuki_NdranC on 2008-05-10
i have the exact same opposite, i can't stop my screen from sleeping, even if i set it up with NEVER sleep.

So far i have reed, people like better kpowersaving then gnome default.

---

### Post by mojportal on 2008-05-10
My monitor go sleep after 10 minutes. That cannot turn off. When looking dvd after 10 minutes monitor go off, just can to hear sound. Must shake mouse and then monitor go on. Power save is both on never. How turn monitor always on?

---

### Post by maestrobwh1 on 2008-05-11
I added to this post... 
[http://ubuntuforums.org/showthread.php?t=682715&highlight=display+power+management](http://ubuntuforums.org/showthread.php?t=682715&highlight=display+power+management)
but it is a similar issue in kde4

it it not solved though, but perhaps it is related.  Oddly, it happened on my asus eee-pc with gutsy and my desktop with hardy... both after a recent update/upgrade (I have the ppa for gutsy installed so perhaps there are some packages similar to hardy in it?).  On my eeepc with gutsy, I also have kde3 and the monitor still shuts off when I set it to.

I am thinking there is a bug with the display power manager and perhaps it is affecting gnome and kde4 if that is possible... is anyone else having the issue and what are you running as your desktop manager?  If your monitor is blanking but not sleeping?

I have kpowersave installed and it has no effect on the display power in kde4.  I also have the box checked in systemsettings under --> display --> power for kde4 and it seemingly has no effect.  I even logged in as "root" and waited the alloted time for what I set it at and alas, the monitor blanked, but I could see the backlight.  On the external monitor, the power light does not blink so yet another indicator that it is not powered down.

---

### Post by Yellow Pasque on 2008-05-11
See if your screen is being controlled through DPMS and see this link for an example of to configure /etc/X11/xorg.conf (open the file with *gksudo gedit /etc/X11/xorg.conf*)
[http://www.barriebremner.com/geek/xfreedpms.cgi](http://www.barriebremner.com/geek/xfreedpms.cgi)

---

### Post by maestrobwh1 on 2008-05-12
Yes, that was the first thing I did... I opened xorg.conf to see if it was "new" after the upgrade.  It wasn't.  Option "DPMS" is there.  It is also an artefact of kde4 and not kde3 on the same system.  I may consider looking at the other lines that were in the post you listed.

---

### Post by generic_idea_machine on 2008-05-14
Couldn't find anything in the settings/configs that could lead to a fix

A stepper motor, set to go off every 9 mins (to move the mouse) might help in such a sceanario ;)

---

### Post by C. Wizard on 2008-05-14
> **hvacr said:**
> I am running Hardy 64. I cannot get my display to go to sleep after ten minutes. No matter what I set the slider to in the power management section, the display never goes to sleep. Has anyone else ran into this.

This is a desktop system with an ATI graphics card. In gutsy, you could never seem to stop the display from sleeping.

I'm using an ATi card and KDE with Kubuntu 8.04 and have a similar problem.  Sometimes it goes off, as it is set to do, and sometimes not.  
I've noticed a pattern. If I install "upgradeable files" using the Adept Manager, the screen saver never works until after the system has been rebooted, but then, that doesn't always work either.  Regardless, you shouldn't have to reboot a Linux system every time you "upgrade" files.

For a while "shutdown," "restart," Log out," etc. didn't work. All I got was a black screen. Then one morning recently, after running the Adept Manager, installing files, that from their names appeared to have nothing to do with xorg or kde, that ability came back to life. Well, almost. If you tell it to shutdown it goes through the motions, but never actually powers off the machine.
There is a bug somewhere. Hopefully the developers will find it in the near future.

---

### Post by efplaya on 2009-02-23
I have an nvidia card and my monitor stops going to sleep after some time and nothing that i do can get it to go back to sleep after a certain amount of idle time, it is really annoying

---

### Post by SpEcIeS on 2009-04-17
Add another system to the list. My display will NOT go into sleep mode. This system is also using an ATI graphics card, Radeon HD 3450.

---

### Post by koolobus on 2009-04-29
> **hvacr said:**
> I am running Hardy 64. I cannot get my display to go to sleep after ten minutes. No matter what I set the slider to in the power management section, the display never goes to sleep. Has anyone else ran into this.

This is a desktop system with an ATI graphics card. In gutsy, you could never seem to stop the display from sleeping.

Exact same problem with kubuntu 9.04.
It still not working as nessesary.

ATI HD 3850

---

### Post by jac0b on 2009-05-01
I am having this same problem. It used to go to sleep in 8.10 but now it just has a box saying "no signal" when it is supposed to be asleep.
Graphics Card: Nvidia 7300LE
Monitor: Envision 19"

---

### Post by the_maassk on 2009-05-04
My Dell laptop has the same problem (nVidia graphics). Checked the xorg.conf but the monitor section lists my external LCD and not the inbuilt laptop screen.

For now I am doing this:

I have created a shortcut on the panel which runs the following command - 'xset dpms force off'

Whenever I am moving away from my laptop, I just click the shortcut.

---

