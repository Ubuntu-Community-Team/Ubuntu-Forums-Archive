---
title: "64bit Install problems with new rig! Please help."
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by FynitE! on 2006-08-20
Hello.

I got my new rig the other day, and today I went to install Ubuntu 64bit on it. First off, my spec:

ASUS M2NPV-VM Socket AM2;
ATI Radeon x800GTO 512mb;
AMD Athlon 64bit X2 Dual Core 4600+;
512mb DDRII (Soon to be 1024mb, they sent me a dodgy stick).

I'm using the free "Version 6.06 LTS for your 64-bit PC" disc that I ordered from the ubuntu website.

When I go to boot into the live CD to install, I get this error:

[http://img134.imageshack.us/img134/8596/3800yq1.jpg](http://img134.imageshack.us/img134/8596/3800yq1.jpg)

[I]"Failed to start the X Server (Your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?

Yes   No"[/I]

After choosing yes, this is what it gives me:

[http://img151.imageshack.us/img151/8038/2800aq2.jpg](http://img151.imageshack.us/img151/8038/2800aq2.jpg)

[http://img150.imageshack.us/img150/8827/1800km5.jpg](http://img150.imageshack.us/img150/8827/1800km5.jpg)

[I]"X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocool Version 11, Revision 0, Release 7.0
Build Operating System: Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux ubuntu 2.6.15-23-amd64-generic #1 SMPPREEMPT Tue May 23 13:45:47 UTC 2006 x86_64
Build Date: 16 March 2006


Module Loader Present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error,(NI) not implemented, (??) unknown).

(==) Log File: "/var/log/Xorg.0.log", Time: Sun Aug 20 11:50:54 2006
(==) Using config file: "/etc/X1//xorg.conf"
(EE) No devices detected.


Fatal Server Error:

no screens found."[/I]

As you can see by the images, the graphics are pretty messed up. Its the same on my friends PC too, spec:

ASUS A8N SLI Premium Socket 939;
AMD Athlon 64bit 4000+ (Skt939) San Diego;
ATI Radeon x800XL 512mb;
1024mb pc4000 DDR 500Mhz


Could this be something to do with the x800? I really have no idea from here, can somebody point me in the right direction?

Thanks. Any help greatly appreciated so I can get off this XP ;)

---

### Post by Ribs on 2006-08-20
I've seen this error before on my system. It's caused by the X server being unable to load a driver for your graphics card. Sadly, I don't know anything about ATI cards, as I'm a nVidia fanboy. So it's difficult to know what to suggest. :-k 

As you can't even boot into the LiveCD, you might want to try one of the other boot options. I believe there are various "safe" options you can use when your computer first reads the disc (I don't have the exact text to hand, sorry). Try those. They may force the LiveCD to start using the "vesa" graphical driver, which should work with all cards.

Failing that, you might want to try the "alternative" cd if you want to install Ubuntu onto your computer and you feel brave enough to deal with a text-only installation process.

Let me know how you get on.

---

### Post by glenn45 on 2006-08-20
yes it might be your graphics driver. you could try tweaking your xorg.conf file in the /etc/X11 directory. sorry, cant help you much , im not in my ubuntu machine right now. but your problem is solvable. look around the forums.

---

### Post by FynitE! on 2006-08-20
Ok, i'll try those now.

---

### Post by FynitE! on 2006-08-20
Safe graphics mode just took me to a black screen, then my monitor started "Searching for signal".

---

### Post by Kilz on 2006-08-20
> **FynitE! said:**
> Safe graphics mode just took me to a black screen, then my monitor started "Searching for signal".

I do have a ATI driver install script, that may work. Look in my signature. Im still not happy with it as some igp models still have problems. Alternatly there is a [howto here that seems to work.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

Either way to download the driver or the script. Navigate to the desktop with cd ~/Desktop and then wget -c [http://addressofthefile](http://addressofthefile) you want to download. If you want to use the script Untar it then launch it with ```
tar -xzvf ATI-8.27.10-install-amd64-3.tar.gz ATI 
cd ~/Desktop/ATI
sudo ./ATI
```

---

### Post by FynitE! on 2006-08-20
Thanks a lot! 

That sounds like it will work! :)

So after i've done that, im guessing I just load up GNOME using

*sudo /etc/init.d/gdm start*

and then just continue to use the live CD to install ubuntu yeah? :)

---

### Post by FynitE! on 2006-08-20
When I do:

wget -c [http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-amd64-3.tar.gz](http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-amd64-3.tar.gz)

I get:

Resolving home.comcast.net... failed: Temporary failure in name resolution.

Is that the correct URL?


EDIT: Duh, it hasnt detected my internet. Hmn, is is possible for me to put the file on a flash stick, and then cp it to the desktop?

---

### Post by Kilz on 2006-08-20
> **FynitE! said:**
> When I do:

wget -c [http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-amd64-3.tar.gz](http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-amd64-3.tar.gz)

I get:

Resolving home.comcast.net... failed: Temporary failure in name resolution.

Is that the correct URL?


EDIT: Duh, it hasnt detected my internet. Hmn, is is possible for me to put the file on a flash stick, and then cp it to the desktop?

Not really, because the script downloads things, but you can follow the howto I linked to above with downloaded files.

---

### Post by FynitE! on 2006-08-23
ok, ive got a PCI network card from my mate to use for now to install. After its finished, how do I restart the X-Server? 

Sorry for being an idiot :>

---

### Post by FynitE! on 2006-09-26
Sorry to bump such an old thread! I tried fedora and it wasnt for me, and I love ubuntu so much :P

Im still getting this trouble. If anyone can answer the question above that'd be great, how do i attempt to restart the installer after installing the driver?

---

### Post by DRF on 2006-09-27
If the problem your having is with the Live CD not displaying any graphics you may want to look in the help on the live CD options screen (first one to appear) in case there is something mentioned there.

But you might have more luck downloading, burning and installing from the alternate install CD. The installer on the alternate CD isn't in my opinion as easy for someone new to ubuntu as it cuts out the graphical interface used in the live CD but it's not much harder to use (just not so pleasent on the eyes).

If you've had problems with getting the graphics drivers to work on the live CD you may find when you reboot after installing from the alternate CD you get a similar error. But might be fixable by trying different drivers or getting the latest updates.

Hope this helps,

Daniel

---

