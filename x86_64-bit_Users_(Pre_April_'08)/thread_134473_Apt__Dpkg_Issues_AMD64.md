---
title: "Apt / Dpkg Issues AMD64"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by nandemonai on 2006-02-22
Greetings all, 

I've noticed a thread about troubles install Ubuntu64, that the image is somehow damaged...

Well I managed to get it installed by doing a server install and all went well...

I setup apt's sources.list with my isp's mirror (I'm pretty sure that is not the issue here).

I then tried to install ubuntu-desktop via apt to get gnome up and running and started to notice a few font errors as it configured everything.. alas the desktop did come up on next reboot so all was well so far..

So I decide to start install some stuff and I notice that apt is giving me an error, being:

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

First time it did this it did tell me to run dpkg --congfigure -a but that just yielded the same error message. Note now the error just displays and does not tell me to try the above command.

So now any apt-get install or upgrade gives me this error and I can't seem to get around it.

I did notice this in my mail box:

To: root
Subject: Debconf: Configuring x-ttcidfont-conf -- FontPath of TrueType and CID managed by defoma is changed
Message-Id: <20060221172124.A8F69D7B26@rendai-ratbox>
Date: Wed, 22 Feb 2006 03:51:24 +1030 (CST)
From: root
Status: RO

TrueType and CID font paths which defoma manages have changed again.
Please add these entries to the "Files" section of /etc/X11/xorg.conf:

  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"


Also add these two directories to the "catalogue" path lists in
/etc/X11/fs/config and/or /etc/X11/fs-xtt/config, and delete any mention
of /usr/lib/X11/fonts/CID in any of these files.

--
Debconf, running at XXX
[ Debconf was not configured to display this note, so it mailed it to you. ]

So I go through and follow the instructions, only to find that the lines I'm supposed to add for xorg.conf are already there and the last and/or files mentioned do not exist.

So that my problem, I have a brick because I can't install anything...

Any ideas would be greatly appreciated, thanks in advance.

Nandemonai

---

### Post by uniko on 2006-02-23
You could try:

sudo dpkg --configure --force-depends -a

and after that maybe remove the offending package (x-ttcidfont-conf?).

---

