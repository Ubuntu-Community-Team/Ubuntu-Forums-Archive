---
title: "DESPERATE! X is DEAD!"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-05-29
I got a notice on the Scribus e-list that there was a new version, 
which included a new repository for .deb files. Thinking that it might
help me get the latest version installed on my Ubuntu-64 Breezy laptop, I
opened Synaptic and tried to add the repository. That didn't work, but in
the process I noticed that there were additional repositories for Ubuntu
Updates and for Security fixes. These repositories had not been enabled. I
wondered why I had not been seeing the little "new updates available" icon
for a long time. So I added them, then updated Synaptic. Following that I
saw the "new updates available" icon. I closed all running programs and
then clicked on it. It listed 230 packages. I decided to go ahead and let
it do the updates. BIG MISTAKE!

Fifteen minutes later it finished. I decided to reboot just to make 
sure everything was cool. Normally when my computer boots it 
lists all the things it is doing, but it does so in "normal" mode or
something. This time it listed everything in like "verbose" mode. Miles of
messages scrolled past. And then, just as I thought it was about to go
graphical, I got a horrible error message: FAILED TO START X WINDOWS
SYSTEM, Unable to locate NVIDIA driver.

I found myself at a command line. No GUI. I had installed the 
Nvidia proprietary driver some time ago, and it had been working 
fine. But I also noticed something in one of the 230 packages 
referring to Nvidia. Undoubtedly that is what caused the current 
problem. I wish there was a "rollback" option to undo the updates. I tried
rebooting one more time, but got the same results.

If I were a command line guru I bet I could fix it. But I know next to
nothing of the command line. Plus I have no idea why the Nvidia driver is
not where it is supposed to be, nor do I even know where it is supposed to
be or what it is called.

Anyone have any ideas where to start? I'm really pretty desperate 
here!

---

### Post by FryerFox on 2006-05-29
You could try to change back to the opensource nvidia driver by changing the lines that read:

```
Section "Device"
        Identifier      "NVIDIA Card" (or whatever it's called)
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
EndSection
```
to:
```
Section "Device"
        Identifier      "NVIDIA Card" (or whatever it's called)
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```

in /etc/X11/xorg.conf:
```
sudo vi /etc/X11/xorg.conf
```

I hope you know how to use vi, but if not, type 'i' to go into insert mode, make your changes and then exit with escape, then x-enter. Or use nano instead:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by FryerFox on 2006-05-29
Oh, and to restart X (with GNOME), type:
```
sudo /etc/init.d/gdm restart
```
Or for KDE, if I remember correctly:
```
sudo /etc/init.d/kdm restart
```

---

### Post by John Jason Jordan on 2006-05-30
[QUOTE=FryerFox]You could try to change back to the opensource nvidia driver by changing the lines...
I hope you know how to use vi, but if not, type 'i' to go into insert mode, make your changes and then exit with escape, then x-enter. Or use nano instead:
```
sudo nano /etc/X11/xorg.conf
```[/QUOTE]
Thanks a million!

Vi did not work. I couldn't figure out how to save the file and exit. But nano worked and had a little panel on the bottom telling me how to save and exit. Once I got the /etc/X11/xorg.conf file edited and saved I just rebooted instead of trying to restart X. And when it finished booting the GUI came back up again! Yay!!!! <Whew>

But while it was booting I noticed a ton of error messages about ndiswrapper. Sure enough, a trip into System > Administration > Networking confirmed that wifi was no longer listed. But this time I knew I was in good shape. I had to go through that the first time I installed Ubuntu, and again when I upgraded to Breezy. By the time I finished fixing it for Breezy I decided that I was never going to have to go through all the hopeless instructions again. Instead I took all the myriad e-mails from kind folks on the Linux R3000 e-list (for owners of Compaq R3000 series laptops), condensed them into a long file, and posted it on their wiki.

This time I just went to the wiki, read the instructions I wrote last November, and in 10 minutes I had it all back functioning as before.

Now all I have left is to get the Nvidia proprietary drivers working again. That's another issue I have bookmarked, so it should be no problem.

Next time I decide I need to apply 230 updates to a system that is functioning perfectly, would someone kindly kick me in the head?

---

### Post by FryerFox on 2006-05-30
[QUOTE=John Jason Jordan]Next time I decide I need to apply 230 updates to a system that is functioning perfectly, would someone kindly kick me in the head?[/QUOTE]

You know you're going to do it again, so here's one in advance: kick! ;)

---

