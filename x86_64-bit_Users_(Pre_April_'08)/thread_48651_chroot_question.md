---
title: "chroot question"
date: 2005-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Irony on 2005-07-13
I'm installing chroot as per;

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)

However I am at the following stage;

[PHP]Setup the chroot 
Open a Terminal. 
Type: sudo apt-get install dchroot debootstrap 
Type: sudo mkdir /chroot/ 
Type: sudo gedit /etc/dchroot.conf 
Add this line to the end of the file, save and exit: hoary /chroot 
Type: sudo debootstrap --arch i386 hoary /chroot/ http://archive.ubuntu.com/ubuntu 
Wait for the installation to complete. 
Type: sudo chroot /chroot/ 
Type: dpkg-reconfigure locales 
Select your proper locale. [/PHP] 
How do I determine what my proper locale is?

---

### Post by dataw0lf on 2005-07-13
A locale is used to determine language, numeric system, monetary system, etc.  For example, I live in the USA, and am most familiar with the American systems, so I use the locale 'en_US'

---

### Post by FluffyElmo on 2005-07-13
Microsoft (yes, Microsoft;)) has a list of the various locale codes and the languages they correspond to. Linux seems to use the same codes so the list may be helpful to you anyways...

[http://msdn.microsoft.com/workshop/author/dhtml/reference/language_codes.asp](http://msdn.microsoft.com/workshop/author/dhtml/reference/language_codes.asp)

---

### Post by Irony on 2005-07-13
Thanks for replies.

I figured it was something to do with language but I wasn't sure which of the en settings to select but the Microsoft listing looks pretty straighforward - I'm in XP at the moment so I'll see if I can finish the chroot installation when I'm back in ubuntu.

---

