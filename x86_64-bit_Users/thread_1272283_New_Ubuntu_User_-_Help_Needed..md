---
title: "New Ubuntu User - Help Needed."
date: 2009-09-22
forum: x86 64-bit Users
---

### Post by napsterdj on 2009-09-22
Hello ,
I just installed the latest Ubuntu 9.04 today and I'm having a string of issues. 

I'm sorry for the random topic posted as I dint know where to start .

I'm running on a x86_64 bit architecture . I partioned my HDD and installed UBUNTU and everything seemed to work normal. 

1. I dont get to hear anything when I play MP3's . I did hear drums sound when it logged in but nothing else. I tried running test by going to System > Preferences > Sound , but the test keeps running forever. 

2. And also the visualisation on the "Movie player" and the videos which play run very very slow. I can see the loading symbol up and running all the time when i try to play videos or mp3's. It did ask me to update for 2 files and i did and it still dint seem to work. 

3. Whenver i try to update my flash player for firefox browser , the files get installed and then it says wrong architecture "i386" ** i'm not sure though , but it was something like that . I cross verified the version i wanted to download "*.deb" file for Ubuntu 8.04+ onwards but it still said "wrong architecture" . 


My question is , did i make a mistake installing the Ubuntu for an x64 system or is there a way to solve all these problems ?? 

I've used fedora in the past and I have very very limited knowledge working with Linux. I dint know where to start as most of the places in the forums a lot of technical jargons were used and I found it hard to understand and interpret it . 

Kindly help me out :(

---

### Post by lisati on 2009-09-22
For the flash problems, have a look at the Applications->Add/Remove menu. This has some plugins to help with playing flash, and will usually use the "correct" 64-bit version.

---

### Post by napsterdj on 2009-09-22
And i just found that I had downloaded the copy "**ubuntu-9.04-desktop-i386**" !!! 
 
I missed the 32/64 bit options below the Download button.

Now do i stick to this version or install the 64 bit version ? 

Also i need to know which would be the best version (8.04 or 9.04) to run on my x86_64 system ?

---

### Post by timgood on 2009-09-22
To play MP3's you will need to have the correct codecs installed. There is an easy way to do this: open System/Administration/Synaptic Package Manager and search for package called Ubuntu Restricted Extras. Installing this will give all all the codecs you need to play multimedia files on your PC.

If you have more than 3GB of RAM then the 64 bit version will see it all. If not you will not see much of an advantage but see other threads in this forum about the advantages/disadvantages of 64 bit. I run 64 bit and love it.

---

### Post by Guy Sibley on 2009-09-22
for the flash problem try:
 
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

(also, I don't believe Ubuntu comes with pre-loaded mp3 compatability.  I could be wrong but I remember having to install some extra packages for my mp3's to work.)
I hope this solves your problem.
-Guy

---

### Post by ursaminor on 2009-09-22
You can run a 32-bit on a 64-bit system, but if want to take advantage of the 64-bit download the 64-bit version. I run 64-bit myself and its just fine.

---

### Post by oldos2er on 2009-09-22
There is a script here [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938) to install 64-bit Flash.

---

### Post by Guy Sibley on 2009-09-22
Hi again, would someone help me clarify the difference between 64bit n 32bit flash?  I wasn't aware of this all I installed was flashplugin-nonfree.  It works fine on my 64 bit jaunty.

---

