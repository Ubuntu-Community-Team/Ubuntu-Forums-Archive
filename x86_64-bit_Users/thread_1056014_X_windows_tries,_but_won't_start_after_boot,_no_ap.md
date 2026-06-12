---
title: "X windows tries, but won't start after boot, no apparent X error"
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by thriftee on 2009-01-31
Running 8.10, just installed the past few days.

The last thing that happened before the problem started was that I ran the apt-get stuff to get multimedia working, and it finally did work, even mms video.

Then I noticed Firfox wouldn't bookmark anything, and saw the restart needed icon, so I told it to restart.

It boots to where it says something about testing the battery on a list of messages screen, and seems to retry bringing up X windows 3 times, because I see the nVidia screen's flash and no video before it hangs on the message screen.  ctrl-alt-f7 has a cursor flashing upper left on a black screen, and ctrl-alt-f1 has a login screen with no apparent errors.

I login, and go look at /var/log/Xorg.0.log and don't see any errors.  So then I look at daemon.log and see a few errors:

x-session-manager[6102]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
x-session-manager[6102]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout  
...
gdm[5643]: CRITICAL: gdm_config_value_get_bool: assertion 'value->type == GDM_CONFIG_VALUE_BOOL' failed

I find that if I do a sudo startx that x windows comes up.

What can I do to get it to start normally?

thanks for any suggestions...

PS: it looks like its in X windows as root, which probably isn't good.

I looked at kern.log and see a warning: 'avahi-daemon' uses 32-bit capabilities (legacy support in use)

I may not be looking at the right places or finding the right stuff, just looking for obvious ERROR messages was what I was doing, trying to see if there was anything I did, or could do.

PSS: more errors in messages
Jan 31 06:18:43 ubuntu1 pulseaudio[6134]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 31 06:18:43 ubuntu1 pulseaudio[6136]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 31 06:18:43 ubuntu1 pulseaudio[6136]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 31 06:20:10 ubuntu1 bonobo-activation-server (bobc-6356): could not associate with desktop session: Failed to connect to socket /tmp/dbus-QPV7s1eHRb: Con$
Jan 31 06:36:59 ubuntu1 -- MARK --

---

### Post by Hero of Time on 2009-01-31
I'm having the same kind of error, on both my PC and laptop. My PC has an nVidia 7800 GTX, laptop an ATi Mobility Radeon x1400. In both cases I updated to the latest versions, and added some Jaunty packages (namely Xfce 4.6 RC1).

I thought that the Jaunty packages caused it, but since you have it too, I doubt that now. What I have is that the X Server actually starts, but the screen stays black and the mouse cursors stays on busy.

Logging in from the CLI, stop GDM and run startx (both root and normal user) I get my GUI as it should.

---

### Post by thriftee on 2009-01-31
Well, I can't run it this way...  I had hoped someone would have solved this before...  googling tells me people have been getting this error since 2007 at least...

I bet I've tried loading linux (debian, sabayon, ubuntu) at least 75 or 80 times on these 2 machines in the past 2 weeks.  And every single time something turns to crap and forces another reload or giving up on one distro or another, on at least one of them.

---

### Post by Hero of Time on 2009-01-31
Yeah, it sucks when this happens. And even worse, it's on both of my systems. Luckily I have a VM where I can do some research with, and an external hard drive that also fits in my laptop, so I'm going to copy a VM install to one of the partitions on the external drive, so I can at least continue with that.

My systems will get a clean install when Jaunty is released, but it's perhaps a bit too early to run it as production. Especially when ATi doesn't have it's driver working with the new Xserver release :(.

When I have more time and found a fix for it, I will reply here.

---

### Post by thriftee on 2009-02-01
Another full from scratch install, and this time I left the nVidia drivers till last.  I rebooted right before the nVidia switch, so we know it was good till that point.  After the nVidia drivers (the ones on the ubuntu sites) were installed, X no longer starts, etc, after trying 3 times.  I then made multiple tries at tweaking the xorg.conf, to simplify it, but nothing I did improved the situation.  Each time it would fail at boot, but run ok under root (via sudo) from the command prompt, giving me a session running as root.

I then tried the nVidia web site's download and still have the same problem.  The proof was to then to --uninstall those and go back to the vesa driver (nv doesn't work), at which point everything is back to working, but essentially taking all that high horsepower video I bought, and running it at 4% of race speed.

Another 3 days spent on ubuntu.

Now, before you go saying its an nVidia problem, consider that this xorg.conf and those same drivers worked fine running both cards and all 4 screens under both debian and sabayon4.  What didn't work for them was playing Windoze Media player files, thus rendering those systems crippled or useless for the intended purpose.

All in all, after all this, I have to say I did like the comparative simplicity of the ubuntu install, and comparative friendliness of its non-geek attitude both in its documentation and places like here, as compared to debian.  I am a linux noob, but been a computer person for over 30 years, and its sad given that, to be so humbled by the resulting immense complexity of installing an o/s and a few programs that certainly shouldn't be THIS tough.  

But I'm very pig headed, and simply REFUSE to scam, buy or run MS code, because I hate their guts so badly for their infinite idiotic upgrades that do nothing but line their greedy pockets while making things slower and introducing new bugs and holes for virus writers to utilize.  But I'm preaching to the choir, there, aren't I?  I wish this worked under ubuntu or sabayon4, but it looks like my only remaining choice is to try again to get the Windoze Media 9 streaming audio and video players working under debian.  I'm simply amazed at the difficulty of accomplishing that, and grateful for the scripts I found here that did actually make it work, regardless of the complexity, even just to RUN it, let alone to come up with it.  Not my preference, but it looks like a redoubled effort on debian is the only alternative left before swallowing my pride and buying MS code.

---

### Post by Hero of Time on 2009-02-01
I got my issue fixed. I thought it might have been the GDM theme I installed that caused some problems after the upgrade. I doubted that, but you can't open the GDM settings if GDM is not running unfortunatly. So I tried to see some settings through gconf-editor. When I ran it from a terminal, it was giving an error that it was missing libgailutil.so.18. I checked my Intrepid VM, and that had some of those libs. I copied them to my system, rebooted and got my GDM back.
Did the same for my laptop, and that too got it back.

So, check if you have any mentioning of **libgailutil** in **/usr/lib**.

Ow, as for your media playing issue, did you try VLC yet? It should play Windows Media files without issues. Mplayer should have no difficulties either.

---

