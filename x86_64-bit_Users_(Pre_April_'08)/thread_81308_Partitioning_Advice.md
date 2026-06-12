---
title: "Partitioning Advice"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by robert-s on 2005-10-24
Hi. I'd like to install Ubuntu on my iBook G4 (933Mhz, 640Mb RAM and 40GB HD) alongside OSX but I'm not sure what kind of partitioning scheme to use. So I was just wondering what filesystems I should use. I'd like to be able to share the same home directory between Ubuntu and Mac OS X if possible.

Any suggestions?

---

### Post by Peter76 on 2005-10-24
Hi, you should probably make two 20 G partitions, one for OSX, formatted as hfs+, and the other formatted as free space( make this the first partition. The free space you can later partition in the ubuntu installer to suit your needs. About sharing the home directory, I don't know, it should be possible i think if you format the osx partition not as hfs+ but as unix file system, but it probably will need some playing around to get it working. Good idea though.

---

### Post by ssam on 2005-10-24
linux reads hfs+ fine. mac os x needs a driver installed to read ext2/3, [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) .

it is possible to share a home directory but not very recommended. you might get weird bugs. for example if you use different versions of the same program on each os, and the both try to use the prefferences same files.

if you want to share documents between the systems you could give each os 15gb, and make a 10gb space for shared documents.

you will also need a swap partition. this is virtual memory. on mac os x the virtual memory is kept in a hidden file. on linux it is usually done on a seperate partition. the recomended size is between 1 and 2 times the amount of ram you have, but if you have lots of ram then you may only need a small swap.

sam

---

### Post by robert-s on 2005-10-24
OK, thanks a lot for the replies. I think I'll just have seperate home directories in that case, and go with a 10GB partition both OSes can share.

Thanks again! ;)

---

### Post by gpogo on 2005-10-25
last I heard OS X Tiger(10.4.x) cannot use that ext2/3 driver. Only real way to share a partition is FAT.

 Good luck man

---

### Post by Netherfox on 2005-10-25
Does Mac OSX read ReiserFS alright? I prefer that anyway.

---

### Post by autocrosser on 2005-10-25
About the ext2/3 driver--You are correct--will not work with 10.4:( --waiting to see if he updates it........ReiserFS as far as I know is not readable by the Mac OS--best bet is to install 10.3 & use the ext2/3 driver--you can get it by searching Versiontracker.com or Sourceforge.com

---

