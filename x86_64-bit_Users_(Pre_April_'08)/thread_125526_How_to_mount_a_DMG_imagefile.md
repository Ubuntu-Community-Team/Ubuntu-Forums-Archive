---
title: "How to mount a DMG imagefile?"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dingen on 2006-02-04
I've downloaded a DMG-type imagefile from the Apple website with some PDF's on it I would like to read on my Ubuntu Breezy-system.

How am I going to mount the DMG?

---

### Post by erimar77 on 2006-02-04
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

---

### Post by Dingen on 2006-02-04
[QUOTE=erimar77][http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)[/QUOTE]

Thanks, but when I try it, it only says:

```
:~$ sudo mount -t hfs -o loop jan06devdocpdf.dmg  /media
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

:(

I also tried this: [wiki-entry on image-stuff](https://wiki.ubuntu.com/ManageDiscImages#head-fc14558e9b3177677844d5851cd01ed8ee7dea4a)

But that results in:

```
:~$ dmg2iso.pl jan06devdocpdf.dmg devdoc.iso
bash: /usr/local/bin/dmg2iso.pl: /usr/bin/perl^M: bad interpreter: No such file or directory
```

:(

---

### Post by phibxr on 2006-02-05
Have you tried -t hfsplus? (or -t hfs+, not sure, but I'd guess hfsplus)

---

### Post by mr_cazorp on 2006-09-06
```
:~$ dmg2iso.pl jan06devdocpdf.dmg devdoc.iso
bash: /usr/local/bin/dmg2iso.pl: /usr/bin/perl^M: bad interpreter: No such file or directory
```


The ^M is a tipoff that there's DOS-style linefeeds (carriage return + newline) in the file. Get rid of them by removing the carriage returns: 

```

$ cat dmg2iso.pl | tr -d "\r" > dmg2isofixed.pl 

```

Then run dmg2isofixed.pl. If you don't have the Perl module Compress::Zlib installed, you'll have to learn about CPAN as well... 

Alas, I ran the script on the DMG I was trying to mount, and it said the image was corrupt, though it mounted fine in OSX. So I guess it's still a work in progress... :neutral:

HC

---

### Post by bluenova on 2006-09-11
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

---

### Post by flouran on 2008-07-11
The only way you can mount a dmg with the command, *sudo mouunt -t hfsplus -o loop /path/to/dmg /mount/point*, is to decompress it first into an img file.

In order to decompress a dmg, then mount it, download *dmg2img* from [http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz]("http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz")
Then, after saving the file, *dmg2img* in your home folder, open terminal, and run, *tar -zxvf ./dmg2img.tar.gz*, then run run, *cd dmg2img*, then once you are inside the dmg2img directory run, *make all*.

If everything goes okay, then you can decompress your dmg file by executing the command, *./dmg2img -i /path/to/inputfile.dmg -o /path/to/outputfile.img*, and remember, you must be inside the dmg2img directory at all times in order to run the command listed above. Also, the img file needs to be in the same location as the original dmg file. And preferably, the img file should have the same name as the dmg file. After decompressing the dmg, run, *sudo modprobe hfsplus*, then if hfsplus is installed (if not, run *sudo apt-get install hfsplus*), run *sudo mount -t hfsplus -o loop /path/to/outputfile.img /mount/point*. To create the mount point, run *mkdir -p /mount/location*.

---

