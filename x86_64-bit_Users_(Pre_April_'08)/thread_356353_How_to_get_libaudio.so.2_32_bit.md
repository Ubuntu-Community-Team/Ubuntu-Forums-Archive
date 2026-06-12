---
title: "How to get libaudio.so.2 32 bit"
date: 2007-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ndefontenay on 2007-02-08
hi,

I'm trying to install skype, everything has been pretty smooth so far thanks to all the excellent work done on this part of the forum so far.

I've reached a point where it's asking me libaudio.so.2 and keeps complaining that there's no such file or folder...

I've seen this thread:

[http://ubuntuforums.org/showpost.php?p=1641546&postcount=113](http://ubuntuforums.org/showpost.php?p=1641546&postcount=113)

i'm running Kubuntu and from all the upload it's doing, I think can safely tell it's edgy...

Can somebody post a link here explaining where I should get this file?

It would be really helpful.

Thanks

---

### Post by Kilz on 2007-02-08
> **ndefontenay said:**
> hi,

I'm trying to install skype, everything has been pretty smooth so far thanks to all the excellent work done on this part of the forum so far.

I've reached a point where it's asking me libaudio.so.2 and keeps complaining that there's no such file or folder...

I've seen this thread:

[http://ubuntuforums.org/showpost.php?p=1641546&postcount=113](http://ubuntuforums.org/showpost.php?p=1641546&postcount=113)

i'm running Kubuntu and from all the upload it's doing, I think can safely tell it's edgy...

Can somebody post a link here explaining where I should get this file?

It would be really helpful.

Thanks

Here is a page I created that will tell you what to do. [http://tghc.org/32biton64bit.php](http://tghc.org/32biton64bit.php)

---

### Post by ndefontenay on 2007-02-08
Hi,

thanks for the quick answer and sorry for the delayed answer. I'm in Thailand...

I've tried your link.

I've think I've been through it at a certain point. 
I used a script to install skype that would download a lot of packages.
I've got all the liba libq files 32 bits and added them.
The last one was not in the package though...

On your link. [http://www.tghc.org/32biton64bit.php](http://www.tghc.org/32biton64bit.php), I'm not able to click on any link in the table. It's showing everything as text and is not clickable (note: I'm trying that from office. It might work better back home on kubuntu)

---

### Post by Kilz on 2007-02-08
> **ndefontenay said:**
> Hi,

thanks for the quick answer and sorry for the delayed answer. I'm in Thailand...

I've tried your link.

I've think I've been through it at a certain point. 
I used a script to install skype that would download a lot of packages.
I've got all the liba libq files 32 bits and added them.
The last one was not in the package though...

On your link. [http://www.tghc.org/32biton64bit.php](http://www.tghc.org/32biton64bit.php), I'm not able to click on any link in the table. It's showing everything as text and is not clickable (note: I'm trying that from office. It might work better back home on kubuntu)

The link and page are not links to download files for skype. They are generic directions on how to install all 32bit applications to 64bit Ubuntu. Please reread the directions.

---

### Post by ndefontenay on 2007-02-09
Ah crap ><

I feel like a n00b now...

Well. I've reviewed your explanation.
I've found the library I'm looking for.

To complete this thread, I will link straight to it:
To get libaudio.os.2 32bits go to this link:

[http://packages.ubuntu.com/edgy/libs/libaudio2](http://packages.ubuntu.com/edgy/libs/libaudio2)

and select i386 in the table.

Since it's in the repository, is it possible to apt-get it?

---

### Post by ndefontenay on 2007-02-09
Thanks a lot for your time by the way.

---

### Post by ndefontenay on 2007-02-09
Just to confirm. It works!

---

