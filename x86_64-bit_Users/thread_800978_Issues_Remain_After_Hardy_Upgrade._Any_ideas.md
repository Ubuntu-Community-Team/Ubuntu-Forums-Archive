---
title: "Issues Remain After Hardy Upgrade. Any ideas?"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by stephenb on 2008-05-20
I have a few issues since my Feisty > Gutsy > Hardy upgrade. Some have been sorted, but I can't find much about these ones below. Does anyone have any ideas?

--------

[U]SEGFAULT ERRORS DURING BOOT UP
[/U][INDENT]     nautilus[26679]: segfault at 43000034 rip 3987c23f0f rsp 7fffffbbdf90 error 4

    gnome-keyring-d[5943]: segfault at 60 rip 60 rsp 7fff9eba8908 error 14

    firegl1.isse.a0[5409]: segfault at c rip 4a6dcf39 rsp ff98aeb0 error 4

    gdm[5531]: segfault at 392e520 rip 397e22b55a rsp 7fffc30db6e0 error 4
[/INDENT]I'm not sure what these mean and they don't seem critical because most things seem to be working. Launchpad had something about the keyring, so that could be fixed soon. 

_WINE IS COMPLETELY BROKEN_

I get this with the last two versions as well as the earlier 0.9.54[INDENT]wine[20049]: segfault at 4a6c3f68 rip 4a6c3f68 rsp ffecaeac error 15
[/INDENT]_SKYPE (the non-static variant) IS BROKEN_

I didn't hold out much hope anyway when I'd heard there was a 64 bit version.[INDENT]     skype[24687]: segfault at 0 rip 0 rsp ffdcceb0 error 14
[/INDENT]_NETWORKING IS UNSTABLE _

Often when I select Places > Network nothing comes up. Then after a while I'll get a popup with this message:[INDENT]Couldn't display "network:///".

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. Please select another viewer and try again.
[/INDENT]Sometimes selecting Places > Network works. It shows my workgroup, however, it cannot display anything within the workgroup, as it used to. Sometimes it just processes, finding nothing, until I hit the reload button. Then I can see my machine but nothing else. 

_BACKGROUNDS AND EMBLEMS HAS A BUG_

Unless I use the "View as list" option I get crazy background patterns that make folder names illegible. I have to add another background to read them or view everything as a list in every window.

[U]NSPLUGINWRAPPER NO LONGER WORKS
[/U][INDENT]nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
[/INDENT]--------

I've noticed a few people with one or two of the same issues, but none of the problems I'm having seem to be widespread. Has anyone else encountered any of these things and found a fix?

---

### Post by Jouke74 on 2008-05-20
The only idea I can give you is to do a clean install instead of an distro upgrade. This will be at the cost of loosing lots of stuff you have tweaked already, and you need to make a backup of all your personal files (basically /home). This will very likely solve most issues since new config files will be made. Things have changed a lot between Feisty and Hardy. However there is no guarantee it will work flawlessly and it is also possible new issues might come up.

---

### Post by stephenb on 2008-05-20
Thanks for the suggestion, Jouke74. I've read recommendations like that before. But I was reluctant to go down that path partly because of the reasons you cite. As you say, a clean install doesn't come with guarantees either. I remember I had a difficult time with Feisty even after a clean install. 

It's just disappointing, when things were working so well before the upgrade. Anyway, these problems are not absolutely critical to me, and I suspect some of them will be fixed eventually. 

As a 64 bit  Linux user, I'm getting used to waiting at the end of the line.

---

### Post by stephenb on 2008-05-21
OK, here are some more things I'd like to add to the list above. 

_NFS WON'T MOUNT_

Internal error when I attempt to mount with NFS. At the command line I get this:[INDENT]mount.nfs: internal error
[/INDENT]If attempting to mount via fstab, I get this:[INDENT]rpcbind: server inspiron not responding, timed out

[/INDENT]_HAL_

Something I haven't seen since 2006:[INDENT]HAL failed to initialize.

[/INDENT]Bring it on Hardy . . .

---

### Post by Jouke74 on 2008-05-21
I still suggest a reinstall. It seems like your config is damaged at several points. Fixing all these issues will probably take more time then reinstalling and figuring out any new issues (if there). To see if you have any major issues, you could try and run the live CD for a while first?

---

