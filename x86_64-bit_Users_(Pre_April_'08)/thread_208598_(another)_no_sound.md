---
title: "(another?) no sound"
date: 2006-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2006-07-03
Ok, this was working at one point, but I did a reinstall to try 64bit and the sound didn't work.  I thought maybe this was isolated to 64bit so I tried 32bit and still no sound. 

I tried sudo alsamixer and had values for all entries, but still no luck (this was from scouring these forums to see some suggestions).

Has anyone gotten this to work easily?   What happened on 6.06 that things got messed up?

Thanks,
linuxted :confused:

---

### Post by Kilz on 2006-07-03
[QUOTE=linuxted]Ok, this was working at one point, but I did a reinstall to try 64bit and the sound didn't work.  I thought maybe this was isolated to 64bit so I tried 32bit and still no sound. 

I tried sudo alsamixer and had values for all entries, but still no luck (this was from scouring these forums to see some suggestions).

Has anyone gotten this to work easily?   What happened on 6.06 that things got messed up?

Thanks,
linuxted :confused:[/QUOTE]
[Have you seen this page yet?]("https://help.ubuntu.com/community/DebuggingSoundProblems")

---

### Post by TripleE on 2006-07-03
[QUOTE=linuxted]Ok, this was working at one point, but I did a reinstall to try 64bit and the sound didn't work.  I thought maybe this was isolated to 64bit so I tried 32bit and still no sound. 

I tried sudo alsamixer and had values for all entries, but still no luck (this was from scouring these forums to see some suggestions).

Has anyone gotten this to work easily?   What happened on 6.06 that things got messed up?

Thanks,
linuxted :confused:[/QUOTE]

I had to use Master Surround to adjust my volume (it was muted) in gnome.  You will have to go to Edit -> Preferences in Volume Control.  Master did not work at all for me. 

If that does not work, look for any muted connections and try to unmute them and adjust the volume. I always unmute all of the options for my sound and turn them up half way and play music. Once I can here it I start muting the options that I do need.

_____________
AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16

---

