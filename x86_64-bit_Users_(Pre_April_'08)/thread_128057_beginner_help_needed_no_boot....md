---
title: "beginner help needed: no boot..."
date: 2006-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxNewb555 on 2006-02-10
[LIST=1]
[*]just built this computer: AMDAthlon64(3400), SeagateBarracuda HD (SATA), Plextor CD/DVD(PX716SA)
[*]BIOS boot sequence: Plextor, hard drive, no Floppy
[*]Knoppix 3.6 works reading from drive
[*]redHat8 install disks work (i canceled once i found out that the system would recognize the cds)
[*]when attempting to use ubuntu5.1(amd64 install version ISO) in the cd drive to boot, i receive this error:"Reboot and select proper boot device or insert boot media in boot device..."
[*]downloaded again, this time the file name was ubuntu 6.1, same error msg.
[/LIST]
So, the 32 bit options don't present any problems, but i can't get the ubuntu install disk to boot. 
The hard drive is brand spanking new, no formatting.
Any suggestions? 
Thanks.
( i will re-examine my BIOS options)

---

### Post by Robgould on 2006-02-10
Sounds like a bad iso.  Did you download or order the pressed version?  It is more common than you might think to download a bad iso or have a burn error that makes it bad.  I would try a new download.  The thread below talks about bad images and how to verify the checksum to make sure your media is good.  Hope this helps you.
 
[http://www.ubuntuforums.org/showthread.php?t=101533&highlight=verify+checksum]("http://www.ubuntuforums.org/showthread.php?t=101533&highlight=verify+checksum")

---

### Post by linuxNewb555 on 2006-02-11
Ok, so i've been doing a lot of work in the past 24 hrs. There was probably nothing wrong with the CD, only the way that I saved it to disc. I was not using an ISO recorder. Based on what I've seen in the forums, I'm willing to bet a lot of people like me (not familiar w/ ISO) make the same mistake.  So, downloaded ISO recorder, re-burned Ubuntu, installation was painless. Now I'm jumping for joy since I have entered the Linux world. Thanks for your input. Next question: how do i protect my computer while connected to the internet? I need some firewall advice.

---

### Post by RAOF on 2006-02-11
Quick answer: unless you deliberately install some form of server (apache webserver, ssh server, ftp server) Ubuntu doesn't listen on any ports.  That means that it doesn't listen to the internet, and so you don't need to protect yourself from it.

If you know you need a firewall (you are running some server process, or something), then 'firestarter' is apparently a good frontend to manipulating the linux firewall.  You should be able to install that through Synaptic.

---

