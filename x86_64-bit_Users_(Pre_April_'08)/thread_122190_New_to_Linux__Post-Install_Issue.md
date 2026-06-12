---
title: "New to Linux / Post-Install Issue"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ToiletDuckie on 2006-01-26
Yea, I'm completely clueless when it comes to Linux. An Operating systems class I'm enrolled in wants me to install it though, so I asked around and a few people mentioned Ubuntu.

I've got an Athlon 64 3700+, 7800GT, 2gb RAM.. I guess those are the relevant statistics.

So, I get Ubuntu "For AMD64" and whatnot, burn the CD, and proceed to install it. The installation was smoothe... even smoother than Windows. Besides a little confusion on the networking adapter ( I had forgotton which of my two was connected to the cable modem instead of another comp) and a tiny issue with the re-partitioning (once again, easily fixed), everything went fine.

Eventually, I rebooted, and a screen comes up asking what video modes I wish to use/not use. 640x480, 800x600, and 1024x768 were all X'd, with the others blank... I wanted 1280x1024 (LCD monitor), but the first time around I "goofed" and forgot to select it.

At any rate, I finally get to the login screen, which looks perfectly normal/functional.. neat even. Type in my name and pass... it switches to a brown screen, I assume it's loading... then.... nothing. Just a ugly white "splotch" in the center of my screen. The mouse cursor still looks/moves fine. I try clicking all over the screen, presssing keys.. Nothing.

I was annoyed, so I reformatted the partition/reinstalled Ubuntu, this time making sure to check 1280x1024 while I was at it. Same issue. Everything looks normal on the login, but after that it goes to poo. I also noticed that clicking on "reset" on the login menu brings up a functional window.. except it has signs of graphics corruption around the edges (little black lines/rainbow colored things). On the other hand, clicking "Sessions" brings up a large, white, corrupted looking box and locks me out... clicking anywhere/typing does nothing.

So, any suggestions? I kinda need Linux in order to do the work the course requires, but I'm at a loss here..

---

### Post by siucdude on 2006-01-26
its kinda hard to tell what it could be can you tell us about the graphic card on your system

---

### Post by ToiletDuckie on 2006-01-26
As mentioned in the second line of the post, a 7800 GT... err, more specifically, an EVGA Nvidia 7800GT CO edition, I think model number 517-AX or somesuch.

---

### Post by mettallicat on 2006-01-26
install the real system and try install nvidia drivers ... after that you should have some time to play with your monitor syncs ... see in manual book or try find the specs on the ethernet.

---

### Post by ToiletDuckie on 2006-01-26
Forgive my newbness, but what is "the real system"?

---

### Post by siucdude on 2006-01-26
ok you need some updates most likely,  at the login screen you need to choose failsafe mode.  then login with your user code.  you will come up to a dos like prompt.  at that prompt type in "sudo synaptic"  password is same as your user pass.  and this is a update utility just type search and nvidia drives.

try this

---

### Post by siucdude on 2006-01-26
oh one more thing while there do a full system upgrade.  also,  clic reload and then once done do a mark all upgrades and then apply,  this should fix some bugs in the system  

good luck

---

### Post by ToiletDuckie on 2006-01-26
Well, that didn't work either. I rebooted / started Ubuntu Recovery Mode... tried "sudo synaptic" and got a "Gtk-WARNING **: failed to initialize window ... or maybe it was graphics..

So, I tried login, my name/pass, then sudo synaptic again... same error.

GtK-WARNING **: failed to initialize (either window or graphics, forgot which).

I'm assuming at this point that it's an issue with my video card.. which is fine I guess. I don't need hardware acceleration or anything, just basic functionality.


Edit: Just to be certain, I booted in default mode, and at the login screen clicked "session". This gave a corrupted, unclickable box.
So, I rebooted and tried Alt-S to get to that box. It comes up, but clicking in it freezes the system, Also, using Alt-_ to select one of the options then Alt-O to confirm locks the system.

So, I can't click session, or choose session with the keyboard, and I can't do the Sudo thing from a command prompt.

I'm stumped.

---

### Post by dickohead on 2006-01-26
When you get to the login screen, don't login, but press: "Ctrl + Alt+ F2" and it will bring you to a command prompt.

Login there and then type:

"sudo apt-get update"
then
"sudo apt-get upgrade"

after that you may want to do this:

"sudo vi /etc/X11/xorg.conf"

and browse to the section about your graphics card, it should say something like:
"driver: nv" or "driver: nvidia"

do a reboot:

"sudo reboot"

and then see what happens.

---

### Post by ToiletDuckie on 2006-01-27
Followed those instructions, got all of the updates, rebooted, same problem.

Checked the conf file, and it says driver: nv and below that lists different "depths" but all show the correct resolutions etc... so I just dunno.

---

### Post by chrisv on 2006-01-27
Maybe there is something else you can try. I am not sure it will work, but give it a try, it fixed my monitor probles (granted my problems were not as serious as yours). 

In that xorg.config file there is an entry called "monitor". In there a lot of info about your monitor is saved. Now, there are two key pieces of info which Ubuntu never gets right for my LCD monitor. I dont quite remember the names for them but thy are vsync and horizrefresh or something like it. 

You have to look at your monitor's documentation or find some descriptions of your monitor on the net which tell you what the real vsync and horizrefresh rates are for your monitor. Then enter those in the xorg.config file and see what happens. 

BTW if there are any Ubuntu developers here, may I respectfully suggest that it is about time Ubuntu starts recognizing Sony LCD monitors.

---

### Post by bonzodog on 2006-01-27
um...just to say, the 7800GT is only supporetd by the very latest nvidia drivers. the ones that come with breezy are an older version. Dapper contains the latest, but it is a devel release and has a tendency to break from time to time. You may need to download the latest drivers from nvidias site, install the kernel headers, then run the nvidia console installer - but this is an 'advanced' thing, and a newbie could get very confused. The best thing I can suggest is switch the the 'driver' line in /etc/X11/xorg.conf so it reads 'vesa' instead of 'nv'. The default nv drivers in ubuntu do not work with the 7800 cards.

---

