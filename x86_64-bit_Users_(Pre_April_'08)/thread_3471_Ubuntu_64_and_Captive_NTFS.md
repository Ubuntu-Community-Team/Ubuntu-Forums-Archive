---
title: "Ubuntu 64 and Captive NTFS ?"
date: 2004-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2004-11-06
How can i install Captive NTFS so i have write access on a NTFS partition ?
When i do the mount :
 mount /dev/hda1 /mnt/windowsxp -t captive-ntfs
Captive NTFS v1.1.5.  Check a new version at: [http://www.jankratochvil.net/](http://www.jankratochvil.net/)

it hangs on my 64-bit OS !
On a 32-bit Linux it works but not on a 64-bit .
Any suggestion ?

---

### Post by pgoya on 2004-11-16
hey, here hapens the same thing, and I don't have a 64-bit.
How do you install the captive on the 32-bit Linux??  :-( 

Thx!

---

### Post by jdong on 2004-11-16
Captive is trying to load a 32-bit **ntfs.sys** onto a 64-bit kernel. Not gonna work.

Sorry, Captive won't work under 64-bit Linux, not even under a 32-bit chroot environment.

---

### Post by ulefr01 on 2004-11-17
[QUOTE=jdong]Captive is trying to load a 32-bit **ntfs.sys** onto a 64-bit kernel. Not gonna work.

Sorry, Captive won't work under 64-bit Linux, not even under a 32-bit chroot environment.[/QUOTE]


That's not true.
Captive NTFS works fine under a 32-bit chroot !

Done following test with the Knoppix Life cd version 3.7 (=32-bit)
- startup with : 'knoppix 2 lang=be'
- execute : 'captive-install-acquire'
     (be sure your windows partition is mounted (read-only))
    afterwards the /var/lib/captive directory should contain the following files
    cdfs.sys, ntfs.sys, ntoskrnl.sys, fastfat.sys, ext2fsd.sys
- execute : 'mount -t captive-ntfs /dev/....  /mnt/hd..'

You have write access

---

### Post by jdong on 2004-11-17
That's not a 32-bit chroot... That's running another 32-bit distro. I was talking about installing 32-bit Ubuntu inside a 64-bit Ubuntu, so a 64bit kernel is running 32-bit binaries. That setup won't work.

---

### Post by ulefr01 on 2004-11-17
[QUOTE=jdong]That's not a 32-bit chroot... That's running another 32-bit distro. I was talking about installing 32-bit Ubuntu inside a 64-bit Ubuntu, so a 64bit kernel is running 32-bit binaries. That setup won't work.[/QUOTE]

Jdong, 
My answer was the answer on the question of  pgoya
"hey, here hapens the same thing, and I don't have a 64-bit.
How do you install the captive on the 32-bit Linux??"

---

### Post by jdong on 2004-11-18
sorry, misunderstanding after misunderstanding! LOL

My answer was in response to the original author, and I thought the 2nd time you were referring to the original author, too. Sorry!

---

### Post by raid517 on 2005-04-11
Hey what about if he substitutes a 32 bit ntfs.sys with a 64bit ntfs.sys? Would that work? You can get a trial version of XP 64Bit from MS for free.

GJ

---

### Post by bunty on 2005-07-06
[QUOTE=ulefr01]That's not true.
Captive NTFS works fine under a 32-bit chroot !

Done following test with the Knoppix Life cd version 3.7 (=32-bit)
- startup with : 'knoppix 2 lang=be'
- execute : 'captive-install-acquire'
     (be sure your windows partition is mounted (read-only))
    afterwards the /var/lib/captive directory should contain the following files
    cdfs.sys, ntfs.sys, ntoskrnl.sys, fastfat.sys, ext2fsd.sys
- execute : 'mount -t captive-ntfs /dev/....  /mnt/hd..'

You have write access[/QUOTE]

I checked for those files and I see ntoskrnl.exe ! Is that a typo on your part or could that be a archive that failed to unpack to give the sys ?

TIA

---

### Post by ulefr01 on 2005-07-06
that was a typo error ; it should be
ntoskrnl.exe

The files must be come from a SP1 Windows XP system then you have NTFS write access on a Windows XP SP2 system.
Please backup or archive these files.

It is not working if your files comes from a SP2 Windows XP system !

---

### Post by bunty on 2005-07-06
Many thanks,

how can I tell SP1 from SP2? I used the "aquire" tool since I have win2k on this machine. If I re-run it , it tells me I have best ones in the right place but it sure dont work.

so far all I get on mount is the error saying to visit the site for an update. ](*,) 

Seems a lot of ppl get that from what I have seen.

Thx

---

### Post by ulefr01 on 2005-07-07
[QUOTE=bunty]Many thanks,

how can I tell SP1 from SP2? I used the "aquire" tool since I have win2k on this machine. If I re-run it , it tells me I have best ones in the right place but it sure dont work.

so far all I get on mount is the error saying to visit the site for an update. ](*,) 

Seems a lot of ppl get that from what I have seen.

Thx[/QUOTE]

Can you do :
ls /var/lib/captive -la

Can you mention me also your mount command and the error message you get ?

---

