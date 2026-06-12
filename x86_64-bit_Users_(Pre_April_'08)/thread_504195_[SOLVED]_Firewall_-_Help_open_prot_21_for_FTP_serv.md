---
title: "[SOLVED] Firewall - Help open prot 21 for FTP serving"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-18
I was never able to find a GUI ftp server for Linux, however Serve-U under WINE installs just fine and is reported to work perfectly under WINE.

My problem is that I can't put the server on-line and I'm 90% sure it's because I don't know how to open port 21 under Firestarter.

I'm this close " " to having it function as needed but I'm not there yet.

Any help on this issue would be great.

---

### Post by Claus7 on 2007-07-19
Hello,

In order to open port 21 in your firewall using Firestarter you should open it as root. Give your password and a window will open. Then you will see three tabs in a row. Go to the Policy tab. There go to the second "area" where it says just above, Allow service.
Do a right click and select add rule. There type the number of the port you want to open, apply it and there you are!

I hope that the port you want to open is only via the firewall and not via your adsl modem as well. You might have to do the same to your modem as well via port forwarding.

I hope that helps,
Regards!

---

### Post by crjackson on 2007-07-19
Got it thanks - I'll try it out tomorrow.

---

### Post by PaulFr on 2007-07-19
AFAIK, you need to open more than port 21 to get FTP service working. See first paragraph of Overview section in **[http://en.wikipedia.org/wiki/FTP](http://en.wikipedia.org/wiki/FTP)**. 21 is typically the port where the client connects (control stream), and then when a transfer is attempted, a second data stream needs to be opened (active, passive and extended passive FTP connections differ in the details of these connections).

---

### Post by crjackson on 2007-07-20
> **PaulFr said:**
> AFAIK, you need to open more than port 21 to get FTP service working. See first paragraph of Overview section in **[http://en.wikipedia.org/wiki/FTP](http://en.wikipedia.org/wiki/FTP)**. 21 is typically the port where the client connects (control stream), and then when a transfer is attempted, a second data stream needs to be opened (active, passive and extended passive FTP connections differ in the details of these connections).

I give up on this one, I just can't get it working.  Guess I'll just have to boot into windows for FTP serving.  I was really wanting to avoid that, but it seems to complicated for me on this one.

---

### Post by John.Michael.Kane on 2007-07-21
These may help.
[HOWTO : Create a FTP server]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp")
[ HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661&highlight=ftp")

---

### Post by crjackson on 2007-07-21
> **SD-Plissken said:**
> These may help.
[HOWTO : Create a FTP server]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp")
[ HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661&highlight=ftp")


This sounds great.  I'll be checking this out in a few days.  Thank you so very much...

---

### Post by crjackson on 2007-07-22
I installed GPROFTPD and it's working like a charm so far.  This seems to be what I was looking for.  I need to do some more tweaking and testing but it's working internally (other systems connected to the same network).

Thanks for your assistance.  I was about to write this project off...

---

