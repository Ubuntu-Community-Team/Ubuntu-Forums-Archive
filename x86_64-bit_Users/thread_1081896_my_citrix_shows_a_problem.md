---
title: "my citrix shows a problem"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by ShankarT on 2009-02-27
Hi 
can any on help me over this when i try to run anything on citrix it shows an error. 
You have not chosen to trust "/C=US/ST..........."the issuer of server's security certificate (SSL error 61)

---

### Post by Reeman on 2009-02-27
Update your current security certificates. I have had to do this before with 32bit Ubuntu running the linux citrix client. For the life of me I can't remember how. Could be that you have a security policy setting in your browser that screws up the citrix client's ability to work. 

Your web browser will balk at certificates sometimes if it gets confused about one it can't find if your policies are too strict. Ubuntu updates the blacklist when availble through automatic updates and your web browser's security policy will determine how the web browser and therefore the citrix web client reacts.

---

