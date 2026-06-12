---
title: "[SOLVED] Gutsy AMD 64 Booting/Installation problems &amp;amp; BUGS"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by perixx on 2007-11-29
> This refers to the buggy Gutsy Xorg or graphics driver - whatever, in the first place: using 1280x1024 resolution will result in a black frozen screen after some time of booting (where X-server should kick in, usually) - if I'm lucky, I can switch to another virtual screen and do 'startx'. This varies from time to time. In my Gutsy-installation, the xorg.conf has got no monitor-, driver-, screen- and device-section after installation; I simply hadn't got the time yet to investigate.

By standard (if I do nothing), the Live-CD will boot at 1600x1200 (but not offering it in the screen manager); I can also choose 1024x768. It's really unpredictable what will happen when using the Gutsy live-CD; choosing another language at boot-up will also result in stopping at the bash. Only touching NOTHING at boot-up will cause Gutsy to boot into X-server at all - most of the time.

Using Gparted mounts every single partition/drive availible and crashes after each applied action.... BUGS BUGS BUGS.


By the way: Feisty - which hasn't got the problems stated above - won't let me choose 1600x1200 resolution at all. It's live-CD will boot into 1024x768 resolution by default. Also, even IF I edit the xorg.conf of my installed system and add "1600x1200" in each line where appropriate, I only get a higher refresh rate option (85 instead of 70 Hz) for the 1280x1024 resolution...

... setting up resolution and refresh rate REALLY mustn't be such a big issue in the year 2007 anymore, yet with installed proprietary drivers (!) - it's one of the most basic and elementary functions every desktop has to support (!!).

Even 'Syllable' - which has only about 100Megs and is only partially functional (and has only a handful of dev's) works like charme, not like **** in this respect...

]:-/

**Edit:** I replaced xorg.conf with a backup file containing all vital sections in my Gutsy AMD 64 installation. Everything still the same, except that when I do 'reboot now' after boot has stopped at bash, the screen goes blank and THEN it offers the GDM? graphical login screen, from which I can enter the system! But still, nothing works correctly; the font is tiny and unreadable, using applications always give some error messages.

I noticed there's a problem with some file-system test (error while some 'ext3.chk') and after that booting stops at the bash with the message 'manual' filesystem-check has to be performed... I booted into Feisty, unmounted the hda5 partition (Gutsy) and started sudo e2fsck -fp /dev/hda5:
>   sudo e2fsck -fpv /dev/hda5
115385 inodes used (8.93%)
414 non-contiguous inodes (0.4%)
# of inodes with ind/dind/tind blocks: 6440/58/0
894256 blocks used (34.66%)
       0 bad blocks
       1 large file

   92528 regular files
    9863 directories
      90 character device files
      26 block device files
       2 fifos
     514 links
   12864 symbolic links (12047 fast symbolic links)
       3 sockets
--------
  115890 files
I'll restart now but don't expect too much.

Edit: didn't help anything...


perixx

---

### Post by perixx on 2007-12-02
*bump*

---

### Post by perixx on 2008-01-04
**Gutsy removed, problem Solved** :mrgreen:

no, seriously, one (or several of those issues) could be addressed:
[http://ubuntuforums.org/showthread.php?p=4070578&posted=1#post4070578]("http://ubuntuforums.org/showthread.php?p=4070578&posted=1#post4070578") along with a corrupted filesystem.

perixx

---

