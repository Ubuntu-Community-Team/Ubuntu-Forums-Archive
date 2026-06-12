---
title: "Java Error J2re1.4"
date: 2007-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zander_Z on 2007-01-31
Hey there, I'm having an error whenever I try to download a package or install java.

E: The package j2re1.4 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


That's the error, I was wondering if anyone had the slightest idea what's going on and how I can fix it?

---

### Post by phossal on 2007-01-31
Do you need an older version of Java? Either way, you can use the link in my signature to install it. If you have troubles, just respond in this thread.

---

### Post by kuja on 2007-01-31
That's a rather odd looking apt error, try this:

sudo apt-get clean
sudo apt-get update
sudo apt-get -f install

---

### Post by angryfirelord on 2007-02-01
Is it just the java package giving you trouble, or apt-get itself?

I recommend installing the sun-java5-jre or sun-java6-jre package instead.

---

### Post by Zander_Z on 2007-02-04
When I run your Sudo commands, it still gives me the first error I posted "E: The package j2re1.4 needs to be reinstalled, but I can't find an archive for it." I'm going to try downloading the j2re ver6 and see what happens. Thanks for all the help!

---

### Post by ben1400 on 2007-02-17
Hi, I am getting exactly the same error as Zander_Z.  I am very new to this OS, I am just trying to get Java & Flash working on my installation (6.10 AMD64).

I don't know if I need an older version of Java.  :( 

I've tried running kuja's code:
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install

I still get the same error as Zander_Z.:( 

I've no idea if it is just the java package giving me trouble, or apt-get itself. :confused: 

I understand that perhaps i will be unable to get Java running on Firefox64 and have tried installing Firefox32 :)  following the instructions at: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firefox32_in_AMD64](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firefox32_in_AMD64)

The first command:
sudo aptitude update

seems to work fine, but the second command (sudo aptitude install ia32-libs gsfonts alsa-oss) brings up the reply below:

 
dad@Ann-Marie:~$ sudo aptitude install ia32-libs gsfonts alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  lib32gcc1 lib32stdc++6 lib32z1 libc6-i386 
The following packages have been kept back:
  libmagick9 
The following NEW packages will be installed:
  alsa-oss ia32-libs lib32gcc1 lib32stdc++6 lib32z1 libc6-i386 
0 packages upgraded, 6 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 53.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the j2re1.4 package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

Aha! another  j2re1.4 error message!:mad: 

I hope this all makes sense to you.:) 

Help!

---

### Post by ubuntwerreulover0.023.231 on 2007-02-27
E: I wasn't able to locate a file for the skype package. This might mean you need to manually fix this package. (due to missing arch)



 My problem like yours but with a different program it won't let me install any thing please help Im thinking of reinstalling ubuntu.

---

