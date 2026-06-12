---
title: "Server Setup"
date: 2005-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by docmur on 2005-06-20
Hello

I'm new to Ubuntu and need some help getting it set up as my server.
Let me explan the installation first.  I selected the server install and it went okay.  Now I'm faced with the login screen.  I can log into the account that it setup but I can not log into root.   What is the root password.  I tryed the user accounts password but that did nothing.  My second question is how would I set it up so that the windows xp machine will see the server and let me save to it as a network drive.  

Thanks DOCMUR

---

### Post by FluffyElmo on 2005-06-20
Quick reply...

1. By default the root account is disabled. You can use *sudo* to run programs as root. You can set a root password if you want to enable root logins.
2. You have to install and configure samba to add Windows file sharing support.  

You can find out how to do these things (and many more, you'll want to install ssh access I assume) at the Unofficial Ubuntu Guide: [http://ubuntuguide.org/](http://ubuntuguide.org/) 

Hope this helps get you started, Good Luck and have fun!

---

### Post by docmur on 2005-06-20
Okay I got the ssh,root,and samba on the ubuntu server.  Now I need help with getting windows to see the server can u help me there

---

### Post by FluffyElmo on 2005-06-20
Two quick questions...What is your network layout? (ie a simple 2 computer setup or do you have a domain controller?) What version of Windows are you running? 

I don't have a Windows box at home, so this is from memory, but if on the Linux side you've installed Samba, setup a network user in Samba and shared a directory...from a Windows command line try:
```
net use drive_letter: \\server\folder /USER:username
```
For example to map drive* f:* to shared folder *files* on server *tigger* with user *elmo*:
```
net use f: \\tigger\files /USER:elmo
```

If this doesn't work then there are a few things that come to mind:
Try the Linux boxes IP address for servername.
TCP/IP and NetBIOS have to be enabled on Windows.
Try disabling your Windows firewall, the XP firewall blocks file sharing by default.

But try it and if you get errors post back and we may be able to narrow the problem down. Good luck...

---

### Post by docmur on 2005-06-20
The one box is ubuntu and the other is windows xp 64 bit

---

### Post by FluffyElmo on 2005-06-21
Maybe try sharing a folder in Windows then and see if you can access it from Ubuntu. In Ubuntu, click the menu item 'Places' then 'Network Servers'. After a short pause you should see an 'Windows Network' icon, click it to browse workgroups and computers. 

In Windows, make sure that TCP/IP and File and Printer Sharing are installed...

   1. Right-click on Network Neighborhood and select Properties.

   2. Right-click on Local Area Network and select Properties.

   3. If the protocols are in the list stop, otherwise select Add.

   4. Highlight protocol and select Add.

   5. Highlight Internet Protocol (TCP/IP) and select Add.

   6. Highlight File and Printer Sharing for Microsoft Networks and select Add.

   7. The protocol should install and return to the Local Area Connection Properties window.

---

### Post by docmur on 2005-06-22
Okay but I used the server install so there's no Desktop only shell how would I find this folder.

---

### Post by FluffyElmo on 2005-06-22
Oops, try *smbclient -L servername -U username* from the command line.

---

