---
title: "Dist-upgrade to 32bit Hoary?"
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nequeo on 2005-05-27
Hi all,

I'm toying with the idea of downgrading my 64bit Hoary system to 32-bit.  I can live with chrooted Cedega and no flash... But I do a lot of remote administration of Windows 2003 servers and mppe-128 has a nasty 64bit bug. I can be a lazy bugger, and if I ever wanted to work from home... *shrug*. It was a fun toy, but I don't do anything computationally expensive enough to warrant the compatibility problems.

Just wondering if anyone knew off-hand if it's at all possible to change my reposititory sources and 'apt-get dist-upgrade' to a 32-bit system, while keeping all my programs and settings intact?

In other words, is there an easy way out?

Otherwise, I'm happy enough to do a clean-install. As long as I can find a way to backup Firefox e-mail. There does not appear to be an export button!

Any help would be appreciated.

Regards,

---

### Post by Nequeo on 2005-05-28
Too slow! Maybe you were all sleeping on another continent something... :) 

```
tar -cvlf backup.tar /home/sger
```  

... backed up smb,conf, too. Then just re-installed Ubuntu, apt-get'ed all my old apps, untarred the archive and hit Ctrl+Alt+Backspace.

Everything came back exactly the way I'd had it, wallpapers, menus and all. I must say, as a long-time Windows user, I'm extremely impressed that this worked as well as it did.

I'm also a lot happier with the i386 install. Lots of niggling little problems I was always having to work around - like gnucash crashes - suddenly went away.

Brilliant. Liking Linux more and more every day.

---

### Post by reuben on 2005-05-31
For future reference, give /home its own partition (seperate from /). Then you can install any distribution into /, and keep all of your user settings, without having to do the tar step.

---

### Post by Nequeo on 2005-06-01
It's certainly good advice... And something I've been advised to do before.

The only reason I didn't was because I was uncertain how much room I'd need for the root partition. I've still got a (small) Windows parition, but the majority of my drive is a FAT32 partition I use for storing OS-independant media such as photos, music, documents and so forth...

---

