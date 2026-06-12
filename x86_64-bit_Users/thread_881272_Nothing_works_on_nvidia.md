---
title: "Nothing works on nvidia"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by aceole on 2008-08-05
This would be my first time posting so bear with me please.

I have been trying to get this to work for a week now and not a thing has got it.
I downloaded the latest NVIDIA driver and tried to install them, but every time I do and reboot it goes to the "LOW graphics MODE". 

I've done everything that other users have done to get theirs working but to no success. the closes thing I get is when i stopX > "sudo /etc/init.d/gdm stop
and try to run the file
> sudo sh NVIDIA-Linux-x86_blah_blah_blah
I get a "can't open file" error... and everything I've tried has failed.](*,)](*,)](*,)

cd Desktop/NVIDIA_blah_blah_blah.
sudo sh ./NVIDIA_blah_blah_blah.

Can someone please help me before i get a worst taste in my mouth the i do
I have Ubuntu 8.04
The video card is a FX 5200 256mb
I'm waiting to be helped...
Thankyou in advance:)

ALSO:
the graphics are stuck in low mode BUT if I remove all NVIDIA software the graphics are fine other than no cool 3D effects.
I have done and seen a lot, too much to remember so as i get help I will post my findings.

---

### Post by logos34 on 2008-08-05
don't cd into the file--it's an interactive installer, not a folder

try:

cd Desktop

sudo sh NVIDIA*

Alternatively you could try EnvyNG automatic installer

---

### Post by aceole on 2008-08-05
CD desktop comes up with the same thing...> can't open file

EnvyNG gives me drivers and puts the res at highest 640x480

---

### Post by logos34 on 2008-08-05
> **aceole said:**
> CD desktop comes up with the same thing...

EnvyNG gives me drivers and puts the res at highest 640x480

with the EnvyNG driver installed try 

sudo apt-get install nvidia-settings

gksudo nvidia-settings

set the resolution and refresh there, and save to x config file.  Any luck?

---

### Post by aceole on 2008-08-05
I'm new at the code for lunix. could you type out the code for me as though it was in the terminal sorry...

---

### Post by aceole on 2008-08-05
I'm reinstalling ubuntu due to the fact i've installed so many third party software in the past week, it's crazy. so if you wish to take it from the top you can.

---

### Post by logos34 on 2008-08-05
type this in a terminal:

sudo apt-get install nvidia-settings

gksudo nvidia-settings

---

### Post by aceole on 2008-08-05
I did:
> sudo apt-get install nvidia-settings

Installed

Then:
> gksudo nvidia-settings

It Runs but theirs nothing in the settings to go higher than 640x480

---

### Post by Neo0351 on 2008-08-06
here's how to get the drivers working from nvidia.  
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by darkknight045 on 2008-08-06
If you want to try and automatic installer use

```
sudo apt-get install envyng-gtk
```

Once its installed, tell it to install the nvidia drivers using auto detect.  It'll work its magic and you should be good to go.

---

### Post by aceole on 2008-08-06
USER Neo0351

I went to your link and did the steps.

when i got to 

> sh /location/to/driver

It reads "Can't open File"

---

### Post by aceole on 2008-08-06
User Neo0351

I went to the link, when i got to step...

> sh /location/to/driver

It read "Can't open file.

---

### Post by Neo0351 on 2008-08-06
post ```
uname -a
```

---

### Post by aceole on 2008-08-06
and ENVYNG
loads fine installs fine. but upon restart after just before login menu it says "Can't auto detect do you wish to manuale input your video card and monitor"

---

### Post by aceole on 2008-08-06
> uname -a
Posted
> linux asa-desktop 2.6.24-19-generic #1smp Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by Neo0351 on 2008-08-06
i think you're not getting the the path right to where you're drivers are located.  are you using the tab key to autofill the right path.  like if you downloaded the driver to your desktop, you would type in ```
/home/asa/Desktop/Nvi[tab]
```
and it would fill in the rest of the path

---

### Post by xen-uno on 2008-08-06
If you follow this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

... to the letter, you'll be up and running.

---

### Post by aceole on 2008-08-06
OK you were right I did not have proper path. this did the trick!
> /home/asa/Desktop/Nvi[tab]
and I was able to install it...HOWEVER!!!](*,)
when I reloaded X it was still in 640x480. upon restarting it said again. "Low graph mode" auto video card driver and monitor not found do you wise to select them from our list.
when I have nothing changes.

---

### Post by Neo0351 on 2008-08-06
> **xen-uno said:**
> If you follow this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

... to the letter, you'll be up and running.

this is much more detailed than mine, i like
aceole, the thread xen-uno should have you up and running.  i think you are still getting conflicting Nvidia drivers.

---

### Post by aceole on 2008-08-06
I did as this on said [http://ubuntuforums.org/showpost.php...71&postcount=6](http://ubuntuforums.org/showpost.php...71&postcount=6)
and it installed. at the part for ENVY ng it said not installed, but it's in my system tools folder.
upon running the X-server again I tried Desktop effects and it said "could not be enabled" I restarted and tried again, but same thing.
I can only go max 800x600 also.

---

### Post by Neo0351 on 2008-08-06
it might be easier to try a fresh install again and follow the last thread again

---

### Post by aceole on 2008-08-06
I'll try! nothing to lose! keep posting please I have a feeling it won't make a difference :(

---

### Post by xen-uno on 2008-08-06
Some people have had the rez problem with monitors that Ubuntu can't correctly identify (ie Samsung Synchmaster). It has something to do with an incorrect modeline in xorg.conf. How they corrected it, I don't know offhand.

You might find something here ...

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by aceole on 2008-08-06
after a fresh install and running through the steps again, when i started the X my screen went to "Out Of Range" Mode. and I had to remove the steps i did just to start it again.

---

### Post by aceole on 2008-08-06
> **aceole said:**
> after a fresh install and running through the steps again, when i started the X my screen went to "Out Of Range" Mode. and I had to remove the steps i did just to start it again.
and now that I removed the driver on startup it's again in low graph mode.

---

### Post by aceole on 2008-08-07
HI people!
I reinstalled again and put a HD monitor on here updated and everything. when I rebooted I got the low graph mode again and now my HD monitor is at 800x600 71hrz.
This is starting to really piss me off...
I ran System tools) NVIDIA x Server Settings) 
It told me > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
So i opened a terminal and put the code (nvidia-xconfig) That said
> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

is there nothing I can do to get this right???

---

### Post by aceole on 2008-08-07
HI people!
I reinstalled again and put a HD monitor on here updated and everything. when I rebooted I got the low graph mode again and now my HD monitor is at 800x600 71hrz.
This is starting to really piss me off...
I ran System tools) NVIDIA x Server Settings) 
It told me 
So i opened a terminal and put the code (nvidia-xconfig) That said

is there nothing I can do to get this right???
another thing, when i run
> sudo dpkg-reconfigure xserver-xorg
it has about 6 questions on keyboard configuring but nothing on Video...???...
and at startup, my screen flashes code that reads in 5 or 6 lines, one says
> check battery state                 [OK]
it goes fast so i can't read it all, I have to restart and try and read them one at a time.
when I change settings in Screen and Graphics the new settings don't stay. they always go back to low graph mode.

---

### Post by aceole on 2008-08-07
:(Has my help come to an end:(

---

### Post by aceole on 2008-08-07
:(Has my help come to an end:(
Well I broke down and reinstalled XP. and i'm pissed that this has not been fixed, what am i supposed to do?
anyway I have ubuntu on a dual boot so if someone wants to have a stab at how to fix it PLEASE!!! I WANT TO GET THIS WORKING. WINBLOWS and I hate eachother.:confused:

---

### Post by aceole on 2008-08-07
> **aceole said:**
> :(Has my help come to an end:(
Well I broke down and reinstalled XP. and i'm pissed that this has not been fixed, what am i supposed to do?
anyway I have ubuntu on a dual boot so if someone wants to have a stab at how to fix it PLEASE!!! I WANT TO GET THIS WORKING. WINBLOWS and I hate eachother.:confused:
Well I had one more go at it and it's working. I'm using the restricted drivers and it's working. 3d and all. thanks for putting up with me yall.

---

### Post by xen-uno on 2008-08-07
Good deal ace.

---

### Post by punkybouy on 2008-08-08
For what is worth, what kind of video card do you have and how much memory is on it?
I run several Nvidia cards from several manufacturers and all are detected and run just fine on Ubuntu. I a currently running several 7300GTs with 256 MB video RAM.

---

### Post by aceole on 2008-08-08
Nvidia fx 5200

---

### Post by Anlace on 2008-08-09
Greetings,

I was having this same kind of problem too and what I found was corrupted EDID info from the monitor.

I explained it here:

[SOLVED] Low Resolution Issues Solved
[http://ubuntuforums.org/showthread.php?t=884211](http://ubuntuforums.org/showthread.php?t=884211)

and made something of a HowTo here:

Nvidia just won't work! Why, why, why?!
[http://ubuntuforums.org/showthread.php?t=883938](http://ubuntuforums.org/showthread.php?t=883938)

I sincerely hope this helps, I spent more than a year trying to find the answer and finally did with this.  Now I'm on a mission to assist others :)

---

