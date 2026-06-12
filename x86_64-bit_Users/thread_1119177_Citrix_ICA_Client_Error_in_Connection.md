---
title: "Citrix ICA Client Error in Connection"
date: 2009-04-07
forum: x86 64-bit Users
---

### Post by trungd_t on 2009-04-07
Hi all,

I'm able to successfully installed the latest Citrix ICA client on my Ubuntu 8.10. I followed the other threads on installing the client, and I've checked all is working fine. I can see the citrix receiver under "Applications -> Internet -> Citrix Receiver", and I can even launch it.

Given that, I VPNed to my work, and login to Metaframe XP. However, I get the "Error In Connection" dialog, when I try to launch an application like ClearQuest. The dialog says "Network or dial-up problems are preventing communication with the server", and then tries to reconnect.

Here's a screen shot of the error.
[IMG]http://i401.photobucket.com/albums/pp92/mrt_foto/MetaframexperrorinconnectionScreens.png[/IMG]

What am I missing? I've looked and googled the web, but have not found anything similar to this. On Windows, the ClearQuest application launches without any issue. I've completely switched over to using Linux (Ubuntu) on my laptop, but this is a problem, and I have to access Windows. ](*,)

Any help would be greatly appreciated. 

Best regards,
Trung

---

### Post by trungd_t on 2009-04-09
Does anyone know if there is an ICA client log that's kept some where on the system? I've looked at the /var/log, /usr/lib/ICAClient, and $HOME/.ICAClient, but there's nothing. Is there a way to run the client verbose or debug mode?

Really appreciated for any information how to move further. I'm at a dead end, and am trying to find if there's any other leads to follow. I've been browsing other threads (including the citrix community), but nothing has shed any light on this issue.

Btw, where can I download the version 10.6 of the ICA client? I've been to the Citrix download site, and it always give me the version 11 to download. Others have mentioned using 10.6 successfully, so I want to give that a try.

Thank you.

Trung

---

### Post by Tomàs M. on 2009-04-22
Same strange problem here, but only in a wireless connection; it works well on a wired connection :confused:

---

### Post by john_navarro on 2009-04-23
What I do after installing the client is set the server prefs to just use TCPIP - perhaps that might help.

1) Launch wfcmgr    (/usr/lib/ICAClient/wfcmgr)

2) Tools -> Settings

3) Select Server Location from pulldown on top

4) For Network Protocol select the one that says "TCPIP" only - not "TCPIP + HTTP" or "SSL/TLS + HTTP"

---

### Post by trungd_t on 2009-05-04
I will definitely try the hardwire to see if that works.

I've already tried setting the TCPIP only as well, but it didn't work. I can try again as you've suggested. It's weird that you don't have to do anything on a Windows box, and it works.

Thanks
Trung

---

### Post by Tomàs M. on 2009-05-04
First I had this problem only in my EEE (Jaunty), after a few days in the desktop too (Intrepid). 
A workaround that works for me is the Window$ Citrix client running in wine.

Hope that helps, and sorry for my English.

---

### Post by cendo on 2009-08-04
update to version 11 helps (with 10.6. I had this problem)

---

