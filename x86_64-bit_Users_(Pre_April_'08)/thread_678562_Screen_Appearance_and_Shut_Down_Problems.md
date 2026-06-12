---
title: "Screen Appearance and Shut Down Problems"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by lillypilly on 2008-01-26
I am running an Intel 946 mb with Intel Core 2 Duo system with onboard video and sound. The graphics shows as Graphic Card (Intel 965) using "Intel - Experimental Modesetting Driver" as automatically chosen on the install

After applying updates I get some strange problems. This has been going on for several months and I have done many clean re-installs. I did not encounter this problem while using he 32 bit version of 7.04 or 7.10 but have had it with the 64 bit version of 7.10

On a fresh install I have no problems and everything works as I would expect. If I then only put the basic updates on I still have no problems. After updating with all the updates available by automatic update the problems start.

The first sign of problems is that the shutdown button on the top right of the screen changes from the  standard red button I have always had to the green running man, the network applet changes to a mouse and several other applets change. Most applets will not work.  If I try to change the screen appearance System > Preference > Appearance this takes a long time to start and then gives an error 

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager

Most programs like Firefox and Thunderbird will still run but everything slows down considerably. I have tried with and without Skype and Flash installed and this does not seem to make any change.

Then when I try to shut the system down after the problem has emerged I am unable to get it to shutdown and have to resort to doing a system power off. Powering up the system seems to go normally until the final screen.

I have tried many things that I have read on these forums but nothing seems to work to stop the problem.

---

### Post by jeffus_il on 2008-01-28
Create a new user, log out and log in to the new user. Does the new user have the same problems?

---

### Post by lillypilly on 2008-01-28
The answer to your question is "yes". I had read that in another thread earlier and all ready tried that.

I have by a process of elimination and doing a update by file groups got it down to most probably 2 files, one of which may be the file causing the problem. They are "gnome-session" and "network-manager".

I have run the computer with no problems since the last re-install that I did just before I  started this thread. I completed the updateing the next day leaving those two files not updated and everything has gone OK since then. Unfortunately I do not have time at the moment to do another complete re-install and so I do not want to risk putting those two files on to try and see which one is causing the problem.

---

### Post by jeffus_il on 2008-01-29
I would guess "network-manager". I have had many problems with it, if you need the roaming functionality, use Wicd instead, If your machine doesn't roam, use manual configuration of the /etc/network/interfaces file, it's easy.

---

### Post by lillypilly on 2008-01-29
That goes along with my suspicion as well. This computer is on a wired link to the router. I take it from your reply that "network-manager" is for the wireless links. I will investigate the  problem further on my next break in a few weeks

Thanks for your interest in this problem. As I state in my first post I first noted this problem back in about November last year so what ever is causing it has been around for a while.

---

### Post by Yellow Pasque on 2008-01-29
Type into the terminal:
> sudo gnome-settings-daemon
What output do you get?

---

### Post by lillypilly on 2008-01-29
here is the result

sudo gnome-settings-daemon
[sudo] password for username:

** (gnome-settings-daemon:6655): WARNING **: Unable to connect to dbus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)

---

### Post by Yellow Pasque on 2008-01-29
Hmm, it appears there's an instance of gnome-settings-daemon running and your applets cannot acces it. The next time you get this message:
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager
Go to System -> Administration -> System Monitor and see if there's a gnome-settings-daemon process running.

---

