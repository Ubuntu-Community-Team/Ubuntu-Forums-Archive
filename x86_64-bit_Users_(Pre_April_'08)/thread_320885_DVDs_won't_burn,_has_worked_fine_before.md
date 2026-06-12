---
title: "DVDs won't burn, has worked fine before"
date: 2006-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2006-12-18
Hi, I have been able to burn DVDs fine up until a couple of months ago. Now that I have a spare minute I'm investigating. 

**Gnomebaker** gives this error:

```
Executing 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p root -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-root/gnomebaker-MLnyxj | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
:-( Failed to change write speed: 0->3324
```

**Nerolinux** only seemed to work in the 32-bit chroot. This is its output:

[IMG]http://homepages.woosh.co.nz/ryan.kennedy/images/nerolinux.jpg[/IMG]

**Graveman** gave the Input/Output error but no more information even when I ran it from terminal. 

I don't know how to burn a data DVD from the command line although I have tried to make data ISOs from the command line using mkisofs:

```
ryan@ryan-desktop:~$ mkisofs -dvd -o /home/ryan/graphics/screenshots/dvd.iso /home/ryan/graphics/screenshots/
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.
```

Can anyone help please? I have previously been able to burn data DVDs just fine using Gnomebaker and Nautilus. I would like to try creating a dvd iso from the command line to identify the error but don't know how.

Thanks for any help.

---

