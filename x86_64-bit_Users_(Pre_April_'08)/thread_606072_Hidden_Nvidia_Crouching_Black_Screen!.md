---
title: "Hidden Nvidia Crouching Black Screen!"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cute Poison on 2007-11-07
Wow, this bug is a nasty one.

Installation of Ubuntu 7.10 64bit edition on a AMD64 3800+ 2.0gb of Ram..... works fine.
this includes the live boot up & first time running / updating all good. 

Then we try to activate the Restricted drivers to get our 256mb Nvidia Geforce 7600 GT.

we have tried the official methods described in the forums...

System reloads, Ubuntu splash screen pops up with the oragnge progreess bar doing the night rider thing.. and then thats it.

fade to black.


It might be worth mentioning that when I tried to install the driver manually it gave me a error stating my kernel did not have support for this card. A failed attempt was made to auto grab the files from Nvidia.. so then it said  it wanted me to compile a new one and again another error came up saying I must install some official "libc" so it can compile one from scratch.. 

since I have only recently come across from windoze I'm dismayed at the issues I'm having trying to install this on my new machine. I have feisty running sweet on a Pentium D, it never gave me grief when I enabled the 128mb 5200 FX. on it.. 
so...
is it the Nvidia Geforce 7600 GT causeing the problem?
is it Ubuntu 7.04 & 7.10 (ive found simular issues on 7.04 forums)? 
is it the actual fact its a AMD 64? 
or it really does work and I have to work a wonderful array of commands into my console..?

---

### Post by dabl on 2007-11-07
Try the Envy script installer.

The web site is here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and you want to download the file "envy_0.9.8-0ubuntu11_all.deb" which is about halfway down that page.  Download it to your desktop, right-click it and "Install with Gdebi".  When it is installed, you can open a console and enter ```
sudo envy -t
``` to run it in text mode.  Choose "Install Nvidia driver" and let it do the work for you.  :)

---

### Post by Jouke74 on 2007-11-07
Loved the title of the topic. :) The video driver and the Xorg.conf are the problem. Envy should be able to help. But the configuration of X may need tweaking anyway.
AMD is working fine (at least my X2 4200 is with an ATI X1600 card).

---

### Post by Cute Poison on 2007-11-09
thanks.. 

Ok. on your advice I went away, got some cans... grabbed my brother and I reinstalled ubuntu once more. determined to show him how cool it all it.

After some effort I managed to download the envy.deb pack (kept giving me internal server errors everytime I clicked on it) and as predictied loads of things happend...

But the end result is the same. 

See,  I can appreciate the fact I need to do some "tweaking".. all for it.  but you cannot tweak what you cannot see. 

So right now.. I have ubuntu sitting on a hard drive updated and using the new compiled drivers installed.(regular turing on will only result in black screen.. (I might like to mention here that the monitor is ok with it.... all the monitors I tested seemed happy with what it was told to display... nothing!) 

How may I gain access to it's little messed up head and make it do my bidding?


I'm like thinking of selling this card and getting a different one!... :lolflag: clearly a issue!.

---

### Post by bonestonne on 2007-11-09
i get a similar action as you, however when i hit a key on the keyboard [not just moving the mouse] i get the login screen....i also have this weird nVidia splash that i haven't seen in previous ubuntu's with the same card.

---

### Post by Dark-Penguin on 2007-11-09
I, too, have an nvidia card...but mine is a Geforce 440 Go. I've been all around the web trying to get compiz to work on this 7.10 Ubuntu.

Should I go back to a previous version of Ubuntu?

I'm a noob to linux but following the printed directions posted by others seem to be easy enough. But they all do not give me the effects I want.

I'm so dissapointed these drivers aren't included in the build. I'm quite sure they have a reason for not including them.

I will try the Envy script and I will let you know what happens....:(

---

### Post by Cute Poison on 2007-11-10
its cool to know I'm not alone... 

Sad to see so many of us suffer the same fate.

Right well, attempt number 5!!!.. I have now re-downloaded me a copy of 7.04 Feisty AMD64 version. and after some chitter chat with a local Linux mate who informs the 7.10 build does not seem to support our graphical card of maddness. 
so Not to be out done.. ( I refuse to slink back to windows with my tail tween z legs.. oh no.. )

Rightio. he also told me of another programe that might do the job similar to ENVY.. called Automatix.  [http://www.getautomatix.com/]("http://www.getautomatix.com/")

So I have reloaded Feisty and before I update anything I going to see if this drivers can be installed Minus the deadly black screen..

EDIT! 30 mins later

GRRRRR!!! stupid video cards!. I swear its out to ruin my life!!!

Ok I installed the new 7.04 version and used Automatix2 (a nifty little program.. does more than video drivers) and yes. same result! black screen o death!. 


So here it is guys. Ubuntu 7.04 / 7.10 work fine. The computer works fine. the software works fine. This video card however does not want to play with all these fine working items... 
Soulutions to how to fix this driver or video card would be welcome.

On a last note. I found pressing "esc" before it loads up ubuntu allows you to enter in the line "automatix-nvidia-restore" saving me hours of updates again.. yay..

---

### Post by Anomali on 2007-11-14
I believe I had the same problem as you.  I considered back-tracking to Feisty since I had no problems there.  Finally I tried 2 things on Gutsy:  Automatix2 (which didn't show me any GFX drivers) and then Envy.

See more details of my **spec and solution** in my response here: [http://ubuntuforums.org/showpost.php?p=3768922&postcount=187](http://ubuntuforums.org/showpost.php?p=3768922&postcount=187)

Hope this is the solution you're looking for,

Ali-]

---

### Post by dabl on 2007-11-14
Maybe some help here (Kubuntu is not different than Ubuntu in this area):

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)


P.S. Automatix will screw with your /etc/APT/source.list file and also with your /etc/fstab file, and not always in a constructive manner.  I stick with Envy for installing the Nvidia driver, and Medibuntu repos for the other non-free stuff like Google Earth and audio/video codecs.  ;-)

---

