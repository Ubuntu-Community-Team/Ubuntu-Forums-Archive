---
title: "upgrade"
date: 2009-04-07
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-04-07
Dear buddies,
I have recently downloaded jaunty jackalope BETA as iso file and converted it in to CD.Could any buddy tell me is it possible to upgrade intrepid 64 bit to jaunty 64 bit by using this CD in my system? if so, how?

---

### Post by _Purple_ on 2009-04-07
I am not using 64 bit distro but I think its possible. 
Go to system > administration > software sources and add CD as source. Then Type in terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by kpkeerthi on 2009-04-07
You'd need Ubuntu 'Alternate' ISO to upgrade from CD. You can, however, upgrade to 9.04 online:

1. Open a terminal and enter ```
update-manager -d
```
2. You should now be notified about a new release and just follow the onscreen instructions.

---

### Post by jayanramesh on 2009-04-07
Dear kpkeerthi,
I have done upgraded by the method as you mentioned last week but all crashed so I downloaded and made a CD.Now what I want is - upgrade  using my CD. Is there anyway?

Thanks

---

### Post by kpkeerthi on 2009-04-07
I suggest you do a clean install. Thats better.

---

### Post by jayanramesh on 2009-04-07
Dear _purple_,
I followed your instructions but I 've got the reply as 

> "jayanr@jayanr-com:~$ sudo apt-get update
[sudo] password for jayanr: 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324) jaunty/main Translation-en_IN
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324) jaunty/restricted Translation-en_IN
Reading package lists... Done
jayanr@jayanr-com:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  g++ g++-4.3 libstdc++6-4.3-dev
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
jayanr@jayanr-com:~$ 
 

---

### Post by jayanramesh on 2009-04-07
Dear kpkeerthi,
I have done that(clean install) also but I could not get softwares and codecs if I do the same.

---

### Post by jayanramesh on 2009-04-07
Hello any buddy -any help?

---

### Post by _Purple_ on 2009-04-07
> **jayanramesh said:**
> Dear _purple_,
I followed your instructions but I 've got the reply as

Which CD did you use?

---

### Post by kpkeerthi on 2009-04-07
> **jayanramesh said:**
> Dear kpkeerthi,
I have done that(clean install) also but I could not get softwares and codecs if I do the same.

How did you install your softwares and codecs earlier? It should not be any different in 9.04.

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Sylslay on 2009-04-07
I thinking than You will be able install the same package after whiele, when thay put them into repo,
About codec , thouse working great for me:
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

PS: Old pakckege are part of PAST TIME, new pakcege ara part of ewolution, Yours choice.

---

### Post by jayanramesh on 2009-04-07
Dear pals,
Is it possible to upgrade from intrepid to jaunty BETA from jaunty CD which I have made from downloaded iso image.If it can be done then  please tell me how?.

---

### Post by mhgsys on 2009-04-07
ehhhmz, 

Weren't you allready talking here?

[http://ubuntuforums.org/showthread.php?t=1118561](http://ubuntuforums.org/showthread.php?t=1118561)

---

### Post by jayanramesh on 2009-04-07
Dear _purple_,
I used 'Jaunty CD"

---

### Post by 3rdalbum on 2009-04-07
Jayanramesh: In order to upgrade your system in-place using the CD, you need the Alternate CD. If you can boot up your computer from the CD and use the Ubuntu live system, then you have the Desktop CD, not the Alternate CD.

On the mirror where you downloaded the Jaunty desktop CD, you just choose the ISO image that has the word "alternate" in its name.

Once you have the alternate CD, the procedure is actually pretty simple. Don't boot up from the disc, just insert it while your regular Ubuntu is running. The CD has a script called "cdromupgrade" or something like that. Run that in a terminal, and you'll get a GUI screen come up that will use the packages on the CD to upgrade your base system to Jaunty.

After that is finished, reboot. You can then enable the repositories in System > Administration > Software Sources (they may have been disabled during the upgrade). Upgrade any packages that still need upgrading, and that's it.

---

### Post by jayanramesh on 2009-04-07
Dear mhgsys,
Yes, but I didn't get anything.Could you hlp me to solve my problem?

---

### Post by jayanramesh on 2009-04-07
Dear 3rd album,
Thanks a lot.

---

### Post by mhgsys on 2009-04-07
You didn't get anything you say ?
I saw lot's of people trying to be helpful in the thread you started before.
Also, sometimes it takes a little time before you get the correct answers, time.. people need to think about your problem.  
Don't get me wrong, I'm not trying to letter you, 
I'm just kinda pissed of people start multiple threads about one topic.
It doesn't make it easier to help them that way.
Anyway; seems to me you got the solution, and I'm happy for that.



> **3rdalbum said:**
> Jayanramesh: In order to upgrade your system in-place using the CD, you need the Alternate CD. If you can boot up your computer from the CD and use the Ubuntu live system, then you have the Desktop CD, not the Alternate CD.

On the mirror where you downloaded the Jaunty desktop CD, you just choose the ISO image that has the word "alternate" in its name.

Once you have the alternate CD, the procedure is actually pretty simple. Don't boot up from the disc, just insert it while your regular Ubuntu is running. The CD has a script called "cdromupgrade" or something like that. Run that in a terminal, and you'll get a GUI screen come up that will use the packages on the CD to upgrade your base system to Jaunty.

After that is finished, reboot. You can then enable the repositories in System > Administration > Software Sources (they may have been disabled during the upgrade). Upgrade any packages that still need upgrading, and that's it.

---

