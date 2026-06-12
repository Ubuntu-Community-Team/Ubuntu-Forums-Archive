---
title: "Using 32 bit programs on a 64 bit system"
date: 2006-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Punisher on 2006-05-19
Hello all,

    I am trying to install the Macromedia Flash Player and libdvdcss2 on my Ubuntu AMD64 system and i keep running into walls.  I'm new to the LInux community and was wondering if anyone could help me with this? It would be greatly apperciated.

Punisher.

---

### Post by ubuntu_demon on 2006-05-19
Take a look at this thread :

[http://ubuntuforums.org/showthread.php?t=179286](http://ubuntuforums.org/showthread.php?t=179286)

In particular to this post :

[http://ubuntuforums.org/showpost.php?p=1033889](http://ubuntuforums.org/showpost.php?p=1033889)

If you insist on 64 bit (it won't be pretty) take a look here :

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

If you decide to go for 32 bit reinstall Ubuntu from an intel/x86 cd and after that install the k7 kernel by :
$sudo apt-get install linux-k7

---

### Post by Kilz on 2006-05-20
[QUOTE=ubuntu_demon]Take a look at this thread :

[http://ubuntuforums.org/showthread.php?t=179286](http://ubuntuforums.org/showthread.php?t=179286)

In particular to this post :

[http://ubuntuforums.org/showpost.php?p=1033889](http://ubuntuforums.org/showpost.php?p=1033889)

If you insist on 64 bit (it won't be pretty) take a look here :

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

If you decide to go for 32 bit reinstall Ubuntu from an intel/x86 cd and after that install the k7 kernel by :
$sudo apt-get install linux-k7[/QUOTE]


Just a few courious questions, Im looking for a better distro at the moment. The orignal question was one I was interested in.
Why would people who paid extra to buy a 64 bit prossessor chose to join a community that tells them to use a 32 bit os? 
Will Ubuntu ever officialy support running 32 bit programs on a 64 bit os like some other distros have?

---

### Post by ubuntu_demon on 2006-05-20
[QUOTE=Kilz]Just a few courious questions, Im looking for a better distro at the moment. The orignal question was one I was interested in.
Why would people who paid extra to buy a 64 bit prossessor chose to join a community that tells them to use a 32 bit os? 
Will Ubuntu ever officialy support running 32 bit programs on a 64 bit os like some other distros have?[/QUOTE]

IMHO 64 bit is mostly a marketing issue right now. 

AFAIK windows 64 bit is currently in the same situation regarding codecs as Ubuntu ... well a bit worse as they don't have chroot.

I've read something about someone wanting to make it easier. Might have been a spec or something. Can't remember where. Eventually it will be easier in Ubuntu but I don't have any idea when.

---

### Post by Kilz on 2006-05-21
Thanks for your reply, 
You are correct, Windoz isn't any better, but I don't like Windoz. I don't even have windowz installed. I'm currently using SuSE 10.0 64 bit. But I'm looking to try another distro or 2. I think that Linux has an upper hand at the moment in 64 bit Os's. It would be nice if 64 bit Unbutu was better at running 32 bit. Its becoming quite common that 64 bit distro's run 32 bit. I was surprised to find that this popular distro didn't have 32 bit support.  I did download the dapper 64 bit beta and liked the speed. 
64 bits may be a marketing tool to some. But if you like 3d modeling, 64 bit can be quite useful. The problem is that some programs have not developed 64 bit versions. So unless you have 32 bit support, you have very limited choices.

---

### Post by ubuntu_demon on 2006-05-21
[QUOTE=Kilz]Thanks for your reply, 
You are correct, Windoz isn't any better, but I don't like Windoz. I don't even have windowz installed. I'm currently using SuSE 10.0 64 bit. But I'm looking to try another distro or 2. I think that Linux has an upper hand at the moment in 64 bit Os's. It would be nice if 64 bit Unbutu was better at running 32 bit. Its becoming quite common that 64 bit distro's run 32 bit. I was surprised to find that this popular distro didn't have 32 bit support.  I did download the dapper 64 bit beta and liked the speed. 
64 bits may be a marketing tool to some. But if you like 3d modeling, 64 bit can be quite useful. The problem is that some programs have not developed 64 bit versions. So unless you have 32 bit support, you have very limited choices.[/QUOTE]
Yeah It would be handy to have better 32 bit support in 64 bit installations. 

I don't know how good the chroot solution is. But it is too complicated for most users see :
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

So at the moment I advice average desktop users to go for 32 bit (k7).

---

### Post by Kilz on 2006-05-21
I tried setting one up, and it is pretty hard. Maybe its something that could be added to a default 64 bit setup to make it easier.

---

### Post by ubuntu_demon on 2006-05-21
[QUOTE=Kilz]I tried setting one up, and it is pretty hard. Maybe its something that could be added to a default 64 bit setup to make it easier.[/QUOTE]
I totally agree. Let's hope it makes Edgy.

---

### Post by BoyOfDestiny on 2006-05-21
Erm... The situation is much different in Ubuntu than Windows.
For one you have around 18,000 64-bit packages at your fingertips. 
Windows doesn't have a plethora of 64-bit software AFAIK.

As for 32-bit, some binaries work with ia32 or lib32 stuff (for example OpenOffice.org is compiled for 32-bit).

As for a chroot, I have made a script that makes it trivial. Please see my signature (and please sticky the thread :) )

As for what I use it with, zsnes svn and firefox + flash (although I'm hoping to replace that with gnash soon)

---

### Post by Kilz on 2006-05-21
[QUOTE=BoyOfDestiny]Erm... The situation is much different in Ubuntu than Windows.
For one you have around 18,000 64-bit packages at your fingertips. 
Windows doesn't have a plethora of 64-bit software AFAIK.

As for 32-bit, some binaries work with ia32 or lib32 stuff (for example OpenOffice.org is compiled for 32-bit).

As for a chroot, I have made a script that makes it trivial. Please see my signature (and please sticky the thread :) )

As for what I use it with, zsnes svn and firefox + flash (although I'm hoping to replace that with gnash soon)[/QUOTE]

Altho it pains me to defend windowz. :-? In all honesty it only has a few driver problems. 32 bit programs for the most part run fine on 64 bit xp pro. There may not have a lot of 64 bit programs but it can run what 32 bit programs users want (along with spyware and viruses). But enough of defending the devil. As I said in a post above, I dont even have windowz on my computer, and I have no intention of ever adding one again.

Thanks for the info on the script, ill be looking into it. Im going to keep a dapper partition and play around with it. The speed is nice and who knows what I will learn. I didnt ditch M$ by giving up. As long as I can get cedega and firefox to run I will be happy.

---

### Post by jeradzan12 on 2006-05-26
Sorry everybody.  I screwed up my original post

---

### Post by jeradzan12 on 2006-05-26
[QUOTE=ubuntu_demon]Take a look at this thread :

[http://ubuntuforums.org/showthread.php?t=179286](http://ubuntuforums.org/showthread.php?t=179286)

In particular to this post :

[http://ubuntuforums.org/showpost.php?p=1033889](http://ubuntuforums.org/showpost.php?p=1033889)

If you insist on 64 bit (it won't be pretty) take a look here :

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

If you decide to go for 32 bit reinstall Ubuntu from an intel/x86 cd and after that install the k7 kernel by :
$sudo apt-get install linux-k7[/QUOT

Thank you for this info.  I am having all kinds of issues with the 64-bit kernel, although I am still a newbie to linux and ubuntu.  Most of the programs I use to not have 64-bit support, so I'd like to use that until all of them have support.  I am assuming with you talking about the k7 kernel that it is possible to run the 32 bit kernel with the amd 64 bit processor.  I also noticed you spoke of reinstalling Ubuntu.  I have a question about this.  My /home is on a separate partition, so I am not worried about losing that.  However I have Ubuntu set up with the themes and layout that suites my current taste which took me hours to get right (Login Manager, custom themes, etc.).  If I have to do a complete reinstall, is there any way to salvage these files and settings so that I can just copy them over to the new installation?  Would the locations of these files/settings be different from the 64-bit version?
Thanks again.

---

