---
title: "Update issues"
date: 2008-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by hlhcomms on 2008-03-08
I currently have 5 updates waiting in the Update manager, but cannot install any of them.

Firstly, I select the 'partial upgrade' option, but this brings back an error saying that the update manager can't get an exclusive lock. I have checked through the system monitor but can't see any other package manager running... so, I try going back and cancelling the partial update instead choosing 'install updates'. The following message appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have researched this through the forums and tried (through a terminal):

sudo apt-get update

which results in:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

So, as instructed, I run sudo dpkg --configure -a which results in:

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up clamav-base (0.91.2-3ubuntu2.3) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.91.2-3ubuntu2.3); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

I tried also sudo apt-get update && sudo apt-get upgrade, but this resulted in:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Anyone got any alternative suggestions? Everything seems to work ok, but but I can't clear any of these updates and may miss an important patch as a result... any help appreciated greatly!

---

### Post by pbpersson on 2008-03-10
I just read in another forum that the /var/lib/dpkg/updates folder is the one where all the downloaded updates are stored before they are installed on your system.

They said there might be a corrupted file in there and if you delete everything in that folder it will clear out all the updates that cannot be installed.

Perhaps one of the files was corrupted during download?

Hey - I just looked at that entire file.....and it sounds like you have larger problems on that system :(

---

### Post by hlhcomms on 2008-03-11
Thanks for taking the trouble to look! 

I'll trying to crack this, and will post the solution if I ever find one!

---

### Post by hlhcomms on 2008-03-11
Well, I just tried deleting those files... I couldn't at first, but logged in as ROOT and had no problem.

I re-ran the update manager and tried a Partial Update, but this failed. However, when I restarted the update manager I tried a full update. Although some error messages were thrown back, the majority of the updates ran through and now there are no outstanding updates shown pending in the toolbar. I'll have to investigate further as to why npViewer crashed in the process, but that's a subject for which I've seen plenty of threads...

Thanks for your help :)

---

### Post by salomaocohen on 2008-03-12
Thank you very much, pbpersson. You solved my 1 month problem.

---

### Post by moreinfo on 2008-03-12
I also just recently got an update problem on 6.10.

When I go to update, nnow I have 20 waiting, I get the following message.

"Only one software management tool is allowed to run at the same time"
"Please close the other application e.g 'aptitude' or 'Synaptic' first."

However, these things are not running.

I am still learning, so if possible laymans terms would be great.
Thanks in advance.

---

