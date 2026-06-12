---
title: "[SOLVED] Video Playback Messed up after New VIdeo Card Install.  LOOK"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-12-14
My video playback is all messed up now after switching from an ATI card to an nVidia 7900 GTO card.

Have a look.  Any Ideas how to fix this?

---

### Post by cotcot on 2007-12-14
I have had the same problem except that the green in your case was pink in my case. After reboot it was gone.

---

### Post by crjackson on 2007-12-14
> **cotcot said:**
> I have had the same problem except that the green in your case was pink in my case. After reboot it was gone.

Not working for me.  I've rebooted several times.  Thanks for the reply though.

---

### Post by Cappy on 2007-12-14
Run
```

sudo nvidia-settings
```

goto "OpenGL Settings" on the left bar. Uncheck "Sync to VBlank".

Restart X (Alt+Control+Backspace) and see if video works now.

If it still isn't working reopen
```

sudo nvidia-settings
```
goto "X Server XVideo Settings" on the left and uncheck "Sync to VBlank".

Restart X (Alt+Control+Backspace) and see if video works now.

If all this fails do the same thing but check the boxes.

I don't remember if you are supposed to uncheck or check the boxes =( On my 7900GT I have the OpenGL Settings VBlank unchecked and the X Server XVideo Settings VBlank checked.

---

### Post by crjackson on 2007-12-14
> **Cappy said:**
> Run
```

sudo nvidia-settings
```

goto "OpenGL Settings" on the left bar. Uncheck "Sync to VBlank".

Restart X (Alt+Control+Backspace) and see if video works now.

If it still isn't working reopen
```

sudo nvidia-settings
```
goto "X Server XVideo Settings" on the left and uncheck "Sync to VBlank".

Restart X (Alt+Control+Backspace) and see if video works now.

If all this fails do the same thing but check the boxes.

I don't remember if you are supposed to uncheck or check the boxes =( On my 7900GT I have the OpenGL Settings VBlank unchecked and the X Server XVideo Settings VBlank checked.

Glad you chimed in Cappy.  It seems you and Kilz are the ones who always have the answers I need.  I'm at work now, but I'll do this as soon as I get home.  I can't believe how much faster this card is compared to my x800.

---

### Post by backhoff on 2007-12-15
similar issue here.. i leave you another threat with more screenshots.. the difference is that in my case it occurs when i use wine, for example CS: source

---

### Post by backhoff on 2007-12-15
[http://ubuntuforums.org/showthread.php?p=3955212](http://ubuntuforums.org/showthread.php?p=3955212)

---

### Post by crjackson on 2007-12-15
> **crjackson said:**
> Glad you chimed in Cappy.  It seems you and Kilz are the ones who always have the answers I need.  I'm at work now, but I'll do this as soon as I get home.  I can't believe how much faster this card is compared to my x800.

I didn't make any changes Cappy.  My settings already match yours...

---

### Post by crjackson on 2007-12-15
Okay, I have found that I can get it working with CTRL+ALT+BACKSPACE.  If I turn OFF desktop effects, the problem is back.  I then C+A+B and it fixes it now.  If I turn ON desktop effects the problem comes back again, and CAB fixes this too.

Since I've been playing with desktop effects a lot, I guess this has been my problem.  Now, I just wonder how long it will work correctly if I make NO more changes.  If it continues to work properly, I guess the fix is to ALWAY C+A+B after making changes related to desktop effects.  I could live with that.  Only time will tell...

---

### Post by Mochino on 2007-12-15
Mhh, those screens are familiar to me, sometimes there's something already rendering in 3d, for example amarok's plugins, and that causes the videoplayback to be green, after i close the 3d rendering plugin, and re-launch, totem or vlc, everything is fine.

Maybe this might be slighty related?

---

### Post by crjackson on 2007-12-16
> **Mochino said:**
> Mhh, those screens are familiar to me, sometimes there's something already rendering in 3d, for example amarok's plugins, and that causes the videoplayback to be green, after i close the 3d rendering plugin, and re-launch, totem or vlc, everything is fine.

Maybe this might be slighty related?

could be I don't know.  In my case it only happens when making adjustments to desktop effects.  I have to CAB after making the change and it works fine after that from what I've seen so far.

I'm out of town for the weekend but when I get back home, I'll search launchpad and see if a bug report has been made.  If not, then I'll file one.

If anyone knows how to change the resolution of the login screen, please jump in and tell.  It's one of my last glitches I need to fix.

---

### Post by backhoff on 2007-12-16
i have this problem with 3d rendering too.. for example counter strike or google earth. and yes, CAB works but i'm not fully happy with that.

---

### Post by crjackson on 2007-12-17
> **backhoff said:**
> i have this problem with 3d rendering too.. for example counter strike or google earth. and yes, CAB works but i'm not fully happy with that.

I'm not fully happy with that either, but I know of no other working solution, or even what the problem is.

---

### Post by crjackson on 2007-12-17
[Bug #177029]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/177029")

---

### Post by bazzbc on 2007-12-17
Same problem here. What I did was uninstall the Nvidia drivers and downloaded the previous version (64-100.14.09) from the Nvidia website.

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

Once you have them put them in your home directory kill your x session and  sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run

I'm pretty far from an expert on these matters but it was a relatively painless operation for me and I have had perfect video playback since.

---

### Post by williammanda on 2007-12-17
You all may be have the same problem as I did and others. I unistalled the Nvidia driver and installed the latest Nvidia beta driver 169.04.  I used this link as a guide then installed the beta driver.
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)


NVidia 169.04 drivers links.
======================
i386: [http://www.nvidia.com/object/linux_d...32_169.04.html](http://www.nvidia.com/object/linux_d...32_169.04.html)
x64 : [http://www.nvidia.com/object/linux_d...64_169.04.html](http://www.nvidia.com/object/linux_d...64_169.04.html)

Hope this helps.
Thanks

---

### Post by crjackson on 2007-12-17
Alrighty Then, I'll give that a try.  Do I need to disable the current restricted driver first (I presume this is HOW I would un-install the current driver), OR do I smiply install the driver OVER the old one?

Please give me a
1)
2)
3)

so that I don't screw it up.

Thanks...

---

### Post by crjackson on 2007-12-17
> **bazzbc said:**
> Same problem here. What I did was uninstall the Nvidia drivers and downloaded the previous version (64-100.14.09) from the Nvidia website.

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

Once you have them put them in your home directory kill your x session and  sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run

I'm pretty far from an expert on these matters but it was a relatively painless operation for me and I have had perfect video playback since.

How exactly does one Kill the X session?

---

### Post by bazzbc on 2007-12-18
Sorry not sure if all my terminology was correct.


1. Use the restricted drivers menu to disable the previously installed version first  (As far as I remember the nvidia setup handled the actual uninstall)

2. Open a terminal and type sudo /etc/init.d/gdm stop all              (This stops all the graphical stuff and leaves you with a basic terminal interface.)

3. Run the  sudo sh ....whatever.run  command to install the drivers.             (These should be in your home folder. If you cant remember the full file name type ls)

 
I tried both the new beta and the older version, both solved the video playback issue but I had issues setting up dual monitors with my Geforce 7600 LE using the beta drivers. With only one monitor connected I didn't encounter any issues.

Hope this helps

---

### Post by crjackson on 2007-12-18
Yes this helps. Thanks for the information.  I work on this in a day or so...

---

### Post by crjackson on 2007-12-19
Before I got a chance to try any of the solutions offered here, I got a reply on my bug report with an updated kernel.  I have EVERYTHIG enabled in my repo sources specifiacally backports/proposed gutsy upgrades.

I don't know if the kernel release came though the regular channels or if it came from on of the repos above, but it fixed the issue on my system.

---

### Post by chikin03 on 2008-02-14
I have only tried it once, but it worked immediately: I switched to a terminal, (Ctrl+Alt+F1), logged in, logged out, switched out (Ctrl+Alt+F7) and then it worked. 

I had the pink corruption, and an NVIDIA card.

---

### Post by crjackson on 2008-02-14
I found that one of the kernel updates fixed it for good.  Are you using 7.10?

---

