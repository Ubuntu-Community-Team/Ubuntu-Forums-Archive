---
title: "Starcraft not installing"
date: 2008-10-31
forum: Wine
---

### Post by ifflejink on 2008-10-31
So, I know from looking at the Wine AppDB that Starcraft is supposed to run quite reliably on Wine. However, not even the setup is working for me. Whenever I try to run the setup.exe or install.exe from the disc, an error window comes up saying "Start menu folder not found." Here's the terminal output:

```

gavin@gavin-laptop /media/cdrom0 $ wine setup.exe
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
gavin@gavin-laptop /media/cdrom0 $ ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

Can anyone help me out with this?

---

### Post by BenAshton24 on 2008-10-31
Have you tried copying the files from the CD to your wine C drive, that may help

--Ben.

---

### Post by ifflejink on 2008-10-31
I actually just tried purging and then reinstalling Wine, and that fixed the problem, along with a lot of other Wine problems I'd been having. Thanks, though!

---

