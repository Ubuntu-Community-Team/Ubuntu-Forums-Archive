---
title: "I feel really let down."
date: 2008-06-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2008-06-24
I got my opensuse 11 DVD this morning. I installed KDE 3.5.9. The first thing I noticed was the kmix kicker applet wasn't to be found. Then I noticed that akregator wasn't there. My volume keys wouldn't work(worked perfect in 10.3). My remote didn't work(worked with 10.3) I started looking in the repos and figured out that most of the KDE apps that had been updated for KDE4 didn't have an entry for the old KDE3 apps. Now to have a fully functional KDE 3.5.9 desktop, you have to mix it with KDE4 apps. I see now that KDE3 was just a tolerated desktop environment for opensuse 11. The only improvement I saw was better conflict resolving, and faster package managment. I think I am through with suse. I refuse to use KDE4.

---

### Post by jrusso2 on 2008-06-24
> **67GTA said:**
> I got my opensuse 11 DVD this morning. I installed KDE 3.5.9. The first thing I noticed was the kmix kicker applet wasn't to be found. Then I noticed that akregator wasn't there. My volume keys wouldn't work(worked perfect in 10.3). My remote didn't work(worked with 10.3) I started looking in the repos and figured out that most of the KDE apps that had been updated for KDE4 didn't have an entry for the old KDE3 apps. Now to have a fully functional KDE 3.5.9 desktop, you have to mix it with KDE4 apps. I see now that KDE3 was just a tolerated desktop environment for opensuse 11. The only improvement I saw was better conflict resolving, and faster package managment. I think I am through with suse. I refuse to use KDE4.

Yes this seems troubling at least until KDE 4 is fully finished.

---

### Post by 67GTA on 2008-06-24
I actually broke down and installed KDE4 on top of it after seeing this just to check it out. I swore I would drink poison before that happened:mad:. The screen turned white while I was adding my /home folder to the kicker since "only stupid people use icons on their desktop", and I couldn't recover. I rebooted, and the kicker icons were gone, and nothing would work. I haven't tried Kubuntu 8.04 yet. Is it in the same shape? If so, I will just have to reinstall Kubuntu 7.10 and stay there.

---

### Post by 67GTA on 2008-06-24
I just answered that. Ubuntu still has all of the 3.5.9 versions in the repos. They will probably disappear in Intrepid.

---

### Post by Antman on 2008-06-24
have you tried upgrading to the KDE4.1 beta?

---

### Post by 67GTA on 2008-06-24
I didn't want to mess with KDE4. I just wanted to see if I could get a full DE by installing it(I did). I don't plan on migrating once 3.5.9 is gone. I won't use KDE4 unless I can have my desktop back.

---

### Post by Growbag on 2008-06-26
Yeah 4.1 beta is great compared to 4.0!

I don't understand why NOT being able to change the menu bar background or hide the menu bar is a good thing!!

KDE4 is a complete mystery to me ö_Ö.

But 4.1 beta at least doesn't give me as many problems as 4.0.

The laptop keys thing is another suse mystery, the dev in charge of that got pissy when asked why on earth they no longer include "laptop-keys" in opensuse, his answer was simply "we no longer ship laptop-keys with openSUSE".

Seems a bit odd, and even completely bloody stupid if you ask me.

Now nobody has laptop keys working, and the volume control never saves the ones you assign between reboots!!

Same with that stupid "Pulse Audio" thing, it might be a fabbo whiz-bang new technology with flashing neon lights and warp 20 hyperthrusters as standard, but when it constantly crashes and takes your Audio down with it, what is the point?

I must be completely stupid or something, but my thought is that when something doesn't work properly and you can't fix it, you dump it in favour of something that actually works.

---

### Post by 67GTA on 2008-06-26
This version has really pissed me off. 10.3 was almost perfect except for the package management. Now with 11 they have fixed the package management and broke things that worked out of the box with 10.3. This was suse's last chance to impress me. I really wanted to like opensuse. I'm not sure how the rpm stuff works. Would it be possible to upgrade the package manager and zypper on 10.3 to 11's version, or is the dependency ties the same as Debuan based OS's?

---

### Post by some-guy on 2008-06-26
> **67GTA said:**
> This version has really *** me off. 10.3 was almost perfect except for the package management. Now with 11 they have fixed the package management and broke things that worked out of the box with 10.3. This was suse's last chance to impress me. I really wanted to like opensuse. I'm not sure how the rpm stuff works. Would it be possible to upgrade the package manager and zypper on 10.3 to 11's version, or is the dependency ties the same as Debuan based OS's?
it is possible, add the zypp:Backport and YaST:Backport repos, then upgrade everything, though you will not get the LZMA compression (which makes installing the RPMs faster)

11.0 imo is a great release, I think they did remove a little too much, but I really like it. PulseAudio requires that you add yourself to pulse-access group.

KDE4.0.x was like a preview, 4.1.x is the real thing ;)

---

### Post by lxuser2008-X on 2008-06-27
> **67GTA said:**
> I got my opensuse 11 DVD this morning. I installed KDE 3.5.9. The first thing I noticed was the kmix kicker applet wasn't to be found. Then I noticed that akregator wasn't there. My volume keys wouldn't work(worked perfect in 10.3). My remote didn't work(worked with 10.3) I started looking in the repos and figured out that most of the KDE apps that had been updated for KDE4 didn't have an entry for the old KDE3 apps. Now to have a fully functional KDE 3.5.9 desktop, you have to mix it with KDE4 apps. I see now that KDE3 was just a tolerated desktop environment for opensuse 11. The only improvement I saw was better conflict resolving, and faster package managment. I think I am through with suse. I refuse to use KDE4.

I have 10.3 installed on an Acer laptop that I am keeping as is (actually just running on official repos + smart). As I mainly use Linux for web surfing, email and downloading/burning some isos, I don't really need to use any other repos and though I had it fully setup to run all multimedia stuff via Packman and Vidolan repos, I removed them in order to have less hassle with updates and package management. I have been using SMART PM and just realised that while it is nice and intuitive it was downloading about 25 MB of metadata even if no packages installed needed updates, CLEARLY NOT VERY SMART. The Yast (and Zypper) PM downloads about 1/3 or less of that amount and that is what I will be using from now on (unless I need to do some removing that Yast will not let me or upgrading/downgrading Yast and Zypper). I tried upgrading Yast and Zypper and found that there were too many changes and conflicts and NOT 100% functionality, hence I downgraded (using SMART) back to original. For comparison, Fedora 9 is now pulling 4 MB in metadata just for the updates repo and is growing every time there are more updates. So, openSUSE 10.3, though older and with much more updates in the list, is downloading less metadata when using Zypper or Yast package manager. Ubuntu 8.04 (Synaptic) is now up to about 540 kb for a repo refresh and is really much faster when you take this into consideration. Time being relative to your Internet connection speed and a slow connection could be very frustrating and making Ubuntu an obvious preference! Look for resolution of metadata payload in openSUSE 11.1 and a possible leap to the lead of the package manager pack.

FYI: I have openSUSE 11.0 installed on a another machine (via netinstall iso and a mostly clean kde 3.5.9) and I can check to see if it concurs with your experience on the packages you say are missing. For some of those packages, it might be a case of them not being installed by default but available in the repos. I am running in Ubuntu right now but I am almost sure the kmix applet is there.

Cheers

---

### Post by 67GTA on 2008-06-27
I'm actually the dumba@#. I forgot that Debian KDE packages are separate. You can install akregator or kmix individually. Opensuse lumps stuff together. When I installed the first time, I removed kdepim to get rid of kontact, but it also contained akregator. I removed this stuff without knowing it. The package manager has been improved to the point that it just removed them without asking me for a manual conflict resolver like 10.3. I reinstalled and left the packages alone, and all is great. I will just have to hide the unwanted apps that caused this in the menu. Right now ktoorent and a couple of other snall apps are the only ones that have the KDE4 versions.

---

