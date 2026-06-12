---
title: "ECC crash Ubuntu 9.10 upgrade"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by flyn_brian on 2009-11-05
Hello all After I got Ubuntu 9.04 almost configured to my liking I decided to take the plunge and update from 9.04 to 9.10. I gotta admit that the update did a few things that I was struggling to get through like installing the most up to date video driver and such. But now when I log on I get a crash and apparently its a bios setting that my bios doesnt support. The crash is:                                                                                  [B]EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded
[/B]

ECC stands for Error correction control and it deals with the ram But my bios wont let me tweak this option I even booted into winblows vista and flashed my bios to the latest bios but to no avail. Any help would be appreciated and freely passed on thank you in advance

---

### Post by timgood on 2009-11-05
This is a known bug - and the crash report does not affect your system which will keep running quite happily. As far as I am aware the latest set of updates seem to help - I have not had this happen since I installed them yesterday. YMMV. But don't worry, it does not affect your system and you do not need to reboot when it happens. Ignore it for now, and hopefully after updates it will just go away. Hope this helps.

---

### Post by flyn_brian on 2009-11-05
Thank you for you fast reply. I noticed that it was a known bug and the only solution I notice was to turn off the automatic check for updates. Thank you I just updated my system and I put the check back in the automatic check for updates. No crash yet :D so I think it might have worked.

---

### Post by BrokenKingpin on 2009-11-17
If the BIOS does support this is it best to turn it on?

---

### Post by efflandt on 2009-11-17
Actually the fix was not really to disable updates.  The problem was that apport was enabled by default and was over zealous reporting warnings that were not really critical.  So after launchpad got inundated with bug reports, the fix was to disable apport.

For example the live CD generates multiple crash reports for known issues that do not matter.

To enable apport if you are having a real issue see /etc/default/apport

In a terminal **apropos apport** gives a list of relevant man pages to review if you need to report or follow up on a bug.

---

