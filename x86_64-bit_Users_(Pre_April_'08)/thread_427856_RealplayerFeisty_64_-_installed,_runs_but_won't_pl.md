---
title: "Realplayer/Feisty 64 - installed, runs but won't play"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slackpacker on 2007-04-29
I installed the .bin as per the [wiki instructions]("https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods") after the 32-bit libraries were installed.  Now RP runs but won't play npr's .wax files ("component missing") error.  I don't need the browser plugin.  I'm wondering if I don't have all the needed libraries...

Man, since I started using Ubuntu it bugs me more than ever that public news providers use such craptastic streaming software.  There's gotta be a better way!

---

### Post by Slackpacker on 2007-05-01
Resolved - workaround:
the .wax thing seems to be a website problem, nothing to do with 64-bit at all.  Changing npr's java link will force it to download the .smil file, like so:
javascript:launchPlayer('2','2', '30-Apr-2007', '&prgCode=ATC&v1st=B3B8CD801A67FAC8', 'RM,WM');

javascript:launchPlayer('2','2', '30-Apr-2007', '&prgCode=ATC&v1st=B3B8CD801A67FAC8', **'RM'**);
Then click the standalone player link.

Weirdly, the embedded Totem plugin is sometimes able to play these streams, but it's sporadic and takes forever to load.

---

