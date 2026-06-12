---
title: "how to install mgeops-psp on ubuntu 64 - MGE ups shutdown software"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by PenzoiderS on 2008-11-05
Hi everybody,

If you have an **MGE ups** you may want your server/desktop to shutdown at critical battery situation. I have an MGE Evolution 3000 S and I'm happy with it. But..

If you use ubuntu 32bit there are no problems, but there aren't any 64bit package to install :-k... so here is the trick to get it working: :D

[LIST=1]
[*] install **dependencies** first, in a a terminal:
```
sudo apt-get install libstdc++5 nut
```
[*]download the last stable version of **mgeops-psp 32bit .deb** (mine is mgeops-psp_3.0.6-4_i386.deb) at [http://opensource.mgeops.com/stable/debian/binary/](http://opensource.mgeops.com/stable/debian/binary/)
and open a terminal where you saved it and use this command:
```
sudo dpkg -i --force-all mgeops-psp_3.0.6-4_i386.deb
```
[*]install **getlibs** ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790))
[*]install **missing libraries** using getlibs:
```
sudo getlibs libglibmm-2.4.so.1 libcairomm-1.0.so.1
```
[*]**run it** from "System>Administration>Personal Solution Pac"
[/LIST]

[SIZE="5"]**Enjoy!**[/SIZE]


[I]NOTES:
This works on xubuntu hardy 64 bit using the version 3.0.6 of mgeops-psp.
If you run a different version of mgeops-psp and seems not to work is probably because you miss some libs.. so try to run it in a terminal
```
psp
```
and it will tell you wich lib is missing.. so just tell getlibs to install it:
```
sudo getlibs nameofthemissinglibs
```
It could be also that you miss some dependencies, and you will see them as an error output when you run step 2... just install'em:
```
sudo apt-get install nameofthemissingpackages
```
...and you should be ok![/I]


hope I helped someone! The community always helped me, now it's my turn.:mrgreen:

---

### Post by expelledboy on 2008-11-25
this has been soooo usefull and saved me (I am sure) about 2hrs of hacking!
thank you..

---

### Post by Mouth on 2008-11-25
My MGE ups is installed/attached to my Ubuntu server. Can I install this app onto my laptop and use it to monitor the ups stats? ie. can this software monitor/report on remote ups's?

Thanks.

---

### Post by PenzoiderS on 2008-12-02
Don't know if it can log elsewhere...

2 SIMILAR WORKAROUNDS:

**A-** go with VNC to the desktop of the box that's linked to the ups and look Mge utility in traybar

or

**B- ** go with X over ssh
```
ssh -X youruser@YOU.RSE.RVE.RIP
```
then
```
psp
```


I personally use vnc, but also the othet metod should work


if you want to know about logging ask to the MGE team..

---

### Post by expelledboy on 2008-12-05
I am trying to run this on a server (ie, no gui installed). How do you use this program in the command line?

---

### Post by harfa on 2008-12-05
Well I wish I had found this post before I went through the pain of figuring it all out for myself :) good post though, save others the trouble.
I tried compiling from source on intrepid 64. 
tip for others, it doesnt compile on intrepid 64, I got halfway through hacking past each problem, then gave the package another go, figuring out the above procedure on my own..
guess I should have searched better first :)

the actual program is missing a few features i would like though :(

I don't know how much brains the ups has, but does anyone know how to configure settings to acheive this:

I have my main pc and my wireless router plugged in to the ups, I would like my main pc to begin shutdown within 60 seconds of AC power loss. but I would like the ups to keep supplying power to the router until the battery reaches ~20%

any ideas? i have a MGE nova 600

---

### Post by battersea on 2009-01-08
Nice how-to.

I got everything installed and psp runs, however, it complains there is no display available (it's a headless machine without any X packages installed) and then just dies.

Is there any way to configure this tool from the command line, i.e. without the GUI?

---

### Post by battersea on 2009-01-19
NUT ([http://www.networkupstools.org/](http://www.networkupstools.org/)) is probably a better solution for headless machines. A splendid MGE and NUT How-to can be found at [http://opensource.mgeups.com/howto.htm](http://opensource.mgeups.com/howto.htm).

---

