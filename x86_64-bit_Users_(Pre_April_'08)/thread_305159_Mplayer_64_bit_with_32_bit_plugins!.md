---
title: "Mplayer 64 bit with 32 bit plugins!"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by drews_blunted on 2006-11-22
I have created this thread in response to a post i read, that i cannot find at the moment, that said if you just compile mplayer from svn you can use 64 bit mplayer with 32 bit plugins! So far i have downloaded and 

./configure
make
sudo make install
sudo mv mplayer /usr/bin/mplayer

Im not sure if this is the correct way to do this? I am glad to say horever that when i went ahead and opened up mplayer it worked! And .wmv were playing perfectly in mplayer on Ubuntu x86_64. My only problem now is that i cannot figure out why there isnt an mplayer gui, i am somewhat unfamiliar with mplayer, so im not sure if its a command or an option when i built it. Does anyone happen to know this or know more about running 64 bit mplayer with 32 bit plugins from snv?

Ubuntu x86_64 Edgy Elf 6.10

---

### Post by RAOF on 2006-11-22
It's not using 32bit plugins; it's using native 64bit WMV3 code.  A better way to install this would be from my repsoitory (see sig), section "multimedia".  After adding one of those repositories, your mplayer packages should be automatically updated next time update-manager runs, or you can run ```
sudo apt-get update
sudo apt-get upgrade

```
to update immediately.

---

### Post by xstaticxgpx on 2006-11-23
> **drews_blunted said:**
> I have created this thread in response to a post i read, that i cannot find at the moment, that said if you just compile mplayer from svn you can use 64 bit mplayer with 32 bit plugins! So far i have downloaded and 

./configure
make
sudo make install
sudo mv mplayer /usr/bin/mplayer

Im not sure if this is the correct way to do this? I am glad to say horever that when i went ahead and opened up mplayer it worked! And .wmv were playing perfectly in mplayer on Ubuntu x86_64. My only problem now is that i cannot figure out why there isnt an mplayer gui, i am somewhat unfamiliar with mplayer, so im not sure if its a command or an option when i built it. Does anyone happen to know this or know more about running 64 bit mplayer with 32 bit plugins from snv?

Ubuntu x86_64 Edgy **Elf** 6.10
 its edgy **eft**, and this has been around for about 2 months

---

### Post by stiaszny on 2007-03-29
> **RAOF said:**
> It's not using 32bit plugins; it's using native 64bit WMV3 code.  A better way to install this would be from my repsoitory (see sig), section "multimedia".  After adding one of those repositories, your mplayer packages should be automatically updated next time update-manager runs, or you can run ```
sudo apt-get update
sudo apt-get upgrade

```
to update immediately.

I followed those instructions, and I get this:

root@chicago:/home/stiaszny/download# apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
E: Broken packages

Why doesn't mplayer come defacto with edgy? It was in dapper... or is this a 64-bit issue?

---

### Post by Kilz on 2007-03-29
> **stiaszny said:**
> I followed those instructions, and I get this:

root@chicago:/home/stiaszny/download# apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
E: Broken packages

Why doesn't mplayer come defacto with edgy? It was in dapper... or is this a 64-bit issue?

The post you are replying to is 5 months old. It isnt a good idea to reply to threads so old.
Mplayer, and the library's your message says are needed are available for Edgy, but they are in the multiverse repository. Are you sure you have enabled it?

---

