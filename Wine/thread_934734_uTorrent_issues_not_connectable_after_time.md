---
title: "uTorrent issues not connectable after time"
date: 2008-09-30
forum: Wine
---

### Post by tazeat on 2008-09-30
System Specs:
P4 3.0 GHz w/ HT
512mb DDR1

Hardy 8.04 upgraded from 7.04, Everything up to date, nothing out of the ordinary with packages, everything is pretty much vanilla... I have apache2 and pptp installed just from packages.

The problem:
I start up uTorrent and it starts up fine working at full speeds, connectable both from "telnet localhost port" and on the uTorrent website. I have ports forwarded on my router using static ips, all nat/windows firewall options are disabled. After I leave the computer seeding for a few hours I come back and the speeds have drastically dropped if it even works at all (often just says 0.0 down, 0.0 up). Trackers still connect ok and peers show up when you update them (although they never connect).

Once it becomes non connectable and slowed I can no longer use the "telnet localhost port" command (I have tried different ports all the same).

I am using the latest uTorrent beta as well as the latest wine, 1.15 but I have also tried 1.0 and .96 as well from the winehq website.

Has anyone else had any problems?

I am seeding approx 150 torrents... I have not wanted to try and move them to deluge as I hear that client is coming up and quite featureful but I've never used it.

---

### Post by asdfoo on 2008-10-01
> **tazeat said:**
> System Specs:
P4 3.0 GHz w/ HT
512mb DDR1

Hardy 8.04 upgraded from 7.04, Everything up to date, nothing out of the ordinary with packages, everything is pretty much vanilla... I have apache2 and pptp installed just from packages.

The problem:
I start up uTorrent and it starts up fine working at full speeds, connectable both from "telnet localhost port" and on the uTorrent website. I have ports forwarded on my router using static ips, all nat/windows firewall options are disabled. After I leave the computer seeding for a few hours I come back and the speeds have drastically dropped if it even works at all (often just says 0.0 down, 0.0 up). Trackers still connect ok and peers show up when you update them (although they never connect).

Once it becomes non connectable and slowed I can no longer use the "telnet localhost port" command (I have tried different ports all the same).

I am using the latest uTorrent beta as well as the latest wine, 1.15 but I have also tried 1.0 and .96 as well from the winehq website.

Has anyone else had any problems?

I am seeding approx 150 torrents... I have not wanted to try and move them to deluge as I hear that client is coming up and quite featureful but I've never used it.

While I azureus not utorrent, I'll just say that it's entirely possible you've found a bug in Wine.

Do you see any error messages on the console when you experience the problem?

You'll need to start utorrent by opening a terminal, changing to the install dir then running: wine utorrent.exe 2> log.txt

That will redirect any messages from wine into the file log.txt, which you can view once you have the problem

---

### Post by david_kt on 2008-10-01
> **tazeat said:**
> 

Once it becomes non connectable and slowed I can no longer use the "telnet localhost port" command (I have tried different ports all the same).

I am using the latest uTorrent beta as well as the latest wine, 1.15 but I have also tried 1.0 and .96 as well from the winehq website.

Has anyone else had any problems?

I am using uttorent and wine 1.0, so far no problem. I suspect your ISP is throttling torrent. You could try to enable encryption to by pass throttling:

[INDENT]Preference > Bit torrent > on outgoing connection choose "enable"
and also tick "allow incoming legacy connection"[/INDENT]

To be sure, remove windows firewall exception (as we do not have windows firewall:

[INDENT]Preference > Connection > do not tick "Add Windows Firewall exception[/INDENT]

Restart utorrent and hopefully it help.

DK

---

### Post by tazeat on 2008-10-02
Well its never really been much an issue with speeds so much as being connectable. My ISP has no effect over whether or not I can connect even using a telnet localhost command. I've always torrented without issue before my upgrade to hardy (along with upgrading to newer wine and everything else) nor do any of my Windows computers suffer from any issues of this kind.

Although yesterday very interestingly after it was no longer connectable I was still uploading full speed so  I changed port, then changed it back... its been a full day (the longest I've seen) and its still working great. I'm not sure I played with a few settings so it might have been something else... I disabled resolve IPs, changed some cache settings, and I turned down the max half-open from 8 to 4... Not sure if any of those did it, but I'm not touching it until it breaks again.

---

### Post by Transmission3000 on 2008-10-02
> **tazeat said:**
> Although yesterday very interestingly after it was no longer connectable I was still uploading full speed so  I changed port, then changed it back... its been a full day (the longest I've seen) and its still working great. I'm not sure I played with a few settings so it might have been something else... I disabled resolve IPs, changed some cache settings, and I turned down the max half-open from 8 to 4... Not sure if any of those did it, but I'm not touching it until it breaks again.

I have the same issue. I know my ISP isn't throttling me. It actually happened after a Wine update, I think. I'll try your settings and switch the port and see if I can get it to work. Good suggestions.

---

### Post by tazeat on 2008-10-03
A day later I open it up 0.0 up 0.0 down, not connectable :(...


I just upgraded to the 1.8.1 RC1 I don't know if that will change anything though, I'm still trying to figure this out...


Ok I just completely deleted my .wine folder and completely uninstalled wine, then reinstalled w/ newest 1.1.5 and re-ran the configure utility... Left on default XP emulation and picked auto detect on folders.... I'll report back...

---

### Post by tazeat on 2008-10-04
No luck.

Upgraded to 8.10 beta, same thing.

Deleted all traces of the utorrent profiles/settings info and started fresh, same thing.

I think it may be my PCI Gigabit DGE-530t which uses the SKGE driver (the newest one on marvell's website wont compile on the newest kernels, I've tried that other people have the same issues trying to use it). Now that I think about it I upgraded to Hardy about a week after I got that card, it could be a bad coincidence... 

I'm using my onboard 100mbit port at the moment, working great for almost an hour now, no 35~40mb/s file  transfers though... But thats ok 11mb/s is bearable for now if it fixes these issues...

edit: Working great still a day later...

---

### Post by Transmission3000 on 2008-10-06
> **tazeat said:**
> No luck.

Upgraded to 8.10 beta, same thing.

Deleted all traces of the utorrent profiles/settings info and started fresh, same thing.

edit: Working great still a day later...

Yeah...nuking the .wine folder, as well as all saved uTorrent settings is my next move. I "reinstalled" Wine, but I forgot to cover my tracks. I'll do that and report back...

Together, we will solve this weirdass problem.

---

### Post by tazeat on 2008-10-07
HA it wasn't that either. Figured a workaround and i submitted bug report on uT forums.

Change half open in advanced to 50 or more, has been running 3 days straight now :). Found someone else who had same problems on a 100mbit box, he says his problems are fixed as well after setting to 50.

---

