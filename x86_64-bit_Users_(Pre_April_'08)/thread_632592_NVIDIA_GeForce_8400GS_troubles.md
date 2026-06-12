---
title: "NVIDIA GeForce 8400GS troubles"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by branhow on 2007-12-05
Hey everyone. I am wanting to switch to Ubuntu but my graphics card kept messing up with it.
I have an NVIDIA GeForce 8400GS. I thought this was a pretty common card and thats why I bought
it thinking it would run better under Ubuntu. I'm still using XP unfortunately and I'm just
getting really tired of it. I'm really a newbie with Linux... But I want to learn, any suggestions
on fixing this error? Thanks a bunch guys and gals.

---

### Post by Yellow Pasque on 2007-12-05
Did you try the latest beta drivers?
[http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)

---

### Post by Law506 on 2007-12-05
I had a lot of troubles with 7.04 but with 7.10 the restricted driver provided with the installation solved my video problems.  I still do not have a splash screen though.  My monitor looses signal during the splash screen and then it comes back on at the login.  

Exactly what are the problems?

-Nvidia 8600GTS is what I have.

Oh, and if you are getting into Ubuntu, you dont want to try to use both the restricted driver and the nvidia driver from their website.. causes conflicts that will crash your system.

---

### Post by branhow on 2007-12-05
i can get it to load, but it will only use a very low screen resolution

---

### Post by branhow on 2007-12-05
do u think i would hav a greater chance using the regular x86 kernal?

---

### Post by Law506 on 2007-12-06
Back on 7.04 I didn't have any luck with the 32bit or 64bit.  It might fix your problem, doesn't hurt to try.  Have you tried using envy yet?  Just do a search for it and you should find out somethings.  I used it to get me going when I had troubles.. might be helpful.

---

### Post by branhow on 2007-12-07
ya i tried envy with an older graphics card... but not this newer one

---

### Post by psycho5 on 2007-12-07
You don't need to use envy, it'll mess up your system. The solution is very easy.

First you need to download the appropriate drivers from the nvidia website and disable the restricted drivers if you have enabled them.

Second, you need to stop gdm, hit alt+ctrl+f2 in ubuntu, now you'll be in CLI mode. stop ur gdm. 

 then you need to install your downloaded drivers, then you need to disable the conflicting restricted drivers by editing linux-restricted-modules-common and change Disabled Modules =" " to "nv nvidia_new" 

After that simply restart your gdm

you should be fine.

this is the guide on how to do that: 
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I have an Nvidia 8600GTS and everything works fine, except for the monitor going out of res problem. I also have it, i think it's either conflicting video cards (like with your onboard) or something else, other than that everything's okay.

---

### Post by saru411 on 2007-12-08
> **psycho5 said:**
> You don't need to use envy, it'll mess up your system. 

um how can envy mess up your system? i have a nvidia 8400 in my dell vostros 1500 and envy worked perfectly. envy is the easiest noob script out there. it picks your card, it sets it up, it sets up your xorg. what else do you really need? ive heard that these resticted drivers are now easy to install on gutsy.....but why would i want to upgrade and find out? my system works how i want it to. if you are wondering if envy will work for this card. the clear answer is yes it will!

if for some reason your resolution isnt set correctly after using envy([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) you can type ```
sudo nvidia-settings

``` and set your resolution there. remember to save your xconfig file once you have it the way you want it.

---

### Post by jp_coll2003 on 2007-12-08
i agree with you saru. I was a newbie not so long back and I have a peculiar nvidia card, a 7500LE. I tried everything to get it set up in the right resolution and could not get the right monitor set up either in Ubuntu 7.04 or 7.10 version. With Envy or that was taken care of and everything was up and running beautifully within 15 minutes of first downloading the program. What a wonderful piece of coding that bloke has done. Nothing but praises to it and its coder.

---

### Post by roger99 on 2007-12-08
I can't really recommend Envy, because I have never used it, but a friend that I introduced to Ubuntu used it and it made a mess of his system.  Installing the Nvidia Drivers yourself really isn't a problem when you know how :)

First of all go the Nvidia site and download the latest _BETA_ drivers.  These seem to work a lot better with the 8 series GPU's although they aren't perfect yet.

Now switch to another tty with Ctrl+Alt+F1.

Make sure you have the necessary packages needed to compile the drivers by entering this command

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Now you need to stop the X server and compile and install the Drivers.  First make sure you are in the same directory that you downloaded the drivers to.  Then enter the following commands.

```

sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86_64-169.04-pkg2.run 

```
(hint - hitting tab after typing the NV of the file name should auto-complete for you in case you arn't using 64bit packages)

Then follow the onscreen commands to let the driver compile.  Also let the installer configure the Xorg.conf for you it works ok until you really know your way around the file.......

When the installer finishes and it's dropped you back to the command line enter the following command.

```
sudo /etc/init.d/gdm force-reload
```

This should take you back to GDM, hopefully with fully functioning NVIDIA drivers.  :)

> Originally posted by **Law506**  	
I still do not have a splash screen though. My monitor looses signal during the splash screen and then it comes back on at the login. 

As for the no splash screen problem following these instructions on Launchpad solved it for me ( after many hours of searching and fiddling )

```
[COLOR="Blue"][https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56)[/COLOR]
```

Hope this helps some people..........

---

### Post by guren on 2008-01-05
> **roger99 said:**
> 
As for the no splash screen problem following these instructions on Launchpad solved it for me ( after many hours of searching and fiddling )

```
[COLOR="Blue"][https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56)[/COLOR]
```


I can confirm that this solution solved my problem.
However, in my case I also added **nvidiafb** in /etc/initramfs-tools/modules
I also commented out **blacklist nvidiafb** in /etc/modprobe.d/blacklist-framebuffer
and used **1024x768 16-bit** instead of 1280x1024 16-bit

I am using an Nvidia 8400 GS on a HP dv2500 laptop and it is now working perfectly with the restricted drivers in gutsy.

---

### Post by zoobean on 2008-01-13
I have a dell vostro 1400 with geforce 8400gs.
i have installed envy, installed the driver, but i m still getting a very low resolution.
i am new to ubuntu, plz instruct how i get about the Xorg.conf thing!!!!
any other solution???

---

### Post by guren on 2008-01-13
> **zoobean said:**
> I have a dell vostro 1400 with geforce 8400gs.
i have installed envy, installed the driver, but i m still getting a very low resolution.
i am new to ubuntu, plz instruct how i get about the Xorg.conf thing!!!!
any other solution???

You may want to uninstall envy and use the restricted drivers instead. Your laptop specs maybe a little similar to mine and your Ubuntu splash screen doesn't show up by default. You may want to view the previous posts for the solution.

And the xorg.conf thing, I haven't touched my xorg.conf since I upgraded to Gutsy because everything is working properly just by installing the nvidia restricted drivers and modifying my screen resolution to the right size.

---

### Post by saru411 on 2008-01-14
> **zoobean said:**
> I have a dell vostro 1400 with geforce 8400gs.
i have installed envy, installed the driver, but i m still getting a very low resolution.
i am new to ubuntu, plz instruct how i get about the Xorg.conf thing!!!!
any other solution???

did you run 

```
sudo nvidia-settings
```

in terminal? then set proper resolution and save xorg file?

---

### Post by zoobean on 2008-01-16
\m/
u guys r gr8!!!!
:popcorn:
MOVIES nw!!!!!!!!

---

### Post by darkworld on 2008-03-06
> **saru411 said:**
> did you run 

```
sudo nvidia-settings
```

in terminal? then set proper resolution and save xorg file?

Hi

I have managed to load up the drivers ok, ive sorted the splash boot screen and I have one last problem. I also cant stop the resolution changing back to a lower resolution 1024 X 768  in my desktop after a reboot.

Administration > Screens and Graphics 1280X1024 

then

Sudo nvidia-settings > Xserver display configuration > set the resolution the same 1280x1024 Auto > save to Xconfiguration file.

Desktop in correct resolution. Reboot PC and desktop is back at 1024 X 768. ????

Samsung syncmaster 920N screen recognized correctly too?

Is there a file anywhere in the system that will give me all information on whats going on in my PC with graphics/video? My only concern is that the nvidia onboard graphics that I have is in some way effecting the 8400GS set up. 

I toggled bios to select PCI express 8400GS and disabled restricted drivers, restricted driver window shows disabled but a tick showing a restricted driver is in use, nvidia-settings also allow me to change things. 

Cant work out whats wrong, not an expert

---

### Post by darkworld on 2008-03-06
further to my problem. 

When I log out and log back in as another user the resolution is correct in there desktop, even after a reboot! But not in my desktop, the installation account. Is Ubuntu screwed? [ SOLVED ] Stupid error. Nvidia settings and screen and graphics under admin but also..... resolution under preferences! Doh!

---

### Post by King_Koopa on 2008-03-28
I have been unable to install the Linux drivers for my Nvidia GeForce 8400GS, on my 32-bit Ubuntu installation.

I have downloaded the drivers, extracted the package, executed the installation, but I receive an error telling me that I do not have a card installed in my PC that is compatible with version 169.12 of the Nvidia drivers.

The error makes no sense because those are the drivers that belong my very card, and I had no issue installing the Windows drivers. Has anyone else expereinced this? Is there a solution out there?

---

### Post by JudasReanimated on 2008-04-02
Check your Restricted Drivers, and see if you can install them. Also post you device manager's findings on you Video Card.

---

### Post by jlh68 on 2008-04-04
Try Hardy Heron 8.04 Beta, and it will find the "new" open source nVidia driver. It works well with my PNY GeForce 7300GT graphics card.

---

