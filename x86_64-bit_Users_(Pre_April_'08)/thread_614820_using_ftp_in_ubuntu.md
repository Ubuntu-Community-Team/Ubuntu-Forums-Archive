---
title: "using ftp in ubuntu"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by temptation on 2007-11-16
Hi all

I am new in using UBUNTU and I have problem in using ftp. 
I can't connect to the ftp.unc.edu from terminal, gFTP and filezila.
the command I use in terminal is ftp ftp.unc.edu, may u help me in this?

---

### Post by ofb on 2007-11-17
Skip gFTP and Filezilla (though they should work) - the Konqueror file manager has FTP built in. Just enter ftp.unc.edu in the address bar.

For information on using terminal FTP (if you're still curious), enter 'man ftp' for the man page.

EDIT: If you're new to Konq, I should mention two non-obvious configurations. F9 toggles the side panel, and you need to enter 'trash:/' in the address bar to access the trash bin. It'll remember that in the address bar drop-down for the next time you want it.

---

### Post by CanonKen on 2007-11-17
I had trouble with filezilla that I never got to the bottom of so I switched to [fireFTP]("http://fireftp.mozdev.org/") - a firefox add-on

---

### Post by Ehtetur on 2007-11-17
Any of the applications mentioned in this post will work..
Assuming you have a valid id & password, :twisted: your admin may have set up the site to lock an id after 3 or 4 unsuccessful logon attempts.

Also, depending on the site's contents. the admin may have configured the ports so all ftp access is blocked except ftp via ssh... If that's the case, just click on SSH2 -(in gftp) before connecting.

---

