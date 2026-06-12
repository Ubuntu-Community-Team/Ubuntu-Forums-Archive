---
title: "Kubuntu AMD64 Openoffice2 users please help"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Navyblue on 2005-11-25
Hi,

If you fit the description in the title, please help me answer the following question.

Is your /usr/lib/openoffice2/program/soffice.bin a binary file or a bash script? If it is a bash script please post the content.

Thank you very much.

---

### Post by metoo on 2005-11-25
Funny question.

KDE - konqueror - /usr/lib/openoffice2/program/soffice.bin - right click - open with... - kate:

------------------------------
#! /bin/sh

GTK_PATH=/usr/lib32/gtk-2.0 LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 exec "$0".real "$@"
-----------------------------

Appears to be a script.

---

### Post by jyhelle on 2005-11-27
well, here soffice.bin is an executable binary ("ELF" at the beginning of kate displayed garbage), while soffice. in the same folder, is a script

---

### Post by jsubl2 on 2005-11-27
file  /usr/lib/openoffice2/program/soffice.bin
/usr/lib/openoffice2/program/soffice.bin: Bourne shell script text executable

#! /bin/sh

GTK_PATH=/usr/lib32/gtk-2.0 LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 exec "$0".real "$@"

---

### Post by metoo on 2005-11-27
I should have mentioned, that I run the final from people.ubuntu.com and not the one with which breezy is coming.
Maybe this explains the difference?

---

### Post by Navyblue on 2005-11-29
Thanks for your reply guys.

metoo,

It's not funny, my soffice.bin actually dissapeared after uninstalling some packages (does not come with official Kubuntu), and renders my ooffice2 unable to start.

jyhelle,

Is yours a 64 bit Kubuntu?

I found out that in my 32 bit Kubuntu where the ooffice2 looks correct, soffice.bin is a binary file.

In my 64bit Kubuntu where the ooffice2 look gnomish, I found that soffice.bin is a script with the content identical to what jsubl2 posted. And the /usr/lib32/libpangohack.so.0.0 that it is pointing does not seem to exist in any package.

So I thought somehow it got corrupted making it look gnomish, but later I foind out that a freshly installed system has this flaw naturally.

---

### Post by jyhelle on 2005-12-02
[QUOTE=Navyblue]
jyhelle,

Is yours a 64 bit Kubuntu?

I found out that in my 32 bit Kubuntu where the ooffice2 looks correct, soffice.bin is a binary file.

In my 64bit Kubuntu where the ooffice2 look gnomish, I found that soffice.bin is a script with the content identical to what jsubl2 posted. And the /usr/lib32/libpangohack.so.0.0 that it is pointing does not seem to exist in any package.

So I thought somehow it got corrupted making it look gnomish, but later I foind out that a freshly installed system has this flaw naturally.[/QUOTE]

(sorry for the delay, I was on a business trip)
My system is an AMD64, with Kubuntu installed straight from a downloaded DVD (all partitions erased at install time)

Since I previously used Mandrake, I never really used Gnome, so I am not qualified to describe my oo2 as gnomish or kde'ish, let's say it looks more or less the same as I used under Mandrake ...

---

### Post by Navyblue on 2005-12-02
No problem at all.

One obvious aspect to note is ooffice2 does not make use of the KDE colour scheme and font. It is especially obvious to me as I use very dark colour theme and ooffice2 just appear as normal grey.

By installing the ia32-libs-gtk package sort of helped a bit. It made ooffice2 uses GTK widget and thus get translated to QT theme by KDE.

---

### Post by jyhelle on 2005-12-02
[QUOTE=Navyblue]
One obvious aspect to note is ooffice2 does not make use of the KDE colour scheme and font. It is especially obvious to me as I use very dark colour theme and ooffice2 just appear as normal grey.
[/QUOTE]

I see what you mean, and yes my oo2 must be gnomish (booohh !) as e.g. the toolbar uses a white-to-grey progressive background, and menu font is much bigger and with thinner lines than "regular" KDE apps...

---

### Post by Navyblue on 2005-12-03
Btw, installing ia32-libs-gtk package would make it a little more decent looking. It makes ooffice2 uses gtk widgets and KDE would translate it to QT ones.

---

### Post by jyhelle on 2005-12-04
[QUOTE=Navyblue]installing ia32-libs-gtk package would make it a little more decent looking.[/QUOTE]
I just tried and yes it looks more "integrated" with the rest of the system.
Thx

---

### Post by Navyblue on 2005-12-05
You are welcome. :)

---

### Post by manzuk on 2005-12-07
Oh, I love u so much!!! I've been looking for a thread about this for weeks!
I installed the package ia32-libs-gtk and now Ooo looks actually more integrated. However, it'd be great if Ooo worked with kde as it seems to work with gnome :???: 
Love kubuntu! Bye!

---

