---
title: "Office 2003"
date: 2013-11-17
forum: Wine
---

### Post by cmcanulty on 2013-11-17
I have been trying to install Office 2003 with a good key with no luck. The CD mounts all locked so I copied the files to my Documents and changed permissions to me still no luck. It did install OK from sudo nautilus but it is nowhere to be found. I am running Ubuntu 12.04 classic, thanks

---

### Post by Toz on 2013-11-17
> I have been trying to install Office 2003 with a good key with no luck.What error messages do you get?

> It did install OK from sudo nautilus
You shouldn't install wine programs using sudo ([reference]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014")), you'll just create headaches for yourself. What are the current permissions of your ~/.wine folder?

There is an Wine Office 2003 How-To [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214").

---

### Post by deadflowr on 2013-11-17
Just open "uninstall wine software" then
Click install then
Click the dropdown where normally it has the username, and in the dropdown click "My Computer".
The disk should be listed among these choices.
Click on the disk and then select the Install.exe.
It should run the installation from there.

The disk is read-only which is why it has locks on it.
as long as it doesn't have an X, it should be good to go.

---

### Post by cmcanulty on 2013-11-17
Ok that worked thenks but now when I try to activate it says I have no connection to internet but I am on for sure.

---

### Post by electrohandyman501 on 2013-11-17
I may be off base with this, but I'm thinking that Office '03 has followed the trail of XP, no longer using online activation.
Read this KB article.
[http://support.microsoft.com/kb/903275](http://support.microsoft.com/kb/903275)

edit: undated the article link.

---

### Post by deadflowr on 2013-11-18
> **cmcanulty said:**
> Ok that worked thenks but now when I try to activate it says I have no connection to internet but I am on for sure.

Do you any firewalls running?
Or set anything to make wineapps not internet connectable?

---

### Post by cmcanulty on 2013-11-18
no

---

