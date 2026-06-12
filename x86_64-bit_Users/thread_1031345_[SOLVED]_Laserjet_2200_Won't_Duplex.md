---
title: "[SOLVED] Laserjet 2200 Won't Duplex"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by wmichaelb on 2009-01-05
Hi, I've installed Intrepid 64-bit on a separate partition, and I cannot get my Laserjet 2200 to print duplex. It works fine on the 8.04 32-bit installation, so it's not the printer or the computer. I've tried both the default CUPS and the HP driver/system. Neither will offer the duplex option in Page Setup; it's one-sided only. HP of course offers no public support for Linux printing issues. Has anyone else seen this problem? Solution?

Thanks in advance!

---

### Post by wmichaelb on 2009-01-10
I figured it out! I went to System/Administration/Printing, and after fiddling around a bit, found that if I right-clicked on the printer icon, I got a new dialog box. I clicked on Properties, Installable Options, and added the duplex option, and now I'm good to go. I'm happier; Ubuntu 64-bit is much faster on this system!

FYI for anyone else who has this or a similar problem.

---

### Post by LarryGJ on 2009-09-11
Hi,
 
I followed your instructions Michael B. of Cincinatti. I made the changes, applied them and then tried to print double sided. It didn't work!
 
My system now shows the duplex option as selected, but when I go to the Print settings, it shows as single sided. I tried rebooting after making my selections, but that did not help.
 
If I had any hair, I would be tearing it out.
 
Larry

---

### Post by wmichaelb on 2009-09-11
Larry: I'm no printer expert, but just to review: 

- Click on System/Administration/Printing
- A dialog box should pop up. Right-click on the printer of concern
- Click on Properties, and then Printer Options
- Set the 2-sided printing option to "Flip on Long Edge (Standard)"
- Click on Apply first, then OK.
- Open an application that will print
- Click on File/Print
- When the dialog box opens, select the same printer that you had adjusted 
  above. Click on Page Setup
- What does the "Two Sided" bar say?

---

