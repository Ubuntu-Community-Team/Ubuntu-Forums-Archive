---
title: "Can't get ia32-libs to install"
date: 2009-09-15
forum: x86 64-bit Users
---

### Post by Acephali on 2009-09-15
[SIZE=2]I've been trying to install the ia32-libs.  When tried through Synaptic I get the following error:[/SIZE]
 

 [SIZE=2]		W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following [/SIZE] 
 [SIZE=2]		signatures couldn't be verified because the public key is not [/SIZE] 
 [SIZE=2]		available: NO_PUBKEY 9AA38DCD55BE302B [/SIZE] 
 [SIZE=2]		NO_PUBKEY 4D270D06F42584E6[/SIZE]
 

 [SIZE=2]So, I went to the applicable website to get the key file and tried to inject it into Synaptic.  It didn't work.  Probably something that's obvious to most of you.  Failing this, I decided to try installing the package manually.  Where I got the following message:[/SIZE]
 

 [SIZE=2]Reading package lists... Done [/SIZE]
 [SIZE=2]Building dependency tree        [/SIZE]
 [SIZE=2]Reading state information... Done [/SIZE]
 [SIZE=2]E: Couldn't find package ia32-libs [/SIZE]
 

 [SIZE=2]I entered the ftp site ([ftp.de.debian.org/debian]("ftp://ftp.de.debian.org/debian") lenny main) into the sources.list.  Rebooted the system and tried each approach again with the same results.[/SIZE]
 

 [SIZE=2]I've tried to clean the local cache using 'sudo apt-get clean.'  No luck.  I've also tried to reinstall the installed packages thinking something might be corrupt and holding up the process.  Still didn't work.  I've searched many websites and forums for about 3 days now and can't find anything that seems to be applicable.  In my mind, my next recourse is to do a complete re-install of the OS.  [/SIZE] 
 

 [SIZE=2]Before I do this though, could someone please give me some guidance.[/SIZE]
[SIZE=2]Thanks and Cheers.
[/SIZE]

---

### Post by mperry on 2009-09-15
The line you added to /etc/apt/sources.list is for Debian Lenny and I don't think that's necessary. You may need to add a few additional repositories but they are all listed in Software Sources I believe. I'd remove that listing in /etc/apt/sources.list and open up Software Sources. On my x64 build, it shows up like this:

mperry@mikesnas:~$ apt-cache search ia32-libs
ia32-libs - ia32 shared libraries for use on amd64 and ia64 systems

This is on a ubuntu server box running 8.10 or so. I'd remove the entry you added for Debian Lenny, open up Software Sources and check what's included and have it reload your sources.list file. Then for safety's sake, open a terminal and do "apt-get update; apt-get install ia32-libs". I don't recall if I had to add anything to my sources.list file to make it show up. I also have the Jauntry x64 loaded on desktop systems.

I don't think a complete reinstall is necessary and I don't think you have to reboot when changing the /etc/apt/sources.list file.

---

### Post by Acephali on 2009-09-15
mperry: I tried as you suggested.  As a matter of fact, before I added the site in question (lenny) I played with the Software Sources package.  I forgot to list this in my 1st thread.

I obtained the 'lenny' site from the ia32-libs Ubuntu website so I thought it would work.  Don't know if they're having a prob with the server or what.  Makes me wonder if other's have the same prob when they enter the site in the sources.list.  Oh well.

I also tried switching the servers in the Software Sources package from 'Main' to 'Servers in U.S.'  Didn't really think this would do anything, but...

Anyway, I get the same error - Can't find package. 

It's encouraging that you don't think I need to re-install the system.  Although it wouldn't be a hard process, I really don't want to rebuild what I've accumulated or do a lenghty backup.

Guess I'll wait until the answer comes along.  Thanks much for your suggestions though.  Every little thing helps to narrow it down.
Cheers.

---

### Post by oldos2er on 2009-09-15
Check Software Sources (System, Administration), and make sure the universe repository is enabled.

---

