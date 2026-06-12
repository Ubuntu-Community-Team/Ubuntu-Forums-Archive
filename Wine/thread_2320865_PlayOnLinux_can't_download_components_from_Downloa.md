---
title: "PlayOnLinux can't download components from Download.Microsoft.com"
date: 2016-04-18
forum: Wine
---

### Post by Richard_Romick on 2016-04-18
Greetings,

I have been having problems in PlayOnLinux downloading files from the download.microsoft.com servers.  When I try to manually download the file, the domain download.microsoft.com can't be reached.  If I go to [https://www.microsoft.com/en-us/download/details.aspx?id=30653](https://www.microsoft.com/en-us/download/details.aspx?id=30653), click the download button, then click the link "If your download does not start after 30 seconds, Click here", I get "Server not found".  Would you try the link also and see if you get the same result?  Thank you,

---

### Post by Richard_Romick on 2016-04-18
So, it appears that download.microsoft.com works fine on my Windows 7 virtual machine, but not in Ubuntu.  I'm guessing there is something Windows related I need to have to access download.microsoft.com, since it is Microsoft after all.  I am googling the answer, but so far no luck.  Any ideas?

---

### Post by Richard_Romick on 2016-04-18
So, I managed to narrow it down to a DNS issue.  When I set my connection to use the DNS server 4.2.2.4, everything was fixed.

---

