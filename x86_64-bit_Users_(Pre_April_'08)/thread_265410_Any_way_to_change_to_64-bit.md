---
title: "Any way to change to 64-bit?"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by WalmartSniperLX on 2006-09-25
Is the ANY way whatsoever I can get my kubuntu 32bit into 64bit w/o having to reinstall?

---

### Post by Mr Frosti on 2006-09-25
You can change your sources.list to reflect the 64-bit servers, and then, from the terminal type in "sudo apt-get update ; apt-get install dist-upgrade"

I would highly recommend backing up your data before doing this though, as there is a good possiblity the machine won't initially boot into your desktop. 

You will also need to reinstall any custom installed drivers, such as ATI's proprietary drivers. Fortunately, you can use the same download since their 32-bit and 64-bit driver packages have been combined.

---

### Post by WalmartSniperLX on 2006-09-25
> **Mr Frosti said:**
> You can change your sources.list to reflect the 64-bit servers, and then, from the terminal type in "sudo apt-get update ; apt-get install dist-upgrade"

I would highly recommend backing up your data before doing this though, as there is a good possiblity the machine won't initially boot into your desktop. 

You will also need to reinstall any custom installed drivers, such as ATI's proprietary drivers. Fortunately, you can use the same download since their 32-bit and 64-bit driver packages have been combined.

Alrighty :D Thanks a lot for your post and info :-D

---

### Post by Mr Frosti on 2006-09-25
You are most welcome. Let me know the results!

---

### Post by Kilz on 2006-09-26
> **WalmartSniperLX said:**
> Alrighty :D Thanks a lot for your post and info :-D

I dont think its possible. You can try if you really want to , but I think you are headed for disaster. I also recommend leaving the 32bit partition alone and starting a new 64bit one. That way if you have any problems you still have a working install.

---

### Post by jharr on 2006-09-26
I wouldn't bother trying to switch. You'll end up with a mess for an installation. It's going to be more work than it's worth.

Your best bet is to back up your home directory contents, install 64 bit, copy your home directory back, and go from there. IIRC most linux apps like to store stuff in a portable fassion (usable on different architectures). Most of your application configuration should port right over.

If you have a bunch of custom packages installed and want to copy those over, do this at the shell:
$ dpkg -l | tail -n +6 > pkglist-32.txt

After you reinstall, `apt-get install diff` and then run:
$ dpkg -l | tail -n +6 > pkglist-64.txt
$ diff -u pkglist-64.txt pkglist-32.txt | grep ^+ | grep -v +++ | cut -d+ -f2 > pkglist-diff.txt

pkglist-diff.txt will now show a list of packages you had in the first install, but not the second. Go through, make sure there isn't anything obvious that shouldn't be in there (like linux-image-2.6.12-10-i386-generic). Save that, then run:
$ sudo apt-get install `cat pkglist-diff.txt`

Then you should be off. Like I said, make sure you check for dumb stuff in your pkglist-diff.txt file before you install something. Chances are, if you don't recognize it, you either a) don't want it b) it's a dependency that apt will handle automatically, so don't worry about it.

That said, migration to 64 bit through reinstall and copying data files is probably more sane than 32-to-64 "upgrading", and definitely more clean. You're also less likely to bone yourself over when you work yourself into a corner where you have only a 32 bit kernel and 64 bit binaries and can't boot.

Good luck ;)

---

