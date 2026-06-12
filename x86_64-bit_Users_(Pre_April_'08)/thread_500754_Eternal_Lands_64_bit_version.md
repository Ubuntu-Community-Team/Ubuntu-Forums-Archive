---
title: "Eternal Lands 64 bit version"
date: 2007-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by UncleAl on 2007-07-14
Hi all,

   I am posting here because I suspect that this might be a 64 bit
issue rather than a purely Eternal Lands issue.

I downloaded and and unzipped the el_linux_install_140.zip file from
the link on the Eternal Lands page, and followed the setup instructions:

Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create. 

Incidentally the zip file DOES have a base directory 'el_install'.

I unzipped to /home/xxx/el_install

chmodded el.x86_64.linux.bin (rather than el.x86.linux.bin)
and exectued it. At this point I got a segfault error.

in /home/xxx/.elc is a file error_log.txt with content:

Log started at 2007-07-14 09:36:37 localtime (CDT)

[09:36:37] Error: Can't open file "/home/xxx/.elc//el.ini"

I went ahead and edited the el.ini file setting #data_dir to

#data_dir = /home/xxx/el_install

(note that what I think of as the usual convention of commenting
lines is reversed; any line WITHOUT a '#' at pos 0 is a comment)

reran el.x86_64.linux.bin, got another segfault. Starting to worry now...

there is now a copy of el.ini in /home/xxx/.elc; I edit the #data_dir in
that copy to point to /home/xxx/el_install and rerun el.x86_64.linux.bin.
still segfaulting.

I have tried several variations on the above to no effect.

Has anyone already dealt with this?
Any suggestions?

Thanks,
UncleAL

---

