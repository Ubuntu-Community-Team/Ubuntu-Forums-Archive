---
title: "Ubuntu or SimplyMEPIS help installing, can't get back to xp AAAAAHHHHHHH!!!!"
date: 2006-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by myubuntuname on 2006-02-11
I HAD an xp system and was going to try linux and I am now offically screwed. Please help.....

System:
AMD 64 3000+ processor
MSI K8 motherboard with onboard 5.1 surround
dual dell 21" trinitron crt monitors
nvidia 6600 gt graphics card
MSI TV/Tuner card
western digital 200 GB and maxtor 250 Gb set as RAID 0 array
(has been working flawlessly for a year and a half)
windows xp pro
epson 740i printer, 610 scanner
logitech pro 2000 webcam
iomega zip100
imation superdisk
yahoo dsl with actiontec wi-fi router
D-link wifi card and antenna
(I included all the periferrals so if there are any issues with them, someone might take the time to note them.)

I was getting tired/sick of windows after having come from the Apple G3 side of things a few years ago and wanted to try linux. I chose Ubuntu for a number of reasons, although I would also like to try MEPIS, and Gentoo when I get more experience. Anywho....

I downloaded Breezy Badger for AMD64 systems and began the install process. I used the partitioner that was on the ubuntu disk. I did NOT use partition magic or an external program to partition the hardrives before the install.
At first it wouldn't recognize anthing to do with my DHCP connection and I was stalled. But then, I figured out my settings (used mom's computer in the front room)and began anew. after the network connection was ok, then I got a base system install error. It told me it could not find an install cd and there was no recognized mirror. After putzing with the cd drive and verifying the disk.....the install went ahead as normal....then after the reboot I got a Grub install error 25.
I thought that since it might be a problem with my raid setup...I looked into the RAID software setup on the ubuntu installer and set the partition as RAID. After that didn't seem to help I cancelled the install operation and tried to reinstall per the default setting again.
After giving up, I tried to boot back into windows and I just get a black screen and it won't load into XP. So now I essentially have no computer and I'm not even sure I can ever get back into xp to my files. I did make backup copies of everything I thought was important, but there is so much stuff on my computer I would really HATE to have to reinstall xp.
After looking on various forums I determined there might still be a problem with the RAID setup and ubuntu was just having a hard time finding the grub bootloader. I also saw a forum entry that suggested trying to use the MEPIS install disk to correct my problem, so I downloaded SimplyMEPIS 3.4-3 and tried to install that onto my system but during the initial process it hangs at the 40% mark...I press F2 for info...but since I'm a n00b I have no idea what I'm looking at anyway, and now I'm stuck again.
  I also typed in "rescue" at the beginning of the ubuntu install and that put it in recue mode, but then it asks me whether I want to use disc 0 part 1,2,3 or disc 1 part 1,2 or 3 and I didn't have a clue what to do, so I chose disc 0, part1 and when that didn't do anything I chose disc 1 part one and then it stopped doing anything.

 SOMEONE PLEASE HELP ME. I looked and looked online for a chatroom, but found none...so I'm resorting to using the forums. Hopefully this will help someone in the future with similar problems.
I am in the process of downloading the LiveCD version of Ubuntu to maybe run the disk and possibly fix whatever is wrong. 

If you can help...please post on the forum to help others...but also please send me an email to [email]mytopsecretmailbox@yahoo.com[/email] because I'm going to have to read your reply on a borrowed computer and an email is easier to access than trying to remeber which forum I posted to and the forum password and crap.

Thanks for any help you can give.
Danny

---

### Post by Robgould on 2006-02-11
I think you need to repair your master boot record.
 
User your winxp install disk to boot to windows in rescue mode
 
when you get a prompt type "fixmbr"
 
reboot
 
You should be fixed.

---

### Post by Robgould on 2006-02-11
As a side note, you can configure setting in these forums so that replies to your posts are automatically sent to your e-mail.

---

### Post by myubuntuname on 2006-02-11
Fabulous....I will try that.

Thanks

.....any idea why ubuntu won't install?

---

### Post by myubuntuname on 2006-02-11
Thank you...I was a little frantic and didn't look at any user prefs...I wanted to post and get a reply as quickly as possible.

---

### Post by Robgould on 2006-02-11
I have never instally ubuntu on a system as sophisticated as yours.  The very first thing I would try it to verigy the checksum on the iso I downloaded.   If it was ok, I would burn a new image.  If it was not, download new file, verify, then burn.  Bad images and burn errors are not uncommon.

---

### Post by myubuntuname on 2006-02-11
Do you mean go to the recovery install?....I booted from the cd and it asks whether I want to do an install a recovery install or exit...I chose recovery and typed in fixmbr and it went back to the c prompt and I typed exit and It tried to load into ubuntu after reboot and I got the grub error 25 again.

---

### Post by Robgould on 2006-02-11
well I guess that did not work out.  I am not sure what to try next.  By default grub is installed to your master boot record.  Fixmbr should have rewritten the mbr.  This should have overwritten grub.  If that did not work, then I am out of ideas.  Sorry I could not be of more help.

---

### Post by Robgould on 2006-02-11
There is another command you could try from your boot disk...it is fixboot
 
I am not sure if this will help or not.

---

### Post by myubuntuname on 2006-02-11
Tried fixboot...said it couldn't find system drive.....argh

Is there any way to fix the grub loader?...I am downloading the stupid ubuntu again....this is taking forever.....I erased it off mom's computer because she doesn't like my stuff on it.

Checksum on my Mepis CD is good btw...
7a18f57344d9656dacf6634d7b7a0f21  SimplyMEPIS_3.4-3.iso

Ubuntu will be known as soon as it downloads...+
---------------checksum on ubuntu is fine also...........

---

### Post by Robgould on 2006-02-11
I will bump this for you and defer to wiser minds....I have never had to repair grub.  I usually jsut do a re-insall if I need to.....I am always playing with different distros.  Sorry I could not help you more.

---

### Post by myubuntuname on 2006-02-13
bueller....
bueller....
bueller....


HELP!!!!!!!!!!!!!!!!!!!!

---

