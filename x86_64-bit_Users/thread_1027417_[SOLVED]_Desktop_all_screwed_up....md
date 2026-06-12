---
title: "[SOLVED] Desktop all screwed up..."
date: 2009-01-01
forum: x86 64-bit Users
---

### Post by pcal on 2009-01-01
Hi guys,

I don't know how, but I've managed to foul up a relatively new install so completely that it is useless. It is a 64bit version, v8.10, running on an AMD Phenom quad board.

It has been relatively stable since install, but I've been trying to get some midi software running. Installed Rosegarden, Jack, and a couple of other midi driver type applications (again, can't get at it to check precise details). While attempting to set everything so it actually works (testing sound drivers to be precise), the Sound Settings page under system preferences locked up. I had to force a reboot to get out of it, and now...

Ubuntu will load OK, gives me my normal desktop for a second or so, and then goes to a low res black screen with "Gnome Screen Flash" or something to that effect in a pop up at screen centre. It looks like a half built desktop - buttons that don't work, and no valid options on anything but a calendar. The flash pop up won't go away, and I can't run anything, no access to the file system, can't even shut it down. Hardware reset is the only way out, and the same thing happens again when I reboot. 

I have directed grub to boot into recovery mode, and attempted a repair to the filesystem, and also to repair x windows system, but this has achieved nothing but to delete my proprietary graphic drivers, giving the same gnome flash screen at even lower resolution.

If I have to reinstall from the cd, it is no huge disaster - a lot of updates and applications have been installed, but not much user data. But I would rather just reverse whatever setting has been made if possible...

Can anyone give me any clues what I have managed to do?, please...

Regards,

Pcal

---

### Post by pcal on 2009-01-02
Got the title on the pop up a bit wrong... Is actually "Gnome Session Splash", not screen splash.

Any clues... please!

---

### Post by pcal on 2009-01-02
Wondering if I may have posted in the wrong forum previously... <snip> May be more relevant here. 

In summary. I have a v8.10 64bit install on an AMD Phenom quad 9550+ system. After attempting to make changes to sound settings related to a midi driver, the system crashed requiring a reboot. After the reboot, the system starts ok - allows log on normally, but rather than the usual desktop, takes me to a "Gnome Session Splash" screen, from which there is no access to anything but a calendar(?), and no escape but a hardware reset.

Any clues please on how to access my system so I can try to correct the driver problems that triggered all this?

Many Thanks,

pcal

---

### Post by Ben Page on 2009-01-02
Does it work all right from live cd? What GPU are you using? Is there some unusual app in system - preferences - sessions?
If youre into MIDI and audio, you can dnld ubuntustudio 8.10.

---

### Post by etnlIcarus on 2009-01-02
I'm guessing Gnome has spazzed out. Press Ctrl + Alt + F1 to get a text login screen and login. Then try the following commands:

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session


Failing that, I'd try creating a new user account.

Press crtl + Alt + F1 to get to a text login screen again. Login and type:

$ sudo adduser

Follow the prompts, press Ctrl + Alt + F7 to get back to your graphical environment and press Ctrl + Alt + Backspace to restart X and get back to your GDM login screen.

Then try logging in with your *new* account.

---

### Post by pcal on 2009-01-07
Thanks for that. Sorry about slow response - earning a living got in the way! ;) Will give it a try and see what happens.

---

### Post by pcal on 2009-01-07
> **etnlIcarus said:**
> I'm guessing Gnome has spazzed out. Press Ctrl + Alt + F1 to get a text login screen and login. Then try the following commands:
[snip]


OK. Everything ran more or less as expected. The line reconfigure gnome-control-center generated an error to the effect that the control center was not installed.

However, it made no difference at all to what happened on login.

Similarly, the adduser command worked ok, but logging in with the new credentials went to exactly the same screen again.

Then I tried all the options on the log in screen to do with changing the session. When I chose to use the gnome session - everything seems to work ok (wrong screen settings / drivers, but changeable). Only when I choose to run the XClient script (the default option) does there seem to be the problem. So it would seem that either the script has been corrupted, or one of the drivers / applications loaded by the script is the cause of the problem.

As I can now log in under the gnome session, where can I find the Xclient script to have a go at editing it? Is it as simple as commenting out one line at a time until it works?

Thanks again for you assistance to date :)

Regards,

Pcal

---

### Post by etnlIcarus on 2009-01-07
> **pcal said:**
> OK. Everything ran more or less as expected. The line reconfigure gnome-control-center generated an error to the effect that the control center was not installed.

However, it made no difference at all to what happened on login.

Similarly, the adduser command worked ok, but logging in with the new credentials went to exactly the same screen again.

Then I tried all the options on the log in screen to do with changing the session. When I chose to use the gnome session - everything seems to work ok (wrong screen settings / drivers, but changeable). Only when I choose to run the XClient script (the default option) does there seem to be the problem. So it would seem that either the script has been corrupted, or one of the drivers / applications loaded by the script is the cause of the problem.

As I can now log in under the gnome session, where can I find the Xclient script to have a go at editing it? Is it as simple as commenting out one line at a time until it works?

Thanks again for you assistance to date :)

Regards,

Pcal
Just a wild guess here: you weren't playing around with apt or synaptic before the error, were you?

Do the following. If it doesn't fix your problem, at the very least, it won't make it worse:

$ sudo apt-get install ubuntu-desktop

If the above fixes your desktop, it means you uninstalled something and accidentally took out half the desktop-related packages with it.

---

### Post by pcal on 2009-01-07
> **etnlIcarus said:**
> Just a wild guess here: you weren't playing around with apt or synaptic before the error, were you?

Do the following. If it doesn't fix your problem, at the very least, it won't make it worse:

$ sudo apt-get install ubuntu-desktop


As noted in an earlier post, I had been using synaptic during the session, but not immediately before the problem struck. There had been a couple of midi applications I had installed, tested, not liked and removed before installing rosegarden. It was while fiddling with midi drivers in the sound system trying to get rosegarden working that the problems began...

re-installing the desktop made no difference. The message given by apt indicated that the latest version was already installed, and no changes were made.

Is there any point in my attempting to edit the Xclient script?

Thanks again,

Pcal

PS: I've found working in the Gnome session not as "working" as I had at first thought. Lots of stuff just doesn't respond, but I can at least fudge my way into a file manager if needed...

---

### Post by etnlIcarus on 2009-01-07
Well, I'm out of ideas. Only other thing that comes to mind is installing another DE/WM and see if you can get a functional session using one of them. Try fluxbox or xfce, perhaps.

---

### Post by pcal on 2009-01-08
Well I gave up in the end. Just deleted the partitions, and reinstalled it all from the live CD. Everything is working fine again - but I'll just go off and download the 2 or 3 hundred updates again...

Thanks for your help...

Pcal

---

