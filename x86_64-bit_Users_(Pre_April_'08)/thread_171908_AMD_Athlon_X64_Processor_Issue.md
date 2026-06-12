---
title: "AMD Athlon X64 Processor Issue"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by vb_packets on 2006-05-07
The machine i am on now is not able to run linux. I get errors when i install it. Is what happens is it will load all the setup and install the files then im asked to remove my Ununtu 5.10 CD so it can continue finishing the setup.

The Black screen comes up and does a check on drivers and hardware but i see its not completing its setup and not finishing the Installation so i cant run it on this contraption!.

the box of my AMD x64 processor says:

AMD x64 tm with HyperTransport tm Technology
3000+
Socket 754

I also have a Nforce 4 MotherBoard so i am not sure if this will stop ubuntu working.

When it started to play up i see that it give a few errors on USB 2.1 Drivers and x64/something 

after those lines in the install if anything goes wrong it gives u options to type in commands but i dont want to play with anything until i can get some responses on the Ubuntu Forums.

Same happens with Kubuntu but it gets to the Boot Screen and freezes.

---

### Post by Ric95 on 2006-05-07
I had a similar problem. I needed to run (from windows command)   C:\>chkdsk/f
Have you reseached the install much?  I can tell you I also should have used the partitioner included in the Ubuntu disk because Partition Magic left my windows partition 'hidden'. (having Sfdisk burnt to cd fixed that)

---

### Post by vb_packets on 2006-05-07
i got a GeForce X800 GT graphics card also. i just booted into the live x64 Ubuntu CD and it said it couldent determine me graphic interface or something.. X Server. it asked if i wanted to go back and configure it but it crashed when it returned back to the black screen. so this could be possibly the issue why Ubuntu is not working on my pc ?

---

### Post by turbojugend_gr on 2006-05-08
Hi m8.
Your description of the problem is not very accurate. I suggest you try to reinstall ubuntu and then write down the error messages you get, so we will know exactly what's going on.
As for your card it can't be nvdia X800GT, either it is ATI X800GT or it is nvidia 6800GT. Find out what your card is so you can follow the instructions correctly if those are given to you.
I know i wasn't much help but i am sure you will get better one after an accurate report of your problem. Feel free to notify me.

---

### Post by vb_packets on 2006-05-08
its a RADEON X800GT Graphics Card

---

### Post by turbojugend_gr on 2006-05-08
M8 i would like you to inform me with your progress. Have you tried anything we suggested? keep us informed so you get your problem fixed!

---

### Post by vb_packets on 2006-05-09
still cant get it to work at all. Its got to be driver issues! No Ubuntu Linux no longer works on this contraption.

I might change the graphics card later and see but apart from that i dont know what else i can do.

---

### Post by turbojugend_gr on 2006-05-09
Hi there again,
Here is what to do.
First of all since you 've never got it going with ubuntu format the partitions of UBUNTU and then Re-install it, be carefull not to agree to anything you do not understand during installation. Feel free to write down any topic you need help on choosing.

Remember you need to format the disk space you plan to place UBUNTU. By that I mean you should use the partioner inside the UBUNTU setup, make 3 partitions using the custom partition or manual edit partition table choice when it comes to that point...:

1st. mount point should be "/" and filesystem ext3 journal, be carefull to make the bootable tag yes for this partition --size should be at least 2.5GB.

2nd. mount point "/home" and filesystem ext3 journal --size is relevant to your needs as this partition is the one holding your HOME folder where you put your data (music-videos-documents-etc).

3rd. choose "use as" and there use as SWAP --this partition should be 2 times your RAM memory size.

---

### Post by turbojugend_gr on 2006-05-09
NOTE: The first 4 partitions of every disk are called PRIMARY while the rest are created as LOGICAL inside an EXTENDED partition. Also be sure to start placing your partitions at the start of the unpartioned space.

Be carefull not to ruin any data on other partitions already existing...

If you have any question regarding the above proccess ask me.

When the setup is done you should be ok. If not Remebmer to note down your exact problem an report it plz. As for the graphics card i used to own an x800GT and had no problem with it, though try reconfiguring your x server. You can find out how to do this in various threads , just write "configure xorg" or anything you feel like and look for it through advanced search.

---

