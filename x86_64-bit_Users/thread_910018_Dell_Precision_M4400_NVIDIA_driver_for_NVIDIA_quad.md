---
title: "Dell Precision M4400: NVIDIA driver for NVIDIA quadro FX770"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by TheDreamingMind on 2008-09-04
dear all,

I have just finished the installation of ubuntu 64 bit on a Dell Precision M4400.

almsot everything works. almost.
I miss the graphc card, which is a NVIDIA quadro FX770.
the system uses vesa driver. ho provato ad installare i driver nvidia-glx and  nvidia-glx-new, but still it seems it is not working.

I have also tried the graphic interface with 
system/administrator/hardware driver 

but no driver is suggested.

what am i doing wrong?

grazie

---

### Post by yds753 on 2008-09-07
I am planning to buy a laptop with a similar graphic card,
so I'd like to know if this problem has already been solved ?

---

### Post by testuser222 on 2008-10-03
I got the NVIDIA card working (after some problems) using envy. Sound does not work yet. The Intel WiFi 5300 AGN had to be compiled and I am not sure if it is 100% stable.

---

### Post by testuser222 on 2008-10-03
To be more precise: sound works, but kmix doesn't work

---

### Post by yds753 on 2008-10-05
> **testuser222 said:**
> I got the NVIDIA card working (after some problems) using envy. Sound does not work yet. The Intel WiFi 5300 AGN had to be compiled and I am not sure if it is 100% stable.

Could you tell me how you've installed the NVIDIA card, because even with the official drivers installed it still doesn't work here.

---

### Post by testuser222 on 2008-10-06
As I am not very organized and I tried a lot of stuff, I cannot give you an exact description.
 
 Try:
 
 
 - install envyng-gtk
 
 - you should have a working internet connection
 
 - then start envyng or envyng-gtk (text or graphically)
 
 - follow the instructions
 
 - I chose the driver with the highest version number (unfortunately I forgot the number), because I thought this must be the most recent one
 
 I think that was it, but I am not sure...
 
 Good luck

---

### Post by spajix on 2008-10-14
> **testuser222 said:**
> As I am not very organized and I tried a lot of stuff, I cannot give you an exact description.
 
 Try:
 
 
 - install envyng-gtk
 
 - you should have a working internet connection
 
 - then start envyng or envyng-gtk (text or graphically)
 
 - follow the instructions
 
 - I chose the driver with the highest version number (unfortunately I forgot the number), because I thought this must be the most recent one
 
 I think that was it, but I am not sure...
 
 Good luck
Thanks for saying how you did that it Helped me to get my M4400 working right as well

---

### Post by biofisikx on 2008-10-28
since nvyng didn't work for me (I have a quadro fx 770m), I had to do it the "hard" way (this should work for any flavor of ubuntu, or linux for that matter):

- Go to NVIDIA Download page at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

- Select the right video card. In my case:
     Product Type: Quadro
     Product Series: Quadro FX Series Mobile
     Product: Quadro FX 1500M (Don't worry, is the same driver for 770m)
     Download Type: Quadro Graphics Driver
     Op. System: Linux 32bit (OR 64bit, depending on your system)
     
-Click on "Search". This will take you to another page with a link and instructions on how to install the driver.
-Download the file NVIDIA-Linux-x86-177.80-pkg1.run (or whatever the name is)
-Log out from your session (it wont work if X is running). At the login screen choose to open a console (command line window) and login.
-Go wherever you saved the downloaded file.
-Type "chmod u+x NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type "sudo sh NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type your password
-Follow instructions. The installer might have to compile something (don't worry, you wont have to do anything, just accept when asked).
-Let the installer configure X for you (it will save a backup of whatever is there)
-When the installer finishes, restart and you're done! you should see
the NVIDIA splash screen!

---

### Post by Amorget on 2008-10-28
> **biofisikx said:**
> since nvyng didn't work for me (I have a quadro fx 770m), I had to do it the "hard" way (this should work for any flavor of ubuntu, or linux for that matter):

- Go to NVIDIA Download page at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

- Select the right video card. In my case:
     Product Type: Quadro
     Product Series: Quadro FX Series Mobile
     Product: Quadro FX 1500M (Don't worry, is the same driver for 770m)
     Download Type: Quadro Graphics Driver
     Op. System: Linux 32bit
     
-Click on "Search". This will take you to another page with a link and instructions on how to install the driver.
-Download the file NVIDIA-Linux-x86-177.80-pkg1.run (or whatever the name is)
-Log out from your session (it wont work if X is running). At the login screen choose to open a console (command line window) and login.
-Go wherever you saved the downloaded file.
-Type "chmod u+x NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type "sudo sh NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type your password
-Follow instructions. The installer might have to compile something (don't worry, you wont have to do anything, just accept when asked).
-Let the installer configure X for you (it will save a backup of whatever is there)
-When the installer finishes, restart and you're done! you should see
the NVIDIA splash screen!

One correction on that... you need to DL the 64 bit drivers, being he is running Ubuntu x64

---

### Post by biofisikx on 2008-10-29
Correct, just pick the right parameters for your system and everything should be fine.

---

### Post by sea-geek on 2008-10-29
> **biofisikx said:**
> since nvyng didn't work for me (I have a quadro fx 770m), I had to do it the "hard" way (this should work for any flavor of ubuntu, or linux for that matter):

- Go to NVIDIA Download page at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

- Select the right video card. In my case:
     Product Type: Quadro
     Product Series: Quadro FX Series Mobile
     Product: Quadro FX 1500M (Don't worry, is the same driver for 770m)
     Download Type: Quadro Graphics Driver
     Op. System: Linux 32bit (OR 64bit, depending on your system)
     
-Click on "Search". This will take you to another page with a link and instructions on how to install the driver.
-Download the file NVIDIA-Linux-x86-177.80-pkg1.run (or whatever the name is)
-Log out from your session (it wont work if X is running). At the login screen choose to open a console (command line window) and login.
-Go wherever you saved the downloaded file.
-Type "chmod u+x NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type "sudo sh NVIDIA-Linux-x86-177.80-pkg1.run" (without ")
-Type your password
-Follow instructions. The installer might have to compile something (don't worry, you wont have to do anything, just accept when asked).
-Let the installer configure X for you (it will save a backup of whatever is there)
-When the installer finishes, restart and you're done! you should see
the NVIDIA splash screen!

I did all of the above but did not see the NVIDIA splash screen.
I am a new user of Ubunutu. This is my second install in 2 days. Yesterday I installed on a Dell Mobile Workstation M2400 and all went amazingly well.
Today I'm trying it on my Dell Mobile workstation M4400 and found this post to help me with the video driver. I haven't installed much that wasn't on the CD and came with the updates.
First I had trouble figuring out how to stop X so I could do the install. I did not see a 'console' option on the login page but I found this to stop X: sudo /etc/init.d/gdm stop
Then I did <ctl>-<alt>-<F1> and got a login prompt and ran the remaining commands there.
The first time I ran the command to install the driver I got an error message saying I didn't have some C libraries. Yesterday I was able to compile 'xv' using some great instructions I found and in there was a command to get C libraries like this:
apt-get install libc6-dev
So I did that on this machine and reran the install command. I let it do what it wanted to do. Eventually it said it was done and I rebooted as instructed but when I did I was told I was in 'low resolution mode' and would have to configure X myself.
I'm not sure how to do this but may be able to find a way by searching but before I go off on a wild goose chase, is there any way to figure out why I didn't get the same results as the poster of these instructions?
Oh, I apologize if I'm posting in the wrong area. I'm using a 32 bit machine not 64 bit. But this thread was the only place I found to deal with this particular graphics issue

---

### Post by BuissonVert on 2008-10-29
Quadro FX770M use driver 177.80, so it should be fine using EnvyNG on Ubuntu 8.10 (the 8.04 version of EnvyNG still installs the 173.xx.xx drivers that won't work for your GPU). Just wait for tomorrow and you'll be happy ;)

---

### Post by undoIT on 2009-03-04
Does hibernate and suspend work after installing the Nvidia driver?

---

### Post by iKevin09 on 2009-08-03
I just opened Terminal and entered in "sudo apt-get install nvidia-glx-96." Then once that was downloaded and installed, I went to System>Administration>Hardware Drivers where it listed Nvidia drivers. I chose the recommended 180 driver pack. It said that it needed a reboot for the changes to go into effect, so I did. Now I'm running Ubuntu in my laptop's native 1920x1200 resolution.. Oh-so-pretty.

---

