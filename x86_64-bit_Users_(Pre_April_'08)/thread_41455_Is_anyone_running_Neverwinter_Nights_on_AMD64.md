---
title: "Is anyone running Neverwinter Nights on AMD64?"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by aglauser on 2005-06-13
So ... I just recently upgraded my processor (woot!) and decided to take a swing at using 64-bit linux.  Almost everything has been working well so far.  I've even converted the */home* directory from my Mandrake 10.0 install (what I was using before the upgrade).

I have a few games installed on in my home directory, most notably UT2004 and Neverwinter Nights.  I installed the AMD64 patch for UT2004 before trying to run it, and everything worked fine.  The problems started when I tried to run NWN.  When I enter the NWN directory and try to execute *./nwn*, I get the following error (not exact, it's from my memory):

nwmain: Can't load libelf.so.1 :  No such file or directory.

I've located libelf.so.0 and symlinked to it using libelf.so.1 in */lib* and in the *nwn/lib* directories.  I also ran *ldconfig* on libelf and on nwmain to no avail.

I then installed a 32-bit hoary chroot environment (from which I can run firefox and synaptic in 32-bit mode), but after using *dchroot -d* to enter the chroot environment, I still get the same error when trying to run Neverwinter Nights.

So, I was wondering: has anyone else has had any luck with this?  Any suggestions would be much appreciated, as I am rather frustrated at this point.

---

### Post by aglauser on 2005-06-13
Alright, after playing around some more I managed to trick the chroot Hoary to install the libelfg0 package.  I had to make a fake /etc/fstab so that apt would install the i386 kernel (fstab needed to create an initrd).  After symlinking nwn/lib/libelf.so.1 to the newly installed libelf.so.0 , I finally got NWN to start!

Sadly for me the performance leave a lot to be desired.  It is worse than on my Athlon 1 Ghz!  Is this normal for GL apps running in a chroot environment?

---

### Post by joekr on 2005-06-14
I'm running Neverwinter Nights flawlessly...

... and I didn't have to install anything else to get it to work...  \\:D/ 

I installed NWN by downloading the game from Bioware, and updating it to the latest version.

I'm not sure why you are having the problems you are...

---

### Post by burntwater on 2005-06-15
I too have NWN working flawlessly on my Ubuntu Hoary AMD64 install.

There was no need to install anything extra at all, I just unzipped the data files, copied the patch stuff in and voila! a working NWN setup in 64 bit environment.

Perhaps try again from scratch? Good luck anyhow  :)

---

### Post by aglauser on 2005-06-15
Thanks for your info joekr and burntwater.  Perhaps the problem is that I am trying to use an existing installation on my */home*  directory, which I had originally installed in Mandrake.

Incidentally, after I posted yesterday I tried to run glxgears agian to see if I could find info in the logs explaining why nvidia-glx was not working.  To my suprise, I got 3000+ fps instead of 13-16.  So, magically, my drivers were working!

Now the only problem is that the expansion packs are not showing up.  I guess it's time to backup my save files and attempt a reinstall.

Thanks again for your comments ... I will try the install in the 64-bit environment first because of them.

---

### Post by Kemotaha on 2005-06-16
I have mine running fine as well.  I used a script that was on the bioware forums to install mine off the platnium CD's.  The only problem was that a few of the mission files didn't get copied right so I had to find them and copy them on my own.

Nathan

---

