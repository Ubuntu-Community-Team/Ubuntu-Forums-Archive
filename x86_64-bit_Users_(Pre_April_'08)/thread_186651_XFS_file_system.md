---
title: "XFS file system"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Circleback on 2006-06-02
I wondering if anyone is using the XFS file system. I read a few articles that stated that XFS file systems are a bit faster than reiserfs. I had my SUSE install at first with reiserfs then i switched to XFS and had a noticeable performance boost. Especially at boot up. How about XFS under Ubuntu/Kubuntu?

---

### Post by henriquemaia on 2006-06-02
[quote=Circleback]I wondering if anyone is using the XFS file system. I read a few articles that stated that XFS file systems are a bit faster than reiserfs. I had my SUSE install at first with reiserfs then i switched to XFS and had a noticeable performance boost. Especially at boot up. How about XFS under Ubuntu/Kubuntu?[/quote]

Read this. Maybe this will help you out:

[http://ubuntuforums.org/showpost.php?p=1071482&postcount=2](http://ubuntuforums.org/showpost.php?p=1071482&postcount=2)

---

### Post by RAOF on 2006-06-02
One of the things not mentioned there is that XFS is aparently less fault-tolerant than ext3.  Oh, and that you don't need a 500mb /boot partition; I use 50mb, and that's fine.

As to your actual question: XFS should work no differently in Ubuntu than SUSE

---

### Post by Circleback on 2006-06-02
Ok thanks for the replies. I will install it using a boot partition. This community around Ubuntu is completely awesome! Really great for the Linux learner.

---

### Post by JoWilly on 2006-06-02
XFS is faster for big files, but reiser is faster for general use.

The reason why xfs boots up faster, is not because it is "faster". Its because reiserfs takes more time to mount and check the filesystem journal for errors.

---

### Post by georgew on 2008-03-21
I have a mail server that is experiencing performance problem.

I have tracked the problem down to a small number of users with excessively large incoming mail folders, with thousands of mail items.

The filesystem performance on these large directories (ext3 filesystem) is abismal.  I sit in 95% i/o wait, using less than 1% of my i/o bandwidth.  I have a fast physical filesystem based on 3ware drive arrays configured for speed, but large folders under ext3 are killing me.

Should I consider moving mail storage to an XFS filesystem?  Or is XFS too unreliable, and I should use one of the other options?  Suggestions?

thanks in advance!
George

---

