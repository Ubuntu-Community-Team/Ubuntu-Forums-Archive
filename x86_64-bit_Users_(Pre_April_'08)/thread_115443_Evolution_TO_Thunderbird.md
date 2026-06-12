---
title: "Evolution TO Thunderbird"
date: 2006-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmeier on 2006-01-10
I am running Breezy PPC on a powerbook.  I have been using Evolution for a while, but don't use the to do list or calendar all that much and would like to switch to Thunderbird.  I have done a couple of google searches and looked here on ways to move my mail over.  They all talk about the mbox format, but when I get to the same folders they are talking about it looks as if my file is an xml file and not mbx.  Is there a way to make this transfer happen?  I have Evolution 2.4.1 and Thunderbird 1.0.7.  Any help is appreciated.

---

### Post by callipeo on 2006-01-11
I did the switch some time ago; here's what I did. Suppose you want to import the evolution (v)folder foo in the thunderbird folder bar. First select all the messages in foo from evolution, then  click File->Save Message... and save them in the file "bar". Now open thunderbird and create the folder bar, then close thunderbird and move the file "bar" you exported from evolution in ~/.mozilla-thunderbird/<code>.default/Mail/Local\ Folders/ (of course you can change "Local\ Folders" to any of your accounts if you want). On the next start thunderbird should have imported the messages. Note that you should call "Inbox" the file exported from evolution, if you want to import the messages in the default Inbox thunderbird folder.

Hope this helps.

---

### Post by tmeier on 2006-01-11
Thanks callipeo that worked like a charm

---

### Post by Gordonbp531 on 2006-01-12
[QUOTE=tmeier]Thanks callipeo that worked like a charm[/QUOTE]

For future reference, an even quicker way is just to copy the directory called .evolution/mail/local directly into your TBird profile. You then just delete all the unwanted folders (for some reason Evolution creates FOUR files and folders per mail box - why I have no idea), and there you are!

---

### Post by Jose Catre-Vandis on 2006-06-04
Thanks, needed this :-)

---

