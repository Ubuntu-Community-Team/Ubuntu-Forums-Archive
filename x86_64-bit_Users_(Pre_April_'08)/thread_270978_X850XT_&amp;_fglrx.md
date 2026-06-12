---
title: "X850XT &amp; fglrx"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by locque on 2006-10-04
Ok... So I've searched and searched for the answer to my problem but I still haven't found it. I've tried some of the other suggestions about commented out certain drivers and adding different options in the xorg.conf but they haven't fixed my problem... So here it is

I have Xorg running fine @ 1920X1200 with fglrx. Everything is fine except when I try to logout, restart Xorg <CTRL-ALT-BACKSPACE>, or change to a terminal with <CTRL-ALT-F#>. When I do these, the screen goes black and my monitor goes into standby because it is not getting any signal. The only way to get out of this is to hit the RESET button. 

I have tried the ATI drivers and I get the same result. Using 'ati' as the driver fixes this problem, but then I am only getting 640x480... The Xorg.log doesn't show anything neither does dmesg...I'm lost and frustrated. Like I said, it boots up fine and Xorg works just fine as long as I don't try to go to console mode or restart it. 

Here are my specs:
              AMD64 4000+
              1GB Memory
              ATI X850XT Platinum Edition

Any help PLEASE!!!

---

### Post by kuja on 2006-10-04
I think you might need a newer version of the FGLRX driver if there is one available. My little brothers computer, formerly my own, has an ATI Radeon 9700 card, and uses the FGLRX driver too. It experiences the same problems you're describing, you know, the hanging. A shame ATI doesn't provide solid graphic drivers for Linux, but oh well, seems the only company who does is Nvidia for now anyway.

---

### Post by xstaticxgpx on 2006-10-04
all i do to install the drivers is follow [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=204910") and just replace the filenames with whatever version you downloaded from the ati website.

---

### Post by locque on 2006-10-04
I appreciate the suggestions and help, however I am still stuck. I tried the 8.27.x driver from the ATI website and got even worse results. I could hear the drums and what not, but I had nothing on the screen. So I went back to the latest driver 8.29.6 and am back up and running, however I'm still having the same problems...

Could it be related to being connected via DVI?

fglrx seems to be working fine:

fdoug@Demonius:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT Platinum Edition Generic
OpenGL version string: 2.0.6065 (8.29.6)

and X starts ok, it's just that I can't leave the current resolution (1920x1200) without it freaking out and locking up. I get nothing from the logs so they are of no help...I'm lost. It's like it doesn't want to change video modes or it tries and then forgets to send the signal via DVI??? 

Very strange

---

### Post by locque on 2006-10-25
I have followed the tutorial with installing the fglrx driver. I have done it a couple of times because I am known for getting ahead of myself and skipping some important detail :mrgreen: . I am still having the same problem. Let me restate my problem so that I make sure it is clear:

Computer starts X just fine.
fglrxinfo shows: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT Platinum Edition Generic
OpenGL version string: 2.0.6065 (8.29.6)

However, if I hit CTRL-ALT-BACKSPACE to restart the X-server, it hangs and my monitor goes blank with the orange light coming on (as if there is no video coming from the computer). Switching to a console mode does the same thing. Even trying to restart the computer using the standard GNOME logout procedures hangs up as well. I have to manually restart it (RESET button) to get anything out of it...

Any ideas?? I have been chasing this thing around and have still not found the solution. If you need more information to help, please let me know....

---

### Post by ginyip on 2006-10-25
> **xstaticxgpx said:**
> all i do to install the drivers is follow [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=204910") and just replace the filenames with whatever version you downloaded from the ati website.

Actually, if you follow the quote tutorial and you are using X1600 pro 512mb agp card AND using 64 bit Ubuntu Dapper. I am sure (for sure I cannot) this doesn't work. After following the tutorial, what i got is same as the poster. ALSO, when >fglrxinfo , I got an info out with a X1600 card but.....computer crashed after info printed.

For myself, I have already applied the tutorial with 8.29 installer.

---

### Post by pony-tail on 2006-10-25
There is a bug with "edgy" and fglrx I have already posted elswhere here but here is a link.
Link: [https://launchpad.net/distros/ubuntu....17/+bug/57716](https://launchpad.net/distros/ubuntu....17/+bug/57716)

---

### Post by locque on 2006-12-05
I stumbled across a solution to this issue. I don't know how it works or why, but it does ( at least it worked for me ). 

 Remove any installed fglrx drivers

 Reconfigure Xserver using : sudo dpkg-reconfigure xserver-xorg

 Configure Xserver to use ati driver (this allowed my X to start albeit only in 640x480 mode)

 In KDE: K-Menu -> System Settings -> Display

 Enter 'Administrator Mode'

 Goto HARDWARE tab

 Click 'configure' by the graphics card

 Scroll Down to ATI and open that tree
 
 Find 'ATI Radeon (fglrx)'

 Apply settings and restart X

Worked for me!!!

---

### Post by Chenzo on 2006-12-06
I have been having this exact same problem with X800. 

I have tried updating fglrx several times.  I am running Edgy, and everything else works fine. fglrxinfo returns:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)

I have searched forums and this is the only one with the same problem description, but I am not running KDE so I can not try this solution. Any other ideas??

---

### Post by Chenzo on 2006-12-06
Update:  All issues are resolved when I use VGA instead of DVI.  With DVI, even on 'sudo reboot -h now' the whole computer freezes and will not reboot.  With VGA, I can reboot, logout, switch users; everything. I would still like to fix this issue as I would like to use DVI.  Any ideas on what would cause this?

---

### Post by RAOF on 2006-12-06
> **Chenzo said:**
> Update:  All issues are resolved when I use VGA instead of DVI.  With DVI, even on 'sudo reboot -h now' the whole computer freezes and will not reboot.  With VGA, I can reboot, logout, switch users; everything. I would still like to fix this issue as I would like to use DVI.  Any ideas on what would cause this?

ATI drivers being crap?  Not very helpful, I know :(.

---

