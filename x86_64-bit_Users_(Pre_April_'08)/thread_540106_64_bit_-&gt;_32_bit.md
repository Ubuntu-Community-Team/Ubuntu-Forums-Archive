---
title: "64 bit -&gt; 32 bit?"
date: 2007-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dub Throatflex on 2007-09-01
i've installed 64-bit ubuntu version (7.04) and i want to migrate to 32-bit version. is there any way to do it without reinstalling system?:(

sorry for poor english:)

---

### Post by meindian523 on 2007-09-01
install in a different partition......

---

### Post by meindian523 on 2007-09-01
> **meindian523 said:**
> install in a different partition......

if you want to preserve your 64 bit system or otherwise just install over it.Just my 2c,if you want to wait for more experienced users,please wait around.

---

### Post by mckryptyk on 2007-09-01
Hello I understand that you want to migrate data from 64 bit to 32 bit correct?

If you have your /home folder on a separate partition then it will be easy.

For example, say you have this: (it won't be exactly the same)

partition 1: /dev/hda1 / (root)
partition 2: /dev/hda2 /home 

I will be much easier.
 If you are unsure of what you have please you this command from the terminal:

```
sudo fdisk -l
```

It will give you a list. Please post it here.

Cheers.

---

### Post by Dub Throatflex on 2007-09-01
> **mckryptyk said:**
> Hello I understand that you want to migrate data from 64 bit to 32 bit correct?

If you have your /home folder on a separate partition then it will be easy.

For example, say you have this: (it won't be exactly the same)

partition 1: /dev/hda1 / (root)
partition 2: /dev/hda2 /home 

I will be much easier.
 If you are unsure of what you have please you this command from the terminal:

```
sudo fdisk -l
```

It will give you a list. Please post it here.

Cheers.

I don't wann aa migrate data, i wanna change 64 bit system to 32 bit without reinstalling it.

sorry again for poor english.

---

### Post by selcuk_kucuk on 2007-09-01
which one is better to use 32 bit or 64 bit ?

I mean speed and security ?? and is it right that some programs wouldnt run on 64 bit?----

may you please inform me ?? if there is no difference to run programs on 64 bit it would be very good to run theme faster on 64 bit if possible :confused:

---

### Post by John.Michael.Kane on 2007-09-01
First it's not proper to threadjack.

With that said I will answer your questions section by section.

> **selcuk_kucuk said:**
> which one is better to use 32 bit or 64 bit ?

As said many time before.Anything that can be done on 32bit ubuntu can be  accomplished using 64bit ubuntu, 32bit or 64bit is not about which one is better, As they both have their problems/issues. 

What I , and many 64bit users would suggest, if you want to try 64bit ubuntu is to use it for thirty days without rebooting into 32bit ubuntu, and make use of the guides made for 64bit,Which will allow you to see for your self if it's worth it or not.  

> **selcuk_kucuk said:**
> I mean speed and security ?? and is it right that some programs wouldnt run on 64 bit?----

Security on 64bit is not different then that on 32bit, and requires work by the end user. Using one architecture over the other does not make for stronger security. For a simpler explanation read more at the following link [**Security on Ubuntu**]("http://www.psychocats.net/ubuntu/security").

> **selcuk_kucuk said:**
> may you please inform me ?? if there is no difference to run programs on 64 bit it would be very good to run theme faster on 64 bit if possible :confused:

For further information there's a sticky thread here [**Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)**]("http://ubuntuforums.org/showthread.php?t=368607") that explains/answers most if not all your questions.

---

### Post by John.Michael.Kane on 2007-09-01
> **Dub Throatflex said:**
> I don't wann aa migrate data, i wanna change 64 bit system to 32 bit without reinstalling it.

sorry again for poor english.

You best bet is to first see if your home folder is on a separate partition, As said by the other poster. If that is the case then you should be able to simply install over your root partition in which case ubuntu should pick up your home folder.

However should the above not be the case, and your indeed running a lone partition then you will have no other option other then to back what is important to you, and reinstall.

---

### Post by Kilz on 2007-09-01
> **Dub Throatflex said:**
> i've installed 64-bit ubuntu version (7.04) and i want to migrate to 32-bit version. is there any way to do it without reinstalling system?:(

sorry for poor english:)

The question no one has asked is Why?

Why do you want to move from a 64bit install to 32bit?

---

### Post by mckryptyk on 2007-09-01
Here is what I think you need to do, assuming everything is on one partition:

1) Boot up amd64-livecd. 
2) Mount existing partion that has home on it.
3) Wipe out everything except for your home folder.
4) Unmount the partition.
5) Proceed with install from livecd, when it comes to partioning menu, make sure not to format the partition with /home on it.
6) Reuse existing username and password for login details.
7) Reboot.

I think this should cover it. I'll let the others here cover the details right now.

I need to get some sleep :)

Cheers.

---

### Post by cjazz on 2007-09-01
I may be misreading this discussion, but ...

Everybody's been suggesting reinstalling the system while retaining the data in the home partition. This is valuable information, but I believe (correct me if I'm wrong) that the OP asked if it was possible to migrate from 64-bit to 32-bit *without* reinstalling.

I may be wrong, but I believe the simple answer to that is: no.

---

### Post by kuja on 2007-09-01
> **cjazz said:**
> I may be misreading this discussion, but ...

Everybody's been suggesting reinstalling the system while retaining the data in the home partition. This is valuable information, but I believe (correct me if I'm wrong) that the OP asked if it was possible to migrate from 64-bit to 32-bit *without* reinstalling.

I may be wrong, but I believe the simple answer to that is: no.

The short answer is no. The long answer is also no.

---

### Post by saru411 on 2007-09-01
> **Kilz said:**
> The question no one has asked is Why?

Why do you want to move from a 64bit install to 32bit?

i think this is the question needed answering. the best responce will come directly from the answer. AND NO YOU CAN NOT UPGRADE/DOWNGRADE 32bit to 64bit or vise versa.

---

### Post by mckryptyk on 2007-09-03
Maybe it's just me, but I'm pretty sure that the question of "Can I migrate from 64 to 32 or vise versa without anything but -- "Insert Automagical Solution" -- has been done before.

That's probably why most people in this thread started offering practical solutions to the problem (such as flattening and reinstall while preserving /home).

I understand that people don't have or don't really want the answer "No".

I just wish more people would learn the habit of "Using The Friendly Search Engine".

Cheers.

---

### Post by Kilz on 2007-09-03
> **mckryptyk said:**
> 

I just wish more people would learn the habit of "Using The Friendly Search Engine".

Cheers.

Heck Id be happy if someone tried an unfriendly search engine. The amount of posts on the top 10 subjects has got to be in triple digits each day on the forum.

---

