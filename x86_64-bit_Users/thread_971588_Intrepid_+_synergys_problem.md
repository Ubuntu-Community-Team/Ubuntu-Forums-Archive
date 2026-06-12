---
title: "Intrepid + synergys problem"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by jwo on 2008-11-05
I've been using Hardy 64-bit for several months now, and everything has been fine in regards to synergys. With no changes in my computer setup, nor links, synergys no longer works properly after upgrading to 64-bit Intrepid.

Description of problem: Connection from client works properly. Mouse and everything else is properly recognized on host machine. Move mouse to client machine, mouse clicks and keyboard are also all recognized correctly. I move the mouse back to the server 64-bit machine and the mouse movement is tracked, but I can no longer move any more windows nor change the focus of windows using the mouse. I can still type using tab navigation however.

I've tried running synergys -f and running both client and server in debug mode 2 but it doesn't tell me why synergy fails to recognize movements of windows. Anybody experiencing this problem or perhaps no why it suddenly wouldn't work in Intrepid vs. Hardy?

---

### Post by blazerw on 2008-11-06
I've got a similar issue. For me, the mouse buttons stop working on the server machine while on the client they still work. So, on the server I can do anything with the keyboard, but I can't use the mouse. The cursor moves, but clicking and using the mouse wheel have no response. This sounds like your issue, except that it takes hours before it occurs. I'm trying to determine if synergy is the cause and am running without it for a day.

**UPDATED:** Ignore my post, it's different from the issues described in this thread. If you have my issue, here's the info as posted by blacky667 in this thread ([http://ubuntuforums.org/showthread.php?p=6124247):](http://ubuntuforums.org/showthread.php?p=6124247):)
> found a bug description with work around which helped in my case: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/261995](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/261995)

in short: uncomment the InputDevice sections in /etc/X11/xorg.conf (if they are commented out by update-manager) and add the following:
Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection

---

### Post by Greeblesnort on 2008-11-07
I think I can confirm this problem as well. I've been fighting with this since I upgraded my 8.04 workstation to 8.10 yesterday and believe I've tracked it down to one of a couple of causes:
1. running multiple terminal services clients
2. the exact same synergy issue described above; all works as expected, but as soon as you move mouse to client workstation (Windows XP in my case) and then move it back to the server (x86_64 8.10 Ubuntu), the mouse will continue to track but cannot click on anything, right, left, or otherwise.

Some additional information:
1. xev appears to work fine until I lose mouse clicks, it then stops reporting anything
2. there is no output from any of "sudo cat /dev/input/[mice|mouse0|mouse1]" before, after, or during the issue

I did switch xorg.conf to use "/dev/input/mice" per some troubleshooting I found elsewhere.

"lsmod | grep mouse" lists only psmouse. rmmod'ing psmouse does not appear to affect anything.

Running multiple instances of Gnome-RDP does not appear to cause any problems. But I can 100% reproduce this issue running two instances of the Terminal Services Client.

This issue occurs, so far, 100% of the time when passing mouse control across to the synergy client.

Lastly, this all worked (multiple TS clients, synergy) with 8.04.

---

### Post by Greeblesnort on 2008-11-11
a little more information...

With synergy running, I can go to the client (WinXP in this case) and the mouse is still working *on the client*. The mouse continues to track on the server, but I can not click. This happens the first time the mouse returns to the server screen from the client. Restarting synergys has no effect. cat /dev/input/mice does show output now for both movement and clicking.

The only change I've made is the 'Option "AutoAddDevices" "false"' to xorg.conf.

---

### Post by Greeblesnort on 2008-11-11
sorry, one more little piece...xev shows nothing in this state

---

### Post by Greeblesnort on 2008-11-11
and one more small piece, starting a guest session creates another session where the mouse works normally...however, leaving that session appeared to leave Gnome in a wierd state, and I had to ctrl-alt-bckspace to get out of it

---

### Post by blazerw on 2008-11-13
I went without synergy for a day, and the problem still occurred. I think we can rule out synergy as the cause. I think there is a bug in the new auto device detection. Although, doing the workaround mentioned in this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261995) which includes adding:
'Option "AutoAddDevices" "false"'
to xorg.conf doesn't seem to work for me.

---

### Post by jwo on 2008-11-14
So I've finally had enough time to test out my theory. I gathered that perhaps there was something different with xorg, and that perhaps my old configuration settings (I have dual monitor setup, 17 and 15) where some how incorrect.

So I used nvidia-settings and disabled xinerama, which essentially loaded a desktop on both screens. Although the screens spanned, they were registered as two separate devices.

Setup:
17 15 Laptop(xp)

When running synergys on the 17", nothing registered on the Laptop. When running synergys on the 15", everything worked with synergys.

However, of course I want my dual setup, and so I enabled twinview and now I get one screen, and synergy.

I should also note that I reconfigured my xorg.conf using dkpg, but it didn't seem to solve anything. However it may have moved me to a clean slate, should there have been any additional problems with my config before I adjusted xorg-config using nvidia-settings.

---

### Post by ussher on 2008-11-14
Same deal here. 2 monitors on kubuntu 8.10 (nvidia card) synergy server.(quicksynergy 0.7)
laptop with XP.  synergy client.(1.3.1)

The mouse click wont click after using an application in XP then coming back.

The one exception is if i hit ctrl+alt+esc to try to kill the quicksynergy window to get operation back.  The X will appear and when i click on the window to kill it the X will disappear, but the window is still there.

Also tried running 'sudo quicksynergy', but it didn't help.

---

### Post by troyvit on 2008-12-08
> **jwo said:**
> So I've finally had enough time to test out my theory. I gathered that perhaps there was something different with xorg, and that perhaps my old configuration settings (I have dual monitor setup, 17 and 15) where some how incorrect.

So I used nvidia-settings and disabled xinerama, which essentially loaded a desktop on both screens. Although the screens spanned, they were registered as two separate devices.

Setup:
17 15 Laptop(xp)

When running synergys on the 17", nothing registered on the Laptop. When running synergys on the 15", everything worked with synergys.

However, of course I want my dual setup, and so I enabled twinview and now I get one screen, and synergy.

I should also note that I reconfigured my xorg.conf using dkpg, but it didn't seem to solve anything. However it may have moved me to a clean slate, should there have been any additional problems with my config before I adjusted xorg-config using nvidia-settings.

I tried what you recommended and:
[LIST=1]
[*]The settings didn't stick, though I saved the resulting xorg file
[*]I still experienced the same problem
[/LIST]

I'm using a Macbook Pro (penryn) with Nvidia graphics and an attached apple cinema display.

---

### Post by h00ch on 2008-12-09
Quick fix for problems arising with Synergy

I am testing my theory that the mouse fails with xorg/xinerama when moving from a virtual screen, e.g. with synergy, to an area that would be outside of the X screen. Since Xinerama LeftOf or RightOf aligns the top of the screens regardless of the screen size, the bottoms will not be aligned when using two different sized screens or when putting screens in different rotational orientations.

Quick fix for Synergy, set the options to disallow moving between screens in an area that would put the mouse outside of the gui on the x screen.

in /etc/synergy.conf (or wherever you store your synergy conf file) add the following to the remote screen:

section: screens
        clientcomputername:
                switchCorners = bottom-right
                switchCornerSize = 800
        mycomputername:
end

800, in my case, is the number of pixels in the specified corner within which the mouse will not move between screens. Mine is 800 because I have a large portrait monitor for viewing scans and documents.  You will need to set this to an appropriate value depending on the size of your screens.

See [http://synergy2.sourceforge.net/configuration.html](http://synergy2.sourceforge.net/configuration.html) for more info

---

### Post by troyvit on 2008-12-17
> **troyvit said:**
> I tried what you recommended and:
[LIST=1]
[*]The settings didn't stick, though I saved the resulting xorg file
[*]I still experienced the same problem
[/LIST]

I'm using a Macbook Pro (penryn) with Nvidia graphics and an attached apple cinema display.

For the record re-rebuilt and updated intrepid and it works. *shrug*

---

