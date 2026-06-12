---
title: "LDraw - LEGO Cad software"
date: 2008-05-14
forum: Wine
---

### Post by linmix on 2008-05-14
I have tried installing the LDraw package, a LEGO CAD software applications package. MLCad (CAD design program) works flawlessly, but LDView (CAD renderer) doesn't start.

In an effort to solve the problem on my own I found information regarding the  [PreloaderPageZeroProblem]("http://wiki.winehq.org/PreloaderPageZeroProblem") but changing 
> vm.mmap_min_addr = 65536

to
> vm.mmap_min_addr = 0

hasn't had any effect. As a matter of fact, this is what I get when I query wine about the version.> $ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.59


The ful output when I try to run LDview from the console is:
> $ wine "C:\LDraw\Apps\LDView\LDView.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x16 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x32 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x16 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x32 @0! (XRandR)



---

### Post by cogadh on 2008-05-14
You need to restart the PC for that change to take affect, if you made the change permanent by editing the sysctl.conf file. If you used the "sudo sysctl -w vm.mmap_min_addr=0" command, the change is instant, but it resets itself when you reboot.

The other part of the error indicates that the application is trying to adjust your desktop resolution to a setting that is not available in your xorg.conf (480X360). Try enabling Wine's "virtual desktop" in winecfg, it may allow the app to launch in a 480X360 Wine window.

---

### Post by linmix on 2008-05-14
Thank you for your response.

After reboot the first error has indeed disappeared. Shouldn't restarting wine have had the same effect?

As for the second problem, I have enabled "Emulate Vistual Desktop" in winecfg and set it to 480x360, but that doesn't solve anything: worse, it makes working with the other CAD application a nightmare since I can only use a tiny part of my display.

I'm a bit weary of changing my xorg.conf to include 480X360 untill anyone can tell me if that would do any good.

---

### Post by cogadh on 2008-05-14
That settings change is not a change to Wine, but rather a change to your entire system settings. That's why a system reboot was required.

Don't set the virtual desktop to the size that the app requires, just set it to the default or larger and it will resize itself as required. However, now that you have set it that small, you are going to have problems changing it back, since the virtual desktop window you set is too small to allow you the necessary access to the winecfg's functions. You are going to need to manually edit one of Wine's registry files to correct it. Open the ~/.wine/user.reg file with your favorite text editor (not OpenOffice) and scroll all the way to the bottom until you see an entry that looks something like this:
```
[Software\\Wine\\X11 Driver] 1208032951
"Desktop"="480x360"
```
Change the "480X360" to "800X600" or higher, then save the file. The next time you run Wine, it should be a bit more manageable.

---

### Post by linmix on 2008-05-14
You read my mind!! Thanks for a solution before I could even start to look for one. :)

I now get a 'virtual desktop windows' but the application still doesn't launch. 

Output now is:
> ~$ wine "C:\LDraw\Apps\LDView\LDView.exe"
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 320x240x16 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x16 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 320x240x32 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x32 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 320x240x16 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x16 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 320x240x32 @0! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 480x360x32 @0! (desktop)


---

### Post by cogadh on 2008-05-14
I'm really not sure why it is still telling you that... very odd. I probably should have checked into this right off the bat, but the app you are trying to launch, LDView, has a linux native version that might be easier to deal with:
[http://ldview.sourceforge.net/Downloads.html](http://ldview.sourceforge.net/Downloads.html)

---

### Post by linmix on 2008-05-14
D'oh! Thanks!!
Unfortunately that still doesn't get me very far, but at least it's no longer a wine problem, so I'll look for another subforum to post my question(s).

---

### Post by dryan775 on 2008-11-16
> **linmix said:**
> I have tried installing the LDraw package, a LEGO CAD software applications package. MLCad (CAD design program) works flawlessly, but LDView (CAD renderer) doesn't start.

Any tips for a newbie who wants to install MLcad on Ubuntu (I've been using it for about a year on XP, love the software, hate that OS, only been on 7.1 for about 6 months now, but loving it!).

It look straightforward enough, but I've never done anything with wine.

DRyan

---

### Post by tbrminsanity on 2009-07-07
If your having trouble with WINE and getting MLDraw working I suggest using PlayOnLinux ( [http://www.playonlinux.com/](http://www.playonlinux.com/) ).  I have a better track record with it then WINE by itself.

On a side note is there a .deb of LDraw?  The Debian package I tried to install coughed smoke.

---

