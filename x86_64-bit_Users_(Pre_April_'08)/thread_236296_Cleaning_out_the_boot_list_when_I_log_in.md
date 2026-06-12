---
title: "Cleaning out the boot list when I log in"
date: 2006-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by rhomp2002 on 2006-08-14
I have loaded several versions of UBUNTU as well as one of MEPIS and my old Windows XP.  I followed the instructions for removing most of the old UBUNTU versions from my boot record.  Unfortunately the boot list still has all of them listed over and over.  There are the generic and the default and the backup versions of UBUNTU loads I did that are still there.  How do I get them off the list.  As it is the listing goes on for almost 3 screens.  If I should ever want to sign onto Windows I have to hold the down key and wait and wait and wait for the list to end as Windows is the last item on the list.

This is, of course, minor as the UBUNTU still loads and works fine but it is rather irritating and it seems I should be able to get these other items off the list easily.  I thought when I removed the old versions from my boot record it would remove them from the list but I guessed wrong.:confused:

---

### Post by earobinson on 2006-08-14
uninstall all old kernels using synaptic

---

### Post by rhomp2002 on 2006-08-14
I checked the Synaptic Package Manager and none of the UBUNTU versions on the list were installed.:confused:

---

### Post by rhomp2002 on 2006-08-14
Correction to the above.  The only UBUNTU version installed was the current one.  None of the others was installed.

:confused:

---

### Post by earobinson on 2006-08-14
what happens if you try and boot into one of the other ubuntu versions?

---

### Post by rhomp2002 on 2006-08-14
Went back in logging into one of the old versions of UBUNTU and then went on synaptic and deleted the linux-image members again.  Then when I tried to log onto that linux image, I got the message that it wanted me to enter a password before I even got to the UBUNTU login screen.  I tried to enter the other limux image I deleted and got the same thing.  Then I tried to enter the Dapper linux image which is the latest one I have and it worked just as it should.

The old linux images still show up as selectable when I boot but they don't boot right.  Now all I have to do is figure out how to delete them from the list on the boot record I guess.  Is there something called a boot/grub/member.lst that would contain these items that I could edit and delete the unwanted entries?

---

### Post by John Jason Jordan on 2006-08-14
> **rhomp2002 said:**
> Went back in logging into one of the old versions of UBUNTU and then went on synaptic and deleted the linux-image members again.  Then when I tried to log onto that linux image, I got the message that it wanted me to enter a password before I even got to the UBUNTU login screen.  I tried to enter the other limux image I deleted and got the same thing.  Then I tried to enter the Dapper linux image which is the latest one I have and it worked just as it should.

The old linux images still show up as selectable when I boot but they don't boot right.  Now all I have to do is figure out how to delete them from the list on the boot record I guess.  Is there something called a boot/grub/member.lst that would contain these items that I could edit and delete the unwanted entries?
First, I think the list is in /boot/grub/menu.lst. Open it with "sudo gedit /boot/grub/menu/lst" and see if it contains your whole list. I've been told that this is the file you need to edit.

Second, as someone else already pointed out, removing the old ones with Synaptic is supposed to remove them from the boot list automatically. In my case that did not happen but I have a special situation closely related to this thread that I hope someone can help me figure out.

The Special Situation of JJJ:

After spring term was over I decided to upgrade my Breezy to Dapper. Breezy was on a 60 GB partition. The hard disk had 20 GB unused. The upgrade to Dapper was a disaster. It went so badly that it wouldn't even boot. In an effort to fix it I made a new 8 GB partition and used it for a new, clean installation of Dapper. My intention was to use it to rescue my Breezy-to-Dapper installation However, eventually it became clear that my old Breezy was unrepairable. By that time I had already installed quite a few things on the new Dapper. I decided to use the new Dapper as a test bed, then move it to the 60 GB partition, whereupon it would become my main installation. 

I am pleased to say that my new Dapper "test bed" installation is now perfect. I have spent a LOT of time installing, tweaking, and fixing stuff. It would take me a week of full time labor to recreate it on a fresh install of Dapper. I now want to copy it to the 60 GB partition and make that my main boot installation, while keeping the test bed installation as a rescue setup.

To accomplish this, first I reformatted the 60 GB partition. Then I used "rsync -a --exclude=/proc/* / /media/hda2" to copy all files, permissions and ownerships to the old 60 GB partition (hda2). This went fine, and there is now a copy of my test bed installation on the 60 GB partition. 

Then I tried to edit the Grub boot list to add the new installation. I opened it as root with Gedit. Then I copied and pasted the list of kernels to boot to (basically just -25 and -26, -26 being the one I normally boot to). Having copied and pasted the list (duplicating it), I edited the location for the first list to "hda2" instead of "hda3." 

Then I restarted the computer. When the Grub menu came up it still just showed the one "test bed" installation on hda3. Editing menu.lst seems to have had no effect. If I open menu.lst with Gedit, my changes are there. So I did properly save it. 

Does anyone know how to make Grub see the copy of my test bed installation and boot to it?

---

### Post by rhomp2002 on 2006-08-15
Mission, I think, mostly accomplished.  I was finally able to clear out all the stuff from the Breezy Badger version of Ubuntu from the boot-grub records.  Now I get only the Dapper Drake versions listed along with the ones generated by the Debian Installer and the Windows XP dual boot entry.  I printed out the list before I deleted all the crap and it ran to 26 pages.  I will print it now and see how much is still there.  I would bet that I cleared out at least 2/3 of it.

Thanks for all the help.  Much appreciated.:D :D :D :D :D

---

### Post by rhomp2002 on 2006-08-15
I was right.  From 26 pages to 9 pages.  Bet this is still more krep that can go as well but this is a big improvement.  Once I become a Linux star then I can take care of the rest!!;) ;) :D :D

---

