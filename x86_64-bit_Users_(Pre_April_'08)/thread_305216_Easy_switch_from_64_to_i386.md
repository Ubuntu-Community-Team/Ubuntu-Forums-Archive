---
title: "Easy switch from 64 to i386?"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ljamie82 on 2006-11-23
I am currently running edgy with the 64bit install...  I understand  problems arise from running a 64 bit os.. and for the most part i've been able to work out most of the problems I've had... but I have recently run into something I can't seem to solve, and i'm just kinda tired of always fighting with it so I'm gonna just go ahead and get back to the i386 version... question is do I have to install the os all over again from the disk... or is there something I can just type in and have it redownload what it needs to?

---

### Post by RAOF on 2006-11-23
No.  You need to install the OS all over again.  Pretty much **everything** is different.

---

### Post by factor on 2006-11-24
But question is, if i backup /home, /etc, /var and /usr/local, i install i386, and restore the backup, will everything work as before? or drivers will have to be installed, configurations of programs remade, etc?

thanks in advance for your help.

Regards.

---

### Post by incubus on 2006-11-24
factor

Make a backup for sure, but I think overwriting /etc with your backup is a BAD idea.  Take a case-by-case approach.  For instance, xorg.conf and fstab should work fine.  So should sources.list.  Test gradually.  Same thing for your /home directory.

As for drivers (modules), you probably have to install them again, but do backup the config files -- they may work as well.

By the way, apt-get keeps deb files on /var/cache/apt/archives/.  I don't think you'll need a backup of those (they are the 64bit packages).  : )

incubus

---

### Post by iggyboy on 2006-11-25
I was originally started with Kubuntu64 (Dapper Drake), but after using it for about 1 month I change to i386 version, due to similar problem like yours.

What i did was just overwrite the "/" root folder from the Installation CD and leave the "home" partition as it is. BTW... I always make sure my "home" directory is in another partition from the "/" root directory.

After i386 OS Installation, I fully install all the software i used previously in my 64bit Kubuntu and fully update everything to latest patch. (all this is done using Adept Manager).

After that I simply recreate my account to previous name and point it to my previous directory location. Oh.. yes, During the installation I use a dummy account (any account name others then the previously used name) for software installtions and OS updates.

Basically what I did was backed-up only the HOME directory and Installed i386 OS followed by instalation of all the software previously used and point back my user account to previous location in the Home directory.

The result was... like magical transformation from 64bits to i386. Only the OS engine changed from 64bits to 32bits all else remain the same. (All my desktop settings, preferrence, bookmarks, Kwallet passwords, partially downloaded torrents etc.)

p/s: Now i am planning to back to 64bits, already used the Kubuntu i386 for about 5 months. Since I think I'm a bit of Linux intermediate to advance user (fully converted to linux last 6 months) therefore i can manage any issues that i might face in 64bits. Finger cross :)

I planned to do the same as what i did before, for transformation from 32bits to 64bits.

:)
iggyboy

---

### Post by incubus on 2006-11-25
That was a cool experience, iggyboy.  Good that the configs are truly platform independent.

I guess whatever you do, the three most important lessons are: backup, backup, backup.

Good luck to you guys.

incubus

---

