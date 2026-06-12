---
title: "tar: This does not look like a tar archive"
date: 2005-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by bean on 2005-08-27
henry@hbox:~$ cd /home/henry/Desktop
henry@hbox:~/Desktop$ tar vxf captive-static-1.1.5.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Read 5237 bytes from captive-static-1.1.5.tar.gz
tar: Error exit delayed from previous errors
henry@hbox:~/Desktop$

Im not sure at all what this means, can anyone help?

---

### Post by bean on 2005-08-27
:neutral: 
This is getting really anoying.  Ive been looking over google results, but even if there was a solution somewhere in there, it was beyond me.  It is appearing with all tar files im using.

---

### Post by bean on 2005-08-27
Hmm, found a workaround.

error:
tar: Archive contains obsolescent base-64 headers

I searched on the net and found lots of people running into this bug. Here is a simple solution that works for me:
gzip -d file.tar.gz
and then do
tar -xf file.tar
And it extracts without errors.

---

