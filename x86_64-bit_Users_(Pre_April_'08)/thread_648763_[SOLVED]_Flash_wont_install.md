---
title: "[SOLVED] Flash wont install"
date: 2007-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luis Macias on 2007-12-24
Hi, im  having trouble installing flash plug in firefox, if i search in synaptic it apperas to be installed, but when i opne a page with flash content the up bar apperas asking me to install the plug in, but then it searches and says there is no suitable plug in.... anyone knows why is that?? in an earlier ubuntu install it gave me to results and was very easy to install.
Thanks and happy holidays !

----

Ok, suddenly it plays videos on youtube, but seems like its not usign the nonfree plugin, but the other one, cause the bat in the video and time left are all over each other

---

### Post by Kobalt on 2007-12-24
Hello,

There is currently a bug in installing Flash on Ubuntu 7.10 / 64bits. You can use [Kilz's script]("http://ubuntuforums.org/showthread.php?t=476924") to get it working the easy way.

Cheerio !

---

### Post by soxs on 2007-12-24
I have the sameproblem, but i got around that when i try to install flshplugin-nonfree on x86_64 ubuntu I get a md5sum mismatch, so the install is actually canceled, but the gtk dialog tells install successfully completed.

The script did NOT work for me... so, any ideas how to cancel the md5sum checksum or get the correct sum?

---

### Post by John.Michael.Kane on 2007-12-24
> **soxs said:**
> I have the sameproblem, but i got around that when i try to install flshplugin-nonfree on x86_64 ubuntu I get a md5sum mismatch, so the install is actually canceled, but the gtk dialog tells install successfully completed.
Currently the known ways around this issue are.
1) [Flash 9 install script for AMD64 (nspluginwrapper)]("http://ubuntuforums.org/showthread.php?t=476924")
2) [Howto Install 32 bit Firefox with Flash]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")
3) [Workaround for adobe flash problem]("http://ubuntuforums.org/showthread.php?t=639029")
4) [Bug #173890 flashplugin-nonfree md5sum mismatch support thread]("http://ubuntuforums.org/showthread.php?p=3929669")

> **soxs said:**
> The script did NOT work for me... so, any ideas how to cancel the md5sum checksum or get the correct sum?
There is no way to get the cancel the md5sum. The md5sum check is used to verify the integrity of the file, As well as to verify the version.

Also should Kilz script or any of the known methods yield no joy. At the very least please post the issues you are having with these workarounds in their respective threads.

---

### Post by soxs on 2007-12-25
Ok, I found a site which gave me .deb packages which work, I've attached them bove and it works for me.

---

### Post by Luis Macias on 2007-12-25
Script didnt work for me, but thanks.
About the deb, it says it installs, but the problem is that when i see videos or flash content they are all wrong, buttons inside the video, stuff like that. I think  the problem is that i have installed the free plugin and that one doesnt work so good, beacuse in an earlier install of gutsy i installed the nonfree from the beggining, but this time i wanted to try the free one, So anyone can tell me how to compeletely uninstall the plugins, so then trying to install the nonfree one? And thanks for helping me

---

### Post by Tyke91 on 2007-12-25
the problem is indeed with the free gnash plugin.

just go to synaptic, search for gnash, and mark it for complete removal. then just make sure the non-free plugin is installed :D


just tried it and it worked for me.

---

### Post by Kilz on 2007-12-26
> **Luis Macias said:**
> Script didnt work for me, but thanks.
About the deb, it says it installs, but the problem is that when i see videos or flash content they are all wrong, buttons inside the video, stuff like that. I think  the problem is that i have installed the free plugin and that one doesnt work so good, beacuse in an earlier install of gutsy i installed the nonfree from the beggining, but this time i wanted to try the free one, So anyone can tell me how to compeletely uninstall the plugins, so then trying to install the nonfree one? And thanks for helping me

When you try multiple versions of flash you create conflicting plugins. The number one reason for the script not working is the files of the failed attempts left in the plugin folders.

---

### Post by Luis Macias on 2007-12-27
> **Tyke91 said:**
> the problem is indeed with the free gnash plugin.

just go to synaptic, search for gnash, and mark it for complete removal. then just make sure the non-free plugin is installed :D


just tried it and it worked for me.

Thanks a lot!!! now its working perfectly!

---

### Post by crjackson on 2007-12-27
> **Kilz said:**
> When you try multiple versions of flash you create conflicting plugins. The number one reason for the script not working is the files of the failed attempts left in the plugin folders.

ops, posted in wrong thread.  Sorry...

---

