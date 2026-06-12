---
title: "some quick questions about setting up the 64bit ubuntu"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonathan987 on 2006-06-01
ok, so I'm about to build a new system (a server, just waiting for the new asus amd board that support ddr2 RAM) and it will run this new version of ubuntu on it. 

My first question is: I have heard stuff about using windows drivers as the linux driver with some wrapping program? a lot of the drivers that are given for windows don't have a linux equals, how does this work? The asus motherboard that I am thinking of purchasing is just about to be released....so there is no driver download page, so I can't point you there specifically. I have heard from friends that they have had troubles with asus motherboards and getting the SATA ports to work, is this the case?

My second question is (which should go in the installation section.....): when installing the 64bit desktop version of ubuntu, I want to setup raid 5 using LVM, so I guess I have to use the "alternate" version of the install? Is this gui, or will I have to slave away in cli for the entire process? Or is it just cli for the raid setup and uses the gui from the normal desktop install?
If it is cli, could someone point me to a tutorial showing me how to set it up or tell me in this thread.
Edit:// to clarify I'm installing ubuntu on a single drive and can setup the Raid 5 later. The raid 5 partition, will not have the OS on it. Should I still download the "alternate" version, or can I setup LVM with Raid5 after ubuntu is up and running?!?! thanks!!!

My third question: How does one know when a drive goes down in the raid 5 setup? The reason I am using raid 5 is because within the last 2 months I have had two harddrives fall apart on me and it's quite a piss off.
The reason I am planning to use ubuntu is because most things just use binaries (saves time) and it's mainly in gui, correct? is there something in the control pannel that lets you know your drive is down?

Cheers + thanks in advance,

Jonathan

---

### Post by Jonathan987 on 2006-06-06
does anyone want to help me out here...?

---

### Post by Hendrik van den Boogaard on 2006-06-07
Quick reply, I don't have a lot of time now

- I don't know about the board. It's probably a AM2 socket board. If they don't use too advanced chipsets or something I think it will work. My 'standard' S939 board (ASUS A8N VM CSM) works fine except for the DVI output (that's another issue with Nvidia).
- You can setup RAID5 later easily with the EVMS-GUI. That should do the trick fairly easy.
- As far as I know the MDADM daemon will notify you by e-mail about the status of the drives in case of a failure. But you can always query the status (or make a script to do so) by 'cat /proc/mdstat'.

---

