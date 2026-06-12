---
title: "Want to put Mac to Sleep Mac style"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by burobaaje on 2005-12-23
anyone been sucessful in getting a mac to sleep mac style in ubuntu?

---

### Post by Rxke on 2005-12-24
You mean a portable? (iBook Powebook) or a desktop?

My iBook goes to sleep and wakes up no problems, even stays logged in w/ Gmailnotifier, something that doesn't work with OSX...

---

### Post by burobaaje on 2005-12-24
sorry, forgot about iBook sleeping when closed..

iMac Flat Panel - sleeps when sleep command is given from apple menu.

my install of ubuntu blacks the screen after some time, but i want the hd to spin down when not used for long periods..i use sleep for this under OSX

---

### Post by Rxke on 2005-12-24
in the terminal, to test it out:

```
sudo hdparm -S 2 /dev/hda
```

should spin it down after 10 secs of inactivity....

(it is in blocks of 5 secs, so 1= s secs, 2= 10 etc... 

if that doesn't work, you also do  

```
sudo hdparm -B 2 /dev/hda
```

that's setting the Advanced Power Management setting (1-255) 1 being most agressive, so it'll try to spin down whenever it can, 255 is no spindown...

If it still spins up, (probably) you'll have to add ```
sudo laptop-mode start
```, probably first installing laptop-mode via synaptic... then look at the laptopmode-files that set up things...

and put it all either in a startup-script, or via the menu system/preferences/sessions and there enter those in 'programs at startup... There's a howto somewhere how to do that with root permissions (because 'sudo' will cause your computer to ask you for your password otherwise during startup...)

Since I very seldomly reboot my computer, i just enter the three... every time after a reboot... (too lazy to figure out how to script it, heh)

---

### Post by burobaaje on 2005-12-26
[QUOTE=Rxke]in the terminal, to test it out:

```
sudo hdparm -S 2 /dev/hda
```

should spin it down after 10 secs of inactivity....

(it is in blocks of 5 secs, so 1= s secs, 2= 10 etc... 

if that doesn't work, you also do  

```
sudo hdparm -B 2 /dev/hda
```

that's setting the Advanced Power Management setting (1-255) 1 being most agressive, so it'll try to spin down whenever it can, 255 is no spindown...

If it still spins up, (probably) you'll have to add ```
sudo laptop-mode start
```, probably first installing laptop-mode via synaptic... then look at the laptopmode-files that set up things...

and put it all either in a startup-script, or via the menu system/preferences/sessions and there enter those in 'programs at startup... There's a howto somewhere how to do that with root permissions (because 'sudo' will cause your computer to ask you for your password otherwise during startup...)

Since I very seldomly reboot my computer, i just enter the three... every time after a reboot... (too lazy to figure out how to script it, heh)[/QUOTE]



I installed laptop-mode and tried all 3 commands.  No spin down.  This is an iMac 17" flat panel.  There is a possiblity that the first thing that needs to happen is to detect a laptop for laptop-mode to work.  Are you using a laptop or some other mac?  I was able to confirm that laptop-mode had started by neither of the 2 commands would spin down the hard drive.  I could also stop laptop-mode, but I got an error message each time saying that "unary operator expected".  Don't know if the error had any effect of not since it reported that laptop-mode had started or stopped.

Will keep searching.  Can't stand for drive to run when I am not using the system!

---

### Post by spencer on 2006-01-24
I have Breezy on Powerbook Pismo and with os x laptop sleeps after some time without closing the lid. I would like for Ubuntu to sleep laptop without closing lid when I'm not using computer; Ubuntu only darkens screen and doesn't put laptop to sleep after some time. 

I can put laptop to sleep by closing the lid or selecting it from the logout menu which gives the option to suspend computer. However, that's not what I want. I also installed laptop-mode and that wouldn't put computer to sleep either. 

Will Ubuntu put to sleep Powerbook Pismo the os x way? 

Any help is much appreciated.

-spencer

---

### Post by sulobanks on 2006-01-25
Spencer-

Install powerprefs from synaptic or apt.  Then run it and adjust your settings accordingly.

Or you can open /etc/pbbuttonsd.conf and change the following:

onAC_TimerAction = suspend-to-ram
onAC_SuspendTime = <number of seconds of inactivity before suspending>
onBattery_TimerAction = suspend-to-ram
onBattery_SuspendTime = <number of seconds again>

Not sure if a Pismo uses suspend-to-ram or suspend-to-disk, but since one of them is already working, look at what onBattery_CoverAction is set to and use that for onAC_TimerAction and onBattery_TimerAction.

---

### Post by spencer on 2006-01-25
Installed Powerprefs and set ''timer action" option set to ''suspend to ram''; worked perfectly!. Thanks! :D

-spencer

---

