---
title: "XGL + Compiz working on G4 iBook without fglrx"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by aimislame15 on 2006-05-15
Yup, I managed it. Here are the steps in what I hope is an easy to read layout.

Fire up Synaptic and install these packages:

xserver-xgl
compiz
gnome-compiz
kde-compiz

Next, you'll need to edit your /etc/gdm/gdm.conf-custom. Here is what I did.
```
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
 
```

Then, I rebooted. Let's hope you're lucky and it boots right back up, otherwise, you'll have a bit of trouble with a white screen.

I then edited my compiz configuration with the configuration editor. I found that without doing that, you lose your window manager. 

Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "active_plugins" in the following order:
```
 gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```

Now you're all set. Time to make the magic happen. You're going to start compiz. I made a script/custom application launcher to launch these commands.

```
gnome-window-decorator (must be on top, start first) 
compiz --replace gconf
```

Now you should have your eyecandy at hand ;-). If you run into any problems, IM me on AIM, I'm more than willing to help.

My computer is only a 800mhz G4 iBook with 32mb VRAM. It doesn't run flawlessly and it does take up some processor speed. The only issue I have besides a bit of jittered text sometimes is it waking up in a terrible mood from sleep. Those of you with better macs shouldn't have any problems. Thanks for reading, Eric.

---

### Post by ssam on 2006-05-16
i made some more up to date packages from src packages at [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz).

quite a few bugs have been fixed since the ubuntu universe packages were made.

you can download them from
[http://tygier.co.uk/xgl/index.html](http://tygier.co.uk/xgl/index.html) , you probably dont need all the packages to make it work, eg you dont need the dev packages unless you want to recompile stuff.

there is more discussion on [http://compiz.net/viewtopic.php?id=701](http://compiz.net/viewtopic.php?id=701)

i'd like to here if they work for you.

---

### Post by aimislame15 on 2006-05-16
I'm going to see if I can get Xgl/Compiz working on my G5 before I go any farther with this stuff, but I really like that people are making improvements in the PPC area on this. Now if only Xgl would work "out of the box". Updates to ATI Drivers anyone?

---

### Post by aimislame15 on 2006-05-16
This is the issue that I have when I attempt to start Xgl as my main display. Any idea's on how to troubleshoot it? I also get a -fullscreen command not found.


```
dlopen: /usr/lib/libGL.so.1: ELF file data encoding not big-endian

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.
```

---

### Post by ssam on 2006-05-17
which packages is that error with?

i got that when i was using bersace's cross compiled packages from [http://compiz.net/viewtopic.php?id=701](http://compiz.net/viewtopic.php?id=701) . i think it means that /usr/lib/libGL.so.1 is compiled for a little endian processer (x86) and you are trying to run it on a big endian one (powerpc).

---

### Post by aimislame15 on 2006-05-17
I fixed that one by getting the libGL.so.1 package on my iBook and moving it over to my G5. Next problem is keeping xgl running. I'm getting a new error on that that I'll post later. Does anybody have xgl running on a G5?

---

### Post by aimislame15 on 2006-05-18
Bump for some help!?

---

### Post by eidex on 2006-06-03
[QUOTE=aimislame15]Yup, I managed it. Here are the steps in what I hope is an easy to read layout.

Fire up Synaptic and install these packages:

xserver-xgl
compiz
gnome-compiz
kde-compiz

[/QUOTE]

hi,

just for those who gave up (like me) when apt-get could not install these packages: they are named compiz-gnome and compiz-kde

---

### Post by matt221984 on 2006-06-06
[QUOTE=aimislame15]
I then edited my compiz configuration with the configuration editor. I found that without doing that, you lose your window manager. 

Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "active_plugins" in the following order:
```
 gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```
[/QUOTE]

I found that compiz doesnt show up in gconf-editor until you run it once. Kind of a necessary evil I guess. I just ran the line c**ompiz --replace gconf** and then logged out and logged back in again and then ran gconf-editor to modify the settings.

PS, I also had to add the community maintained (binary) source under the repositories in Synaptic to be able to see the required packages.

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=aimislame15]
Start gconf-editor and go to "apps/compiz/general/all screens/options",[/QUOTE]

apps/compiz doesn't exist and X fails on boot but for some reason when I start it again using startx it works.

---

### Post by aimislame15 on 2006-06-10
I don't have anything new to add currently as far as it running on my G5 because I took the machine to work and haven't brought it home in the past 2 weeks. I'll try again as soon as I can bring it back home. Just one more try, does anyone else have it running on a G5?

---

### Post by wingk1314 on 2006-06-15
[QUOTE=n00bWillingToLearn]apps/compiz doesn't exist and X fails on boot but for some reason when I start it again using startx it works.[/QUOTE]

I'm having the same problem... some one shed some light!

---

### Post by Gnatcho on 2006-07-03
I was able to get xgl working with aimislame15's instructions, but for some reason gnome-window-decorator wouldn't work, thus preventing compiz from working properly.  I installed a number of ssam's generously provided .debs and now it seems xgl won't work (resulting in "compiz.real: No composite extension").  Could someone make absolutely clear which of those .debs ought to be installed?  Also, libgl1-mesa from ssam's .debs is conflicting with the one installed from the universal repository and won't install.  Any way to resolve that?

Thanks in advance.

---

### Post by tariqf on 2006-07-11
I have the same problem I wish I'd never installed those debs manually to update!

How can we resolve this?

---

### Post by ebel_ on 2006-08-31
> **aimislame15 said:**
> 
Then, I rebooted. Let's hope you're lucky and it boots right back up, otherwise, you'll have a bit of trouble with a white screen.


I get this white screen when booting up. iBook G4 Ati radeon 9550. Any advice?

---

