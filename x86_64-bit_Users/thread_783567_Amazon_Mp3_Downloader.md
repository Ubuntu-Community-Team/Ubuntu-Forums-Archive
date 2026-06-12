---
title: "Amazon Mp3 Downloader"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by natibo on 2008-05-05
I have had trouble downloading music with the Amazon MP3 Downloader.  It worked under Gutsy, but not under Hardy.  I did the force install and get libs thing.  It launches OK but simply states under the status:

"Can't connect.  Check your internet connection and retry download."

This is a shame because this software was going to make iTunes unnecessary.

---

### Post by keeler1 on 2008-05-06
It did not work for me either.  I used the same -force as well.  Then again it was compiled for 32 bit gutsy.  It could just not be forward compatible or it might be a 64 bit thing.

---

### Post by Julius on 2008-05-06
I think this has to do with that bug that prevents 32-bit apps from connecting to the internet.


Try again after installing this:
```
sudo aptitude install lib32nss-mdns
```

---

### Post by natibo on 2008-05-06
That worked.

Thanks.

---

### Post by seehad on 2008-12-08
That worked for me too.  Goodbye iTunes!

---

### Post by thefrozenpenguin on 2008-12-15
I followed what was above the downloader would not start, when run from CLI I get the following, I have included the output from the forced install also:

iain@iain-desktop:~$ sudo dpkg -i --force-all ~/Desktop/amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 163850 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.4-1 (using .../iain/Desktop/amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up amazonmp3 (1.0.4-1) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


iain@iain-desktop:~$ amazonmp3
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
iain@iain-desktop:~$ 


I checked and libgtkmm-2.4-1c2a is installed.

Any thoughts?

---

### Post by oldos2er on 2008-12-15
Try this software: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

 It works very well for me, and I had all but given up on on Amazon MP3s.

---

### Post by thefrozenpenguin on 2008-12-15
Brilliant thanks for that.

---

