---
title: "How to install Nvidia Drivers on ubuntu 64"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by asvestomix on 2009-06-15
hello,

i am just starting to use  Ubuntu 
i just download the right driver file from nvidia site but i dont know how to install it

---

### Post by Arup on 2009-06-15
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Follow instructions to the last point. Make sure to remove linux resitricted moudles and linux restricted modules common with total uninsall checked in Synaptic. After that do a sudo apt-get install build-essential

Then do a ctrl+alt+F1 and login to the tty, after that do a sudo /etc/init.d/gdm stop

Then do a sudo .sh NVIDIAxxxxx and hit enter, make sure nvidia driver is in the home folder.

Select yes for all the option and when done type sudo reboot, your system will then boot with nvidia installed.

---

### Post by cph05a on 2009-06-15
You can get linux 32bit and 64bit drivers from nVidia here:
[http://www.nvidia.com/page/drivers.html](http://www.nvidia.com/page/drivers.html)

This is where I got the drivers for my nVidia GeForce and I haven't had any problems with it.

to install these, log in from a tty terminal (ctrl + alt + F1) and run
```

sudo /etc/init.d/gdm stop

```

then run the tool as
```

sudo ./nvidainstallerfilehere

```

once the installer finished, restart gdm
```

sudo /etc/init.d/gdm restart

```

then log out of tty and log into gdm (it should pop up automatically)

---

### Post by izizzle on 2009-06-15
Why not just use the restricted Nvidia drivers?

---

### Post by tommah04 on 2009-06-15
System>Administrator>Hardware Drivers
 
that'd be the easiest way  (I think its Admin, not at my comp)
 
but if that doesn't work, yea, look into other ways

---

### Post by cph05a on 2009-06-15
> 
Why not just use the restricted Nvidia drivers? 


If they work for you, go for it. I had issues with mine.

---

### Post by Arup on 2009-06-15
The ones in repo are old and the newer ones bring in many more features, stability and performance so its always a good idea to install from the manufacturer's site.

---

### Post by asvestomix on 2009-06-15
hello guys..
i am totalled confused right now
since i dont have any experience in ubuntu interface
well my driver is saved at the desktop i tryed to do as cph05a says and it says not found or something like that
 i would like to play games so i need the latest driver for nvidia gtx 280 64bit ...
when you say i must remove the restricted drivers pls tell me how to do it
to move the driver file to home directory i should copy it and pase it in the folder "asvestomix" (this is my user) ??

---

### Post by nikgare on 2009-06-15
Install the drivers that are automatically provided for you by Ubuntu.
Please go to **System->Hardware Drivers** and then activate the recommended Nvidia driver.
This will then download the driver (it takes a while!) and after areboot it should be working.
Which graphic card do you have?

---

### Post by asvestomix on 2009-06-15
> **nikgare said:**
> Install the drivers that are automatically provided for you by Ubuntu.
Please go to **System->Hardware Drivers** and then activate the recommended Nvidia driver.
This will then download the driver (it takes a while!) and after areboot it should be working.
Which graphic card do you have?

I already instal them with the way you told me but it install an older version 180..
my vga is gtx 280

---

### Post by cph05a on 2009-06-15
hey, I'm sorry if my response earlier was a little vague (I posted rather hastily). Here is a link which is a little more specific:

[http://ubuntuforums.org/showthread.php?t=1030962](http://ubuntuforums.org/showthread.php?t=1030962)

right after you log into tty, use
```

cd Desktop

```

This will move you to the directory you saved your installer in.

---

### Post by asvestomix on 2009-06-15
when i type ch Desktop
it says "-bash: ch: command not found " :s

---

### Post by cph05a on 2009-06-15
lol sorry, I'm not sure where my head is today

ch should be cd

cd Desktop

---

### Post by asvestomix on 2009-06-15
lol i knew the cd command but i thought it was somthing more advanced haha
btw it works!!
but after the install i get a messeget ubuntu running in low-graphics mode
i reset my pc and when it boot i get a messege 

"ubuntu running in low-graphics mode
the following error was encounted. you may need to update your conficuration to solve this
 (EE) NVIDIA(0): Failed to initialize the nvidia kernel module. Please see the (ee) Nvidia(0): system's kernel log for additional error messages and (EE) NVIDIA(0): conslut the Nvidia readme for details.
(ee) nvidia(0) : *** aborting ***
(EE) screen(s) font, but none have a usable configuration.

---

### Post by cph05a on 2009-06-15
That sometimes happens if you haven't logged out of tty1. Make sure you logged out. Once you restart GDM, the login screen will pop up, just press CTRL + ALT + F1 again and type ```
exit
```

then press CTRL + ALT + F7 and log into GDM.

---

### Post by asvestomix on 2009-06-15
i try the whole thing fro the start..
after i type "sudo /etc/init.d/gdm restart"
the messege apears "failed to initialize the nvidia kernel..."
Sorry my friend if i am getting tedious

---

### Post by cph05a on 2009-06-15
When you run the nvidia tool are you asked whether you want to download or compile something? If so which one did you chose?

---

### Post by asvestomix on 2009-06-15
when i was set up it ask me to compile the kernel or somthing like that i say yes

---

### Post by cph05a on 2009-06-15
Here is a page I found on nVidia's website that might help:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/README/chapter-04.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/README/chapter-04.html)

Btw, I've never tried downloading the precompiled kernel, I've always had it compile me a new one.
Which nVidia card do you have?

---

### Post by asvestomix on 2009-06-15
i think i did a big crap..
is there any way to uninstall all and try it again or i must try to format again with ubundu

---

### Post by nikgare on 2009-06-15
The OP has no experience iusing Ubuntu - how can you possible suggest that he attempts the feet of installing the nvidia drivers he obtained from their website over the simple method of letting his system do it for him

---

### Post by cph05a on 2009-06-15
formatting is a last resort, you don't have to do that unless you really want to. You can use the --uninstall option to uninstall the driver, but you shouldn't need to to reinstall. 


> 
The OP has no experience iusing Ubuntu - how can you possible suggest that he attempts the feet of installing the nvidia drivers he obtained from their website over the simple method of letting his system do it for him


It's really not that big of a feat and if you give up, you can still log into ubuntu in low graphics mode if you want to use the restricted drivers.

---

### Post by asvestomix on 2009-06-15
i have gtx 280

---

### Post by asvestomix on 2009-06-15
i am not give up 
:P

---

### Post by cph05a on 2009-06-15
Here is another on the gtx 280:

[http://ubuntuforums.org/showthread.php?t=914654](http://ubuntuforums.org/showthread.php?t=914654)

---

### Post by asvestomix on 2009-06-15
oh dude i made it
thnx you so much
my next target is to set up wine and try a game

---

### Post by cph05a on 2009-06-15
no problem. Good luck with wine it's pretty finicky.

---

### Post by Anubis on 2009-06-15
Threads like these are so sad, and so plentiful.:(:-&#-o](*,)

All this kid had to do, was take a moment to READ or GOOGLE this topic. All the information out there and people still are too lazy to just read it. Then we have people who recommend things that new users should not be attempting. Especially new users with an aversion to reading directions, searching the forums, and or googling.

---

### Post by headsmash on 2009-06-15
> **cph05a said:**
> You can get linux 32bit and 64bit drivers from nVidia here:
[http://www.nvidia.com/page/drivers.html](http://www.nvidia.com/page/drivers.html)

This is where I got the drivers for my nVidia GeForce and I haven't had any problems with it.

to install these, log in from a tty terminal (ctrl + alt + F1) and run
```

sudo /etc/init.d/gdm stop

```then run the tool as
```

sudo ./nvidainstallerfilehere

```once the installer finished, restart gdm
```

sudo /etc/init.d/gdm restart

```then log out of tty and log into gdm (it should pop up automatically)


This worked for me as of 20 minutes ago with 3 Nvidia 9500s

---

### Post by asvestomix on 2009-06-15
> **Anubis said:**
> Threads like these are so sad, and so plentiful.:(:-&#-o](*,)

All this kid had to do, was take a moment to READ or GOOGLE this topic. All the information out there and people still are too lazy to just read it. Then we have people who recommend things that new users should not be attempting. Especially new users with an aversion to reading directions, searching the forums, and or googling.

I dont usualy  ask things in forums ..
but just today i install linux..
ok we did some **** things in the school but just basic commands
so i needed some one to explain me how it works

---

### Post by cachcoco on 2009-07-10
I'd just like to thank the helpers in the Ubuntu community. I've really appreciated your posts as they have made my jump from Windblows to GNU/Linux much easier and much more comforting. To the elitest jerks who scoff at those offering assistance and shun the ones seeking guidance remember: you too were once taught how to walk.

---

### Post by philip5 on 2009-07-11
I have (among a bunch of other updated packages) the latest 185.18.14 version (for the moment) of the nvidia driver as packages in my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try and don't want to mess around installing development packages, fiddling with Xorg shutdown and compiling.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

### Post by philinux on 2009-07-11
Theres is a caveat to the manual install.

Every time there is a kernel update these manually installed drivers will have to be reinstalled.

---

