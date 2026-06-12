---
title: "Howto Avast antivirus on AMD64"
date: 2006-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by juanjo4x4 on 2006-08-09
Hi!

This is my first "howto", and it's very easy:

1. $apt-get install linux32 libc6
2. Download the .deb package from [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)
3. Register you license from [http://www.avast.com/i_kat_207.php?lang=ENG](http://www.avast.com/i_kat_207.php?lang=ENG)
4. Install it: sudo dpkg --force-architecture -i avast4workstation_VERSION_i386.deb

Everytime you wanna scan: $linux32 avastgui


That's all folks

---

### Post by Kilz on 2006-08-09
> **juanjo4x4 said:**
> Hi!

This is my first "howto", and it's very easy:

1. $apt-get install linux32 libc6
2. Download the .deb package from [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)
3. Register you license from [http://www.avast.com/i_kat_207.php?lang=ENG](http://www.avast.com/i_kat_207.php?lang=ENG)
4. Install it: sudo dpkg --force-architecture -i avast4workstation_VERSION_i386.deb

Everytime you wanna scan: $linux32 avastgui


That's all folks
That's nice, however Linux doesn't really need anti virus. It is theoretically possible to be infected. But all concept viruses, or real ones I have ever read about require you to do something stupid. Like run as root.
If you are getting your applications in the repositories the chance of a virus is like that of getting hit by lightning 18 separate times, in an hour.

---

### Post by bbfuller on 2006-08-09
While I agree with Kilz in so far as it applies to a wholly Linux world, unfortunately I have to live in a Windows world as well. This means receiving attachments on e-mails and then passing them on, either by e-mail or on memory stick / CD / even floppy disc still in this day and age.

Under those circumstances I'd rather play sure and have AV on my machines than become known as a source of infection.

---

### Post by Kilz on 2006-08-09
> **bbfuller said:**
> While I agree with Kilz in so far as it applies to a wholly Linux world, unfortunately I have to live in a Windows world as well. This means receiving attachments on e-mails and then passing them on, either by e-mail or on memory stick / CD / even floppy disc still in this day and age.

Under those circumstances I'd rather play sure and have AV on my machines than become known as a source of infection.

If you are reciving executables attached to emails and you are forwarding them to a Windows user maybe it would be worth it. 
Depending on if the scanner is looking for Windows viruses. 
It may not be if its a linux scanner. I took a look at this and there is no auto update, or constant protection. Its just a manual command line scanner. You may be better off having the windows machine scan any media you may suspect is infected.
Anyone running Windows without antivirus has a disaster waiting to happen.

---

### Post by bbfuller on 2006-08-10
I certainly agree about anyone running Windows without AV being a disaster waiting to happen. I think anyone who gets requests to fix computers won't be surprised how often it happens though.

Actually, although I'm using an Ubuntu base, most of the time I run Kubuntu on top of it. I use Clam for my AV here and that integrates nicely with Kmail. I then run Clam manually against my data directories on a regular basis. I'm always interested to see other AV packages though so I'll be taking a look at Avast.

---

