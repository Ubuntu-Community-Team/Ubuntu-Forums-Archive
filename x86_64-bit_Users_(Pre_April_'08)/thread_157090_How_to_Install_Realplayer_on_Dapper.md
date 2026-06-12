---
title: "How to Install Realplayer on Dapper?"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan86corolla on 2006-04-08
Hello everybody,

As the title says, I'm trying to get Realplayer on Dapper. I am very new to linux, so I may be missing something obvious, but I am stuck. Here's what I've tried.

I downloaded Realplayer for 10.0.5.756 GOLD from here: [https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin]("https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin")
I entered this in the terminal:
```
$ chmod +x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
$ sudo ./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
```
But I got this message:
```
./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```
So I searched for libstdc++.so.5 on Synaptic (yes I have universe and multiverse enabled) but didn't find anything. I tried the same procedure with Realplayer 10.0.4.750 and also Helix 1.0.5.757 all downloaded from this site: [https://helixcommunity.org/project/showfiles.php?group_id=154]("https://helixcommunity.org/project/showfiles.php?group_id=154")
I am trying all of this on a fresh install of Dapper Flight 5. I have the latest updates as of today as well. I don't know too much about what i'm doing, but that sounds like an important library, right? I've only seen an issue with (the lack of) it when installing Realplayer though. So...any thoughts? Thanks in advance.

---

### Post by DutchR_PW on 2006-04-08
Install the libstdc++5 package:

sudo apt-get install libstdc++5

---

### Post by davidmaxwaterman on 2006-04-10
[QUOTE=DutchR_PW]Install the libstdc++5 package:

sudo apt-get install libstdc++5[/QUOTE]

Doesn't EasyUbuntu work? I've been trying to use it to install RealPlayer (plus other stuff), but it doesn't seem to install anything that I can tell.

How can I tell if it has worked or not?

Max.

PS. I'm on Breezy, I think.

---

### Post by seatea on 2006-04-11
I think EasyUbuntu is only for Intel or AMD  (i386?) based computers.

---

### Post by davidmaxwaterman on 2006-04-11
[QUOTE=seatea]I think EasyUbuntu is only for Intel or AMD  (i386?) based computers.[/QUOTE]

Actually, it does work on PPC.

However, I had to download the latest version from subversion. It might have worked before, but I found it difficult to tell.

Now I have fast graphics (OpenGL screensavers are quick), and the Deerpark icon has changed to Firefox; so I know it's worked.

However, some packages just aren't available for ppc (Skype, for example), and the EasyUbuntu is still under development, so things like RealPlayer doesn't get installed (if is will actually work).

IE YMMV :)

Max.

---

