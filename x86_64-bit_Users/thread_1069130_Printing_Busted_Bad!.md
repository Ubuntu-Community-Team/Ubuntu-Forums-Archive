---
title: "Printing Busted Bad!"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by yyyc186 on 2009-02-13
Less than two weeks ago I was able to print both the PDF of my new novel and print it from inside OpenOffice3.  Since then, several updates have happened as part of the automatic update cycle.  I remember seeing a CUPS update and a C library update.  Guess what?  I tried printing today and some of the PDF software could print to my Lexmark Optra S 1855 single sided only, no matter how I set the duplex options.  Those were the better working of the applications since OO simply spooled some kind of gibberish the printer tossed into the bit bucket.  KWord was able to print in duplex though.  Okular and Document Viewer were simply wasting CPU cycles and network bandwidth.

I'm having to print from Windows Worsta since I have to get a copy off to a reviewer and don't have time to see if KWord and OO are 100% compatible with their renditions of ODF.

---

### Post by cariboo on 2009-02-13
Could it be that the ppd changed?

Jim

---

### Post by yyyc186 on 2009-02-13
I re-installed the printer thinking that was the problem as well.  No love.  The fact that this problem affects OO3 and the PDF viewers, but not KWord tells me the bug is in the C library stuff which got shoved down a week or so ago.  Yes, it could still be the CUPS update...but...that would mean KWord uses a different path through CUPS when I tell it to print via CUPS.

Sadly, my Lexmark Optra C710 went to the great beyond, so I'm down to one duplexing printer right now.  I wouldn't be surprised if nobody tested duplex printing after they made a round of changes.  A lot of printers don't even provide duplex capability.

---

### Post by yyyc186 on 2009-02-21
Yesterday's round of updates for CUPS fixed printing for Okular and Document Viewer, but OpenOffice is still unable to print duplex.  No output physically comes out of the printer, though the printer does kick on.  I can export the exact same document to PDF and print it to the printer in duplex via Okular though.

Today there is some round of updates which seems to be un-installing all things KDE from my machine.  It really p*sses me off when I'm forced to run this live-in-caves-eating-our-own-young-Gnome interface, but it infuriates me when an automatic update run in this interface starts removing KDE packages.  They just removed KWord and KOffice.  Those packages actually WORKED when it came to printing.  OpenOffice does not.](*,)](*,)](*,)

---

### Post by John Jason Jordan on 2009-02-21
> **yyyc186 said:**
> Yesterday's round of updates for CUPS fixed printing for Okular and Document Viewer, but OpenOffice is still unable to print duplex.  No output physically comes out of the printer, though the printer does kick on.  I can export the exact same document to PDF and print it to the printer in duplex via Okular though.

Today there is some round of updates which seems to be un-installing all things KDE from my machine.  It really p*sses me off when I'm forced to run this live-in-caves-eating-our-own-young-Gnome interface, but it infuriates me when an automatic update run in this interface starts removing KDE packages.  They just removed KWord and KOffice.  Those packages actually WORKED when it came to printing.  OpenOffice does not.](*,)](*,)](*,)

I have not done updates for about a month because I depend on this computer for school, but this morning I decuded to run Update Manager to see what was there. It has never done this before, but I got a popup warning:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible
This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

I use Gnome desktop, but I have a great many KDE apps installed as well. Scrolling through the list of available updates a great many were unchecked, as though those were the ones I should not be installing. Most were KDE apps or otherwise related to KDE. And the few KDE packages that were checked for update were pretty harmless things like khelpcenter and kde-icons-oxygen. 

The only things I can think of that caused this is that it is Intrepid x86-64, yet I have manually installed OOo 3.01 and made a lot of manual changes so it will be the default, yet I did not install the desktop integration package because I needed to keep 2.4.1 for the time being. Or another possibility is that I have completely removed pulseaudio in an effort to get my bluetooth headphones working as they did in Hardy. (No success yet.)

There are a total of 132 packages listed for update. I'm not going to install them just yet. I'll wait to watch the forums for a bit to see if something hairy is going on.

Also, I have had a lot of trouble printing. I have various printers and several PDF files could not be printed with Adobe Reader, although Okular printed them fine. Yet, even in Okular it will print only one copy at a time regardless of how many I specify.

---

### Post by Reeman on 2009-02-22
I have found that it is possible to run an exclusive KDE desktop complete KDE 3.5.10 and Gnome. If you install all the KDE packages and then set a separate user to run the KDE desktop. I think it has something to do with DCOP in Gnome. 

If you view all of your hidden desktop files in Gnome with nautilus then You see that the .kde has the wrong permissions! I guess this is to keep KDE pim hidden from the Gnome desktop for some reason. The KDE pim settings require installation through root.

I have my wife running the KDE desktop and I run Gnome. Her KDE PIM includes ssl info for her work. She can duplex print no problem ...I cannot with the Lexmark. So I guess that if you run kde libs with Gnome they bork on printer duplex spooling where the .kde printer settings do not. 

So if you do not have user access to make settings changes in the hidden .kde configurations then your hosed. What I did to change this was to do a chown on the .kde in my user so that user can set config files. It worked for a music notation program (Rosegarden) when I was getting dcop errors in trying to run Rosegarden or print to pdf from Rosegarden.

It sounds like the local pdf problem is associated with lack of access to .kde when using Gnome.

---

### Post by yyyc186 on 2009-02-26
I tried changing the permissions on both the KDE and KDE4 subdirectories to match the GNOME and GNOME2 directories.  Still unable to print from OpenOffice to Lexmark printer.  I can (and could before) print just fine to my Epson Color 880.  BTW, I tested this from within KDE.

---

