---
title: "Failure to boot from CD"
date: 2006-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by _TK_ on 2006-07-28
Hi,

I'm new to Linux and a friend said that Ubuntu was the best to get so I downloaded the CD image (6.06) of the 64 bit version (as I have an AMD 64 FX-55). I would love to dual boot between windows XP and Ubuntu. 

There is just one problem... When trying to boot off the cd there is a message like 'Please insert boot media and press any key or restart' I dont know if theres a problem or if I'm just being stupid about something. I have checked the MD5's from the download source against those of the file and they appear to match.

I have no idea as to the problem and would apreciate any help. 

Thanks

_TK_

---

### Post by Mike_N on 2006-07-28
1st: Did you "burn image to disk" or burn the ISO as a data CD?
2nd: Is your BIOS set to boot from CD before Hard Disk?

---

### Post by _TK_ on 2006-07-28
Answers:

1st: I extracted the ISO and then just burnt the files to the cd using XP's burning software

2nd: The BIOS is set up to boot a: > CD > Hard drive

---

### Post by s_h_a_d_o_w_s on 2006-07-28
Firstly, set up your BIOS to boot from cd (as first boot device), if you haven't already.

Secondly, boot-up. you should get the message you were talking about. Something like "Please insert boot media" or "Boot media not detected, please insert CD and press Enter to continue".

Thirdly, Insert the CD and press enter. There you should boot into the installe, though I reccomend using the live installer as it features the install option, through a GUI and is much faster.

[COLOR="DeepSkyBlue"]Troubleshooting:[/COLOR]

Check that:

You burned the cd as a .iso, and not the dump the .iso on the cd. If you are in windows, on your cd burning software, click "burn cd image" , that should do it.

You burned the cd at the lowest speed possible, and make sure the cd has no scratches.

Your cd drive is functioning properly.

Hope that helps :-)[COLOR="DeepSkyBlue"][/COLOR]

---

### Post by _TK_ on 2006-07-29
Hey thanks ... it seemed to work! I guess I hadn't burnt the CD correctly

---

### Post by ntgooroo on 2006-07-29
I got this message before, too.  I had two DVD/CD ROM drives.  They were set to cable select.  I read some where to set them one to Master the other to Slave.  This fixed my problem.

---

