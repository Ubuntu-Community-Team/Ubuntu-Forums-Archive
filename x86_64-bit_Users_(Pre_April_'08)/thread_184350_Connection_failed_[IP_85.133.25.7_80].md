---
title: "Connection failed [IP: 85.133.25.7 80]"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjod on 2006-05-29
Hi all;

During install of Ubuntu 6.06 64-bit on an Acer laptop, I got a message indicating that security updates could not be obtained. Installation continued after acknowledging the message.

However, when trying to run the update manager ("70 updates available") they all fail :(  with messages similar to this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.55-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.55-1ubuntu3_amd64.deb)
  Connection failed [IP: 85.133.25.7 80]

Only the URL changes. The IP address is valid, but only has a root directory.

Any ideas on that?:-| 

Thanks!

---

### Post by gerbman on 2006-05-29
> **tjod]Hi all said:**
> http://us.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.55-1ubuntu3_amd64.deb[/url]
  Connection failed [IP: 85.133.25.7 80]

Only the URL changes. The IP address is valid, but only has a root directory.

Any ideas on that?:-| 

Thanks!Can you ping 85.133.25.7? I can click the link in your post and download the package directly, can you do that? If not, what's the output of "ifconfig" and what does your /etc/network/interfaces file look like?

---

### Post by tjod on 2006-05-29
[QUOTE=gerbman]Can you ping 85.133.25.7? I can click the link in your post and download the package directly, can you do that? If not, what's the output of "ifconfig" and what does your /etc/network/interfaces file look like?[/QUOTE]


Yes, I can ping the IP, and I can open the "/" page in the browser, manually.  I can also download them manually, but am quite new at Linux and wouldn't have the foggiest idea what to do with 70+ downloads.

... and I guess my main concern is ... Is it fixable?

Thanks!

---

### Post by tjod on 2006-05-30
[QUOTE=gerbman]Can you ping 85.133.25.7? I can click the link in your post and download the package directly, can you do that? If not, what's the output of "ifconfig" and what does your /etc/network/interfaces file look like?[/QUOTE]
Tried it again this morning from a different network. Now working. 

The problem might be with the first network or maybe someone fixed something elsewhere. In any case, I'm glad it's working. Thans for your help.

---

### Post by gerbman on 2006-05-30
[QUOTE=tjod]Tried it again this morning from a different network. Now working. 

The problem might be with the first network or maybe someone fixed something elsewhere. In any case, I'm glad it's working. Thans for your help.[/QUOTE]Cool. No problem.

---

