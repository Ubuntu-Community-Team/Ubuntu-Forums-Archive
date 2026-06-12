---
title: "need some clarity about 64"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by i0h on 2005-10-15
Hi im kinda new to linux (been using shells and stuff in the past and experimented on my 486 :D)
and i installed ubuntu 5.04 hoary some weeks ago and i like it alot..

in 2 weeks i get new computer..  athlon64 3200+ venice 939

and ive read little in this forum(amd64users)  and i have noticed that all apps dont work in the 64 version..  and me dont like :/

is it a big change to go from hoary to breezy 64bit ?
it took me forever to get some things running in hoary.. but i finally made it..
and im affraid somethings wont work on 64.. :/

thanks in advance..

Ubuntu developers.. you rock :)

*former debian wannabe*

---

### Post by AndersAA on 2005-10-15
basically 32bit stuff wont work "out of the box", those include closed codecs, such as wmv, and flash atleast.

But you can install the i386 version of ubuntu and it'll work perfectly fine on and amd64, you just wont get the advantages of a small speed increase on the amd64 stuff.

---

### Post by brentoboy on 2005-10-15
split your drive into three partitions.
One for 32 bit ubuntu, one for 64 bit ubuntu and one for data

mount the data drive at /home for both distros, so that when you boot up, at least you have all your data from either environment.

Use 32 if you need it, and 64 as often as possible.  Either you will like it, or you will constantly have to switch back and forth.  If you dont end up liking 64, just run it 32 bit - there's nothing stopping you.  Most apps dont get much extra out of 64 bits anyway, becuase they are just ported from 32 bit source to begin with, very little code out there was originaly concieved with 64 bit processors in mind.

---

### Post by i0h on 2005-10-15
thanks for the replays.. then i shouldnt change to 64bit i think... maybe later when there will be more support for it..

if it runs as good in 32bit as in 64.. im good :)

---

### Post by brentoboy on 2005-10-15
the only reason I run it 64 is so that I can find possible bugs to that down the road the stuff will be stable when it is more mainstream.

and I like living on the edge.

---

### Post by qiezi! on 2005-10-15
[quote=brentoboy]split your drive into three partitions.
One for 32 bit ubuntu, one for 64 bit ubuntu and one for data

mount the data drive at /home for both distros, so that when you boot up, at least you have all your data from either environment.
[/quote]

How would you mount the data partition as /home for both distributions?? Do you do this at time of install, when doing the partitioning part or later after the install is complete?

---

### Post by brentoboy on 2005-10-15
install the first version (say 32) and leave a partition empty - dont even mount it - just to keep life easy.  It should be the same basic size as the one you are installing for the 32 install.

make a thrid partition with a all the size possible (give maybe 8 to 12 GB each for the other two, and leave all your leftovers for the data area)

in the mount option, connect it to /home
(Im guessing you know how to do that part, and you are only asking how to do it with a dual ubuntu scenario.)

Then, install the 64 breezy. when you get to the partitioning part, put it on the other partition, and dont even mount the first one. but put the data on /home

the second one will see the first one in grub when  it goes to setup grub for itself, and it will help you dual boot at that point.

with a large drive, you could do the same thing with another distro in the mix to.  I have an empty partition that I leave open to install mepis or something on that one if I feel the need to stray from ubuntu for a week.

---

### Post by qiezi! on 2005-10-16
Cool, that's great, thanks.  Should be able to do that no probs.

---

### Post by ikd69 on 2005-10-16
[QUOTE=i0h]Hi im kinda new to linux (been using shells and stuff in the past and experimented on my 486 :D)
and i installed ubuntu 5.04 hoary some weeks ago and i like it alot..

in 2 weeks i get new computer..  athlon64 3200+ venice 939

and ive read little in this forum(amd64users)  and i have noticed that all apps dont work in the 64 version..  and me dont like :/
*former debian wannabe*[/QUOTE]

Unless you depend extensively on wmv and flash-y stuff, then you may want to stay with the 32-bit version (i run it on an old PIII @ 800 MHz box and it's running fine).  But I would definitely move to a true 64-bit version and 5.10 rather than 5.04 since I find 5.10 more stable than 5.04

But, it's all about choices.

cheers,

ikd

---

### Post by i0h on 2005-10-16
im going to reinstall with 5.10.. but i use a 32bit ftp client (the only one i have found supporting implicit ssl)  i searched for atleast 10hours for one :>

what if i cant find the apps i use now in 64bit? :/

---

### Post by AndersAA on 2005-10-16
[QUOTE=i0h]im going to reinstall with 5.10.. but i use a 32bit ftp client (the only one i have found supporting implicit ssl)  i searched for atleast 10hours for one :>

what if i cant find the apps i use now in 64bit? :/[/QUOTE]

first of all, nobody should be using implict ssl (it's not a rfc standard, explict is), second, every single application connecting through tcp/ip can use it, by using for example stunnel (.org).

---

