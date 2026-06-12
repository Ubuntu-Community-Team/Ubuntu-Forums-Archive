---
title: "MS-Outlook Initial Setup failure - &quot;The connection to Microsoft Exchange is unav...&quot;"
date: 2012-08-30
forum: Wine
---

### Post by malshant on 2012-08-30
I am using Ubuntu 12.04, PlayOnLinux 4.1.7 and POL automatically downloaded and used Wine 1.5.3.

MS Office 2010, properly got installed and runs.

But I am trying to configure Outlook to connect to enterprise Microsoft Exchange but I get the following error "The connection to Microsoft Exchange is unavailable. Outlook must be online or connected to complete this action."

Seeing various forums I have even added updated ntlm authentication configuration in smb.conf. But still no change.

I badly require to fix this.

Somebody please help.

-malshant

---

### Post by Gordonbp531 on 2012-08-30
You are connected to the domain in which the Exchange server resides?

---

### Post by dcstar on 2012-08-30
> **malshant said:**
> I am using Ubuntu 12.04, PlayOnLinux 4.1.7 and POL automatically downloaded and used Wine 1.5.3.

MS Office 2010, properly got installed and runs.

But I am trying to configure Outlook to connect to enterprise Microsoft Exchange but I get the following error "The connection to Microsoft Exchange is unavailable. Outlook must be online or connected to complete this action."

Seeing various forums I have even added updated ntlm authentication configuration in smb.conf. But still no change.
........

SMB has **absolutely nothing** to do with Exchange, that is File Sharing on *your* machine.

Exchange requires a clear network connection with no firewalls interfering, if you cannot ping the Exchange server then Outlook will not work.

---

### Post by Toz on 2012-08-30
Moving to the Wine subforum.

---

### Post by malshant on 2012-08-30
Yes. I am able to ping to the domain server. Infact Evolution works.

---

### Post by malshant on 2012-08-30
- You are connected to the domain in which the Exchange server resides?
 
Do you main the Windows domain? If unix domain, then yes I am in the same domain and I am able to ping the exchange server.

---

### Post by malshant on 2012-08-30
> **toz said:**
> moving to the wine subforum.
 
ok

---

### Post by Mark Phelps on 2012-08-30
The link below is to a page oin the WineHQ site dealing with Outlook -- perhaps it can help:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161&iTestingId=71137]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161&iTestingId=71137")

---

### Post by malshant on 2012-08-31
> **Mark Phelps said:**
> The link below is to a page oin the WineHQ site dealing with Outlook -- perhaps it can help:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161&iTestingId=71137](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161&iTestingId=71137)

Thank you for the link. Let me try that.

---

