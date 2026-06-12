---
title: "install iscan impossible for 64 bit"
date: 2007-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by JvdS45 on 2007-03-12
Hi I cannot use the iscan software and use alien, because it is a i386.rpm file. Is there someone who knows how I can install these software? Or how I can able my scanner. 
I used alien but get message it is not possible ofcourse and the tgz file sources cannot install too. It is all related to the i386 product. 

I hope someone can give me a little help for installing software or howto enable my scanner in a 64 bit environment

even I have firmware in myn /usr/lib/firmware directory but that is still not accesible I think :|

I thank for those who can help me out of this :-)

---

### Post by Kilz on 2007-03-12
> **JvdS45 said:**
> Hi I cannot use the iscan software and use alien, because it is a i386.rpm file. Is there someone who knows how I can install these software? Or how I can able my scanner. 
I used alien but get message it is not possible ofcourse and the tgz file sources cannot install too. It is all related to the i386 product. 

I hope someone can give me a little help for installing software or howto enable my scanner in a 64 bit environment

even I have firmware in myn /usr/lib/firmware directory but that is still not accesible I think :|

I thank for those who can help me out of this :-)

Use the XSane image Scanner application. You can find it in Applications > Graphics . If it isnt installed it is in apt/synaptic. You will have to do some setup.
[Here is a good link for information on how to install applications in Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/").

---

### Post by JimmyME on 2007-03-12
JVDS45,

I was unable to get my Epson scanner working with USB but it works great with Firewire.  

You need to add the line "scsi EPSON" to the epson.conf file and comment out everything else.  I run XSANE through GKSUDO so I don't have any permissions problems.

I'm very happy with the scans through XSANE.  I'm scanning some old black and white negs and adjusting the dynamic range in XSANE from the preview and it produces great, high-res scans.

Jim

---

