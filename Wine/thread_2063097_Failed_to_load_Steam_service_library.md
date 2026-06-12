---
title: "Failed to load Steam service library"
date: 2012-09-26
forum: Wine
---

### Post by zuti on 2012-09-26
I'm running into a problem with the latest version of Steam and current wine builds. For some reason when the windows version is set to Windows 7 under winecfg, Steam will require admin privileges for the installation of a service component. But even after going through the installation, it is obviously not detected:

err:eventlog:ReportEventW L"Failed to load Steam Service library."

The problem can be seen with Portal 2, and what's worse, I think it also popped up with the new XCOM demo. 

Has anyone been able to successfully install the component?

---

### Post by thatguruguy on 2012-09-26
If you can wait a month or two, Steam is coming to Linux.

---

### Post by zuti on 2012-09-26
> **thatguruguy said:**
> If you can wait a month or two, Steam is coming to Linux.

So they say :) 

I doubt the bigger titles will get ported any time soon, so better to stick with wine for now. 

I'd use WinXP mode to get past the service installation, but it seems Win7 works better with Steam and games at the moment.

---

### Post by zuti on 2012-10-13
Apparently this might be fixed in 1.5.15 ([http://bugs.winehq.org/show_bug.cgi?id=31861](http://bugs.winehq.org/show_bug.cgi?id=31861)). Just have to wait until the Quantal package is compiled, since there's no longer a quick way to compile it on my own 64-bit Ubuntu installation :(

---

### Post by vladdy on 2012-10-15
Actually the current version of wine ppa doesn't compile on quantal, I copy the binaries over from precise.

However it should easily be possible to make it work again though, I'm just looking for steps that make it easier on my side to upload both and keep them in sync.

EDIT: I just copied over 1.5.15, enjoy!

---

### Post by zuti on 2012-10-15
Great! Thank you! 

Steam is indeed working with 1.5.15 as it should again, and as an added bonus, XCom also starts, but crashes after a while in the tutorial. 

I guess I'll have to set up a 32-bit environment so I can compile wine with the needed patches until they are added to the ~bi-weekly releases. (if someone ends up here after searching for xcom, this link may be useful: [http://bugs.winehq.org/show_bug.cgi?id=31794](http://bugs.winehq.org/show_bug.cgi?id=31794)).

---

