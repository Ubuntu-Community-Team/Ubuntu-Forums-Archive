---
title: "installing 32 bit stuff on a 64bit machine"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by natman on 2007-05-05
Hi,
I am running feisty 64bit kubuntu and wanted to indstall a .deb i downloaded ( yahoo messenger ). I ran the following
[HTML]natman@natman-laptop:~$ sudo dpkg -i ./polymake_2.3-1_powerpc.deb
Password:
dpkg: error processing ./polymake_2.3-1_powerpc.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./polymake_2.3-1_powerpc.deb
natman@natman-laptop:~$ 
[/HTML]

Is there any way to get around this issue or is it up too yahoo?

---

### Post by zvacet on 2007-05-05
Well,maybe I´m wrong,but it seems that you downloaded powerpc.deb and you don´t run Mac.Find 64 bit version of file and you should be fine.

---

### Post by Kilz on 2007-05-05
> **natman said:**
> Hi,
I am running feisty 64bit kubuntu and wanted to indstall a .deb i downloaded ( yahoo messenger ). I ran the following
[HTML]natman@natman-laptop:~$ sudo dpkg -i ./polymake_2.3-1_powerpc.deb
Password:
dpkg: error processing ./polymake_2.3-1_powerpc.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./polymake_2.3-1_powerpc.deb
natman@natman-laptop:~$ 
[/HTML]

Is there any way to get around this issue or is it up too yahoo?

As said above, you installed the powerpc version. You can look for a 64bit version, but I believe there is only the i386 one. [Take a lookin the sticky ]("http://ubuntuforums.org/showthread.php?t=191205")for information about forcing in i386 packages. Only do this with debs that install applications, never with libraries.
You might also want to look at jabber and the jabber-yahoo plugin that is in synaptic.

---

