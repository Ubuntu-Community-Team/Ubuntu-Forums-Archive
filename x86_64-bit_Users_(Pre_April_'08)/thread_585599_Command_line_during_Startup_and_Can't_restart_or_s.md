---
title: "Command line during Startup and Can't restart or shutdown!"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by monstar on 2007-10-21
I'm relatively new to Linux...

Been reading nonstop howtos and what not to try and get my system up.
Worked through slow boot up and getting BCM43xx to work on my Acer in Gusty...

Anyways the problem I face now is...

**During bootup**

It starts going through the boot up
ex. Loading blahblah blah [OK]
it gets about half way through and there some talk about Mounting the Swap...

It says 
Checking minimum space in /temp
bash : no job control in this shell

-AND THEN-I get the command line, the only way to get it to continue booting up is by typing _exit_

It continues wit the Loading blahblahblah [OK]

**During shutdown or restart**
It goes toe the black screen with the red text..
Restarting system or System is shutting down, but it stays on that screen.

If I push Ctrl+Alt+F2 i think it was? One of the F# buttons, it brings me to a black screen with Command line again..

THE ONLY WAY to shut down/restart is typing exit again.

Does anyone know what might be going on?
I tried searching for this, but the shutdown/restart probs don't seem to be related to this..


Thanks in advance...
Oh I am running Gusty AMD64....
Don't really know what other info you guys may need

---

### Post by John.Michael.Kane on 2007-10-21
Well first off the standard Ubuntu install should have installed gnome+gdm. 

Second: what method did you use to fix your slow boot up and getting BCM43xx to work on your Acer in Gusty, and did these methods require you modify system files.

Third: before you used whatever methods to get the above issues "fixed" did the machine boot normally? If so then your issues are with the methods you employed.

Also what version of Gutsy have you installed. f.e:Gnome Kubuntu Xubuntu or was this a command line install or server install? 

Last was this a clean install or a upgrade from another Ubuntu version?

---

### Post by monstar on 2007-10-21
Second: what method did you use to fix your slow boot up and getting BCM43xx to work on your Acer in Gusty, and did these methods require you modify system files.

-To fix the slow boot up i removed Splash/Quiet from the menu.lst
It booted up fine for awhile so I don't think taht was it..

As for the BCM43xx..there was one forum that links to a setup involving Acer_Acpi..if you do a search for the words "ACERHK" it will bring up the method I used...

Here is the link
[http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595](http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595)
--------------------------

If anything, this bootup/shut down problem only seemed to surface sometime after getting my wireless to work..

Sorry..The Gusty install was off the Live-CD, I am sure it is a regular Ubuntu install..

It is a clean install, but dual boot off a new partition with Winxp

Hope that helps you a bit..Im going to look through the acerhk link a bit..though like I said..it is my 4th day with linux...Hopefully something stands out to me

---

### Post by monstar on 2007-10-21
It usually seems to happen around the bootup / shutdown lines near

Swap files or Mounting drives..

I don't know what it could be though...went through the Wireless install stuff and nothing seems like it could be potentially affecting this, but..what would I know? :confused:

---

### Post by monstar on 2007-10-22
I've got some RTC error now and it doesn't boot at all...
Safeboot doesnt work either...nothing works...:popcorn:

---

### Post by John.Michael.Kane on 2007-10-22
> **monstar said:**
> I've got some RTC error now and it doesn't boot at all...
Safeboot doesnt work either...nothing works...:popcorn:

IMHO starting over again might be best, This time make sure to keep a notepad handy keeping track of what you are doing before rebooting.noting what effects the guides you use have on your install. 

Also I would not use that guide or any other guide without giving the maker of that guide your complete system specs,and asking if it would work. As some guides may not be compatible with your hardware or the version of Ubuntu you are using.

---

### Post by monstar on 2007-10-24
I ended up reinstalling, it fixed the RTC but still had the commandline shutdown boot problem..
So I installed PCLinuxOS but didn't like it and went back to Ubuntu and the errors are gone..
Still no working wireless now though but...I have a hunch that might be what screwed it up...hard to say...
Kinda iffy on doing anything I'm not sure about..

One thing I did notice was that my computer ran at 100% alot though...opening 2-3 tabs in Firefox and my fan was blowing HARD and it was running at full speed

---

