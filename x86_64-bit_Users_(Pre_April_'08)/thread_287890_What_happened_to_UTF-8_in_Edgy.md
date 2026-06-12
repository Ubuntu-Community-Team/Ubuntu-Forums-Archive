---
title: "What happened to UTF-8 in Edgy?"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hajk on 2006-10-29
Just did a fresh install of 64-bit Edgy on my AMD box, specifying US English keyboard, and I notice that the default locale (also in /etc/default/locale) is "en_US.ISO-8859-15". I'm pretty sure that it was "en_US.UTF-8" on my previous 64-bit Dapper installation, just as it is in an i386 Edgy installation.

Is this not strange? Did Ubuntu not opt for UTF-8 in all its versions? What happened to UTF-8 on 64-bit Edgy?

---

### Post by fabertawe on 2006-10-30
I have 'en_GB.UTF-8'. I upgraded from Dapper rather than a fresh install of Edgy.

Paul

---

### Post by Case_f on 2006-10-30
Yes, same here. I even had a few problems with it that disappeared once I changed locale to en_US.UTF-8. I guess it's a bug...

---

### Post by HeresJohnny on 2006-10-31
I also did a clean install of Edgy, because I wanted to see if SCIM was now working for FF and OOo.  Oddly enough, it hasn't let me install any new locales and when I try to install 'language support' app from add/remove programs, it says that language support is not available for my system (meaning amd64).  What's that about?  Has anyone else had trouble installing input methods?  I need to add Korean, if that helps, and I'm perfectly fine with UTF-8.

---

### Post by kekojeep on 2006-11-01
Well, I'm having trouble on my language (brazilian portuguese, or pt-BR).. the default locale is set to pt-BR.UTF-8, everything is set to pt-BR, Swiftfox and all Ubuntu menus are in portuguese but I can't write correctly because I can't get the punctuation right, when I try to write this "á í ó" I get this "'a 'i 'o" and damn this is annoying when I want to write correctly on my language.. any suggestions??

Thanx

---

