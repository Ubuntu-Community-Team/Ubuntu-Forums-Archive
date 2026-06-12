---
title: "Blank Screen After Boot Splash Screen"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Technogenius on 2007-12-03
I am running 7.10 64-bit edition on an AMD Athlon 64 X2 4600+ with 2gb memory and a GeForce 6100 onboard video. After installing with the alternate install CD, everything worked fine and I updated and installed a few programs. On the 3rd boot, the screen just turns blank after the boot splash. I know it's not a hardware problem because the screen's power light stays on. Any help would be greatly appreciated.

---

### Post by Beaucephus on 2007-12-03
I had two problems like this.  The first time was because usplash was not installed. This is what displays the ubuntu logo during bootup.  
The Fix```
sudo apt-get install usplash
```

The second problem was when the drive was being checked for errors, the screen went blank and gave me no indication what it was doing.  Eventually it came back up.  I have not seen a fix yet.

Either of these sound like your problem?

---

### Post by Technogenius on 2007-12-03
I guess it was that the drive was being checked, because it spontaneously fixed itself. Isn't the drive only checked every 30 mounts?

---

### Post by Technogenius on 2007-12-03
Never mind, the problem's back again.

---

### Post by Beaucephus on 2007-12-06
Do you ever see the ubuntu logo with the line showing boot progresst?  Or does it go from the blank screen straight to the login prompt

---

### Post by Leion on 2007-12-18
> **Beaucephus said:**
> Do you ever see the ubuntu logo with the line showing boot progresst?  Or does it go from the blank screen straight to the login prompt

on startup, i see the grub page
then i click on the first option, which is to boot ubuntu
then it says "loading.."
then whole screen blank 
waited a long time before i see the login screen...

---

### Post by Technogenius on 2008-01-17
Mine never got to the login screen. The Ubuntu logo and progress bar flashed for a second, then nothing. I just reinstalled and it works great.

---

### Post by pepolez on 2008-01-22
> **Leion said:**
> on startup, i see the grub page
then i click on the first option, which is to boot ubuntu
then it says "loading.."
then whole screen blank 
waited a long time before i see the login screen...

I've got the same problem here.

---

### Post by KingWilliam on 2008-01-22
try to activate verbose mode. This will give you the output between the moment you leave grub and when you enter the log in screen. You can activate verbose mode in grub. Somewhere in /boot/grub. Altough i cant exactly tell where. 
If you do get output between grub and login somthing is wrong with the thingy that shows the progressbar...

---

### Post by amr952 on 2008-01-22
I am also have the same problem as mentioned above.

I have tried to install usplash and receive the message that I already have the newest version installed. I have not tried verbose mode yet because I have not idea what that is but I am going to try and found out.

After I chose the default Ubuntu in Grub I see the two lines that say the following then everything goes blank.

Kernel alive
kernel direct mapping tables up to blah blah blah

If anyone has any other advice I could really use some.

Thanks in advance.

---

### Post by glennph on 2008-01-22
had a similar problem with a Debian distro on another comp.. 

Changed "splash" to "nosplash" in the kernel line of  /boot/grub/menu.lst

then all was peachy..

---

### Post by amr952 on 2008-01-22
Ok, I fixed my problem. Hopefully it will help someone else out also.

1) After grub loads hit 'e' on default ubuntu
2) Hit 'e' on the kernel line.
3) Remove the word "quiet" and change "splash" to "nosplash"
4) Hit Enter
5) Press 'b'

There is probably a setting in menu.lst that will make this permanant. I will try and figure that out now and post back.

---

### Post by KingWilliam on 2008-01-23
```
sudo gedit /boot/grub/menu.lst
```
Scroll down to Ubuntu and change 'quiet' to 'noquiet'.

When you reboot, I think you get all those things the uSplash hides for you. But I am not sure ;)

grtz

---

### Post by redrovo on 2008-01-23
I am having the same problems with my AMD Turion 64 laptop. The LiveCD worked great, but then after installing, the same Black Screen desricbed. Thanks for all your guys help. I'm going to try and implement the above suggestions, and let you know.

---

### Post by redrovo on 2008-01-23
> **amr952 said:**
> Ok, I fixed my problem. Hopefully it will help someone else out also.

1) After grub loads hit 'e' on default ubuntu
2) Hit 'e' on the kernel line.
3) Remove the word "quiet" and change "splash" to "nosplash"
4) Hit Enter
5) Press 'b'

There is probably a setting in menu.lst that will make this permanant. I will try and figure that out now and post back.

These steps solved my problem. Now, I just need to make it a permanent change or get the splash screen loaded properly. 

 Thank You again!

---

### Post by roofninja on 2008-01-24
To KingWilliam:

Thanks for the help.  This is my first time in the 64bit world.  So, how bad are my noobie cloths looking like?  For a time, I thought that it was a bad video card, so now, one down and many more left.

---

