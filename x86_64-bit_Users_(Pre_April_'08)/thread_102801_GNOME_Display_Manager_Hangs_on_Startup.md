---
title: "GNOME Display Manager Hangs on Startup"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrishack14 on 2005-12-12
Well, I'm about at my wits' end here.  I have been using Ubuntu for about 6 months now without any huge problems, until earlier today.  I attempted to start Ubuntu, and all I got instead of the login screen was a flashing cursor that just sat there.  I figured it locked up while trying to start GNOME, so I tried rebooting in recovery mode, but then I got a kernel panick - something about "RAMDISK: compressed image found at block (0,0)" and not being able to mount /hda2 (partition that Ubuntu is installed on) on block (0,0).  Well, okay.  So I restarted into recovery mode again, and this time I got it to boot up, until it hung up on "Starting GNOME Display Manager...".  I have since tried reinstalling GNOME from the command line using apt-get, run sudo dpkg-reconfigure xserver-xorg, and run sudo dpkg-reconfigure gdm, but to no avail.  sudo dpkg-reconfigure gdm exited with an error saying something like "command 'reload' failed".  Also, the command "startx" does in fact start X, but it's just a "blank" grey screen with an "x" cursor, if that's of any significance.  My system is:

EMachines M6809
AMD Athlon 64
ATI Mobility Radeon 9600
Dual-Booting Windows XP and Ubuntu Breezy

This is about as much of it as I can reconstruct from memory.  Any ideas?  If more detailed information would help, I can try to get it if I know what I'm looking for.  Thanks for any help that anyone can offer.  I've learned a great deal about Linux and Ubuntu from this community, and I really appreciate so many people being willing to help here.

---

### Post by dickohead on 2005-12-12
I too am running an e-machines laptop, and if there' one thing i've learnt while running Ubuntu on it - go back to the VERY beginning.

1. - Verify that your CD has been burnt succesfully, don't just assume! If it has errors, burn it at 1X speed.

2. - Run a memtest86 from the ubuntu install disk (where it says to type server/default to install - you type memtest86.. or maybe just memtest)

3. - Your graphics drivers WILL NOT be installed and as such should be! So when you boot in and you get the Gnome login screen being unuseable, do a CTRL+ALT+F2 (or F3..4.5.6...) and run:

sudo apt-cache search ATI

and find your graphics driver, failing that also do a search for fglrx and firegl

4. -You WILL run into a few issues whilst running a 64bit computer (provided you also installed 64bit Ubuntu), as some software has deb's made for it, and others don't - but as i've found out, there is ALWAYS a workaround, even if you have to compile from source and then manually workout dependency problems.

5. - Good luck!

---

### Post by RAOF on 2005-12-12
Except that he's been running Ubuntu just fine for the previous 6 months.  My first advice would be to run a memtest.  You should be able to run that from the grub prompt.  Second would be to check your partitions, using fsck.

---

### Post by chrishack14 on 2005-12-13
Thanks for the replies.  I've pretty much been through the nightmare that is installing graphics card drivers and such for ATI graphics cards on a 64-bit system before and got that worked out some time ago.  That's definitely not the problem.  However, as both of you suggested, I also ran memtest86+ from the GRUB prompt and, well, wow...  It came up with hundreds of errors on several of the tests.  I guess that could explain things.  In retrospect, it probably explains a lot, like the fact that for a few days before all this, some of my programs (Firefox, BitTorrent...) had started randomly crashing every once in a while.  That probably should have been the first thing to check.  Thanks for pointing that out.  Oddly enough, though, Windows XP still seems to run fine on the same machine.  Anyway, so is the most likely culprit here my RAM?  If so, not a huge deal - I was thinking about upgrading it soon anyway.  I have very little experience with memtest86+, though.  Should replacing the RAM be the first thing to try, or could something else be causing the errors in memtest?

---

### Post by RAOF on 2005-12-13
If memtest is failing, then there's certainly **something** wrong with your hardware.  But it doesn't have to be the memory; maybe the powersupply is not putting out enough power.  Maybe the CPU is writing corrupt data.  Maybe the motherboard ram traces are bad.  It's difficult to say.

XP has, in my experience, handled bad hardware somewhat better than linux.  Partially, I think, because a certain degree of random crashing is expected ;)

---

