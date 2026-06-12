---
title: "Printing from firefox32"
date: 2006-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaatmx on 2006-06-08
Is it possible to print from firefox32? or this is a payload for runing 32bit apps under a 64bit enviroment?
G.

---

### Post by Kilz on 2006-06-08
[QUOTE=gaatmx]Is it possible to print from firefox32? or this is a payload for runing 32bit apps under a 64bit enviroment?
G.[/QUOTE]

Im running 32 bit firefox on 64 bit dapper and was able to print a page.

---

### Post by John Jason Jordan on 2006-06-08
[QUOTE=Kilz]Im running 32 bit firefox on 64 bit dapper and was able to print a page.[/QUOTE]
Me too. But the page is not the web page I was trying to print. What I get is a one-sheet error message telling me my PostScript printer needs to be replaced with a newer PostScript printer because it's too old to print to. Note, however, that none of my other apps have a problem printing to the same printer. That is, sometimes features are missing (tray selection, duplexing, resolution settings, etc.), but I always get the output.

---

### Post by Kilz on 2006-06-08
[QUOTE=John Jason Jordan]Me too. But the page is not the web page I was trying to print. What I get is a one-sheet error message telling me my PostScript printer needs to be replaced with a newer PostScript printer because it's too old to print to. Note, however, that none of my other apps have a problem printing to the same printer. That is, sometimes features are missing (tray selection, duplexing, resolution settings, etc.), but I always get the output.[/QUOTE]

Can you print to a file?

---

### Post by John Jason Jordan on 2006-06-09
[QUOTE=Kilz]Can you print to a file?[/QUOTE]
Yes, no problem. It creates mozilla.ps. The only thing I can find that will open it is PostScript Viewer. However, having opened it in PostScript Viewer, if I then print it I get the same one page of error messages.

The error message page says:

The PostScript interpreter in your printer is 2014.108
This printout requires at least version 2015 or greater.
To make a Unix/Linux Gecko browser (e.g., Netscape or Mozilla) produce output that will work on any level 2 interpreter change the print command from
lpr [OPTIONS]
to (all on one line)
<very long line that I could never retype accurately here>

The line that I skipped starts with "gs," which I think sends the file through GhostScript. I've never been able to get GhostScript installed. Also I don't really want GhostScript installed. 

The printer in question is an HP Laserjet 8000. This printer uses PostScript emulation that HP licenses from Xionics. It has the latest firmware. I also have an HP Laserjet 5Si that is 8 years old. It also has PostScript, but genuine Adobe. Its interpreter is version 2.0013. Firefox prints to it perfectly without a complaint.

Is there a way to send the mozilla.ps file directly to the printer without opening it in an application first?

---

