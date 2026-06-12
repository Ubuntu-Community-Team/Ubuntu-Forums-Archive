---
title: "from i386 to AMD64 printing stopped working."
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mp035 on 2007-10-29
Hello All,
I have been on this for hours, and have done the forum search, which normally works for me, but I have a tricky problem this time, and I hope that there is a linux-head out there with enough knowledge and experience to fix this problem.  

 I have 2 Brother printers, and got both of them working under SuSE 10, Dapper-i386, Edgy-i386, Feisty-i386, and Gutsy-i386.  I have a new machine and installed Gutsy-i386, and got both printers working.

after about 1 day I discovered that the processor I was using (intel 2160) was a 64 bit cpu, so I decided to upgrade to gutsy-AMD64, from a clean HDD, using a CD.

The install went fine.

I have just tried to get my printers working.  Driver install shows no problems, and the printing interface shows no errors, but nothing comes out of the printers when I try to print, the jobs even show as "completed" in the "Document Print Status".

The printers are:
1) Brother MFC-640CW using  mfc210clpr-1.0.2-1.i386.deb wrapped in  cupswrappermfc210c_1.0.0-1_i386.deb from the brother website.  This printer does not work on USB, or wifi.  It worked on wifi under gutsy-i386 on the exact same machine.

2) Brother HL-2040 using brhl2040lpr-2.0.1-1.i386.deb wrapped in cupswrapperHL2040-2.0.1-2.i386.deb, on USB.

The packages were installed with the --force-architecture option as per the brother website, and the command  ```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter/ 
``` 
returns 
```
cp: `/usr/lib/cups/filter/brlpdwrapperMFC210C' and `/usr/lib64/cups/filter/brlpdwrapperMFC210C' are the same file
```
because /usr/lib, and /usr/lib64 are linked in the gutsy install.

I know this is a squirmy one, but I am confident that someone out there is smarter than the average bear :)

---

### Post by mp035 on 2007-10-29
P.S. lib32stdc++6 and ia32-libs are installed.  Thanks to anyone with help, but I think you'd have to be ........ well, an ubuntu genius to sort this one.  Google finds nothin',  Thanks again.  
Mark.

---

### Post by mp035 on 2007-10-29
Hi again all, I switched of my PC and printer, went to bed, then fired it up this morning and BAM! printing works!!!!

Sorry to anyone following this thread hoping for an answer, I don't have one :(

Happy Ubuntu-ing!

---

