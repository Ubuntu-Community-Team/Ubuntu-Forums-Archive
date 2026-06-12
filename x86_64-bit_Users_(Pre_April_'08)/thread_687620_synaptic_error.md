---
title: "synaptic error"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by biddy on 2008-02-04
hi to all,

I have just recently started to get the hang of this ubuntu, i'm a happy user of it & love the idea of free software, up yours BG...
all though has gone a little pear shaped in the last 24 hours.

it started when I set my wifes ipod touch up in gtkpod.., the upshot is that I now have the following faults:

**No sound for any music, video or internet but can hear sound when ubuntu starts & logon, error when clicking on speaker icon on top panel as follows which as a red square with a white cross next to it:**

*No volume control GStreamer plugins and/or devices found.*
**No access to synaptic, get the following error:** 

[I]Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I]

Synaptic icon is no longer in the system, administration drop down menu, only icons that remain are keyring manager, network tools, printing, system log, system monitor & update manager, also add/remove programs has dissapeared from the applications menu, now i know how to add icons to panels but I certainly didn't move or delete them.

when I run synaptic from command I have no priviliges, this seems to be all down to rights but dont understand why my sound has all of sudden stopped working & I cant run any sudo commands in terminal, I am the only user setup to use this pc.

someone please help, i love my music...
:guitar::guitar::guitar:

biddy

---

### Post by kuja on 2008-02-04
Hmm, somethings definitely broken. With regards to sound its hard to tell where exactly to be pointing the finger - perhaps **esd** or **gstreamer** - at any rate, certainly not sound "in general". You'll probably need to reinstall them, which of course leads you  back to the other problem eh? 

Try running the command "*gksudo synaptic*" and see what that gets you.
If that doesn't work, well, you could always pull up a shell and use **apt-get** or **aptitude**. Seeing as its your comfort zone the first thing to do would probably be to get it working again .... maybe it uninstalled somehow, try running "[i]sudo apt-get install synaptic[/b].

---

### Post by biddy on 2008-02-07
Hi Thanks very much for your input, I have now sorted this thanks to the excellent post fromn ccollins:
turned out be that for some reason all my rights to groups had been removed or more like I removed them with a dodgy command like trying to 
sudo usermod without the -a
anyway the below commands remedied all my problems & of course access to the groups once more, thanks, 2 days without music
had to do the commands in recovery mode

sudo usermod -G ccollins,adm,uucp,dialout,cdrom, \
floppy,audio,dip,video,plugdev,scanner,netdev, \
lpadmin,powerdev,admin ccollins

sudo usermod -g ccollins ccollins

:):):)

:guitar::guitar::guitar:

---

