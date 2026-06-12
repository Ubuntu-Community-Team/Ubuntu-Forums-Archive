---
title: "Brother MFC 420CN does not print, but jobs dissapear"
date: 2009-08-23
forum: x86 64-bit Users
---

### Post by endersbean3k1 on 2009-08-23
Hi guys, trying to set up my first Ubuntu 64bit installation. I'm working with 9.04.

I installed the drivers for my Brother MFC 420CN from the brother website. I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=590793") and [here]("http://ubuntuforums.org/showpost.php?p=3835451&postcount=61"). I feel it is necessary to note that I initially installed the 440CN drivers by mistake. To undo this all I did was go to System->Administration->Printing, right-clicked, and deleted the printer. I imagine this left the 440 drivers installed, but supposed that the few MB hard drive space weren't worth the hassle of finding the files to delete.

Anyhow, here's whats going on. I access my CUPS page on localhost and the printer appears, everything is fine. If I attempt to print a test page or a document when the printer is not plugged in, the job queues as normal. When the printer is then plugged in, the test page job disappears or the document job is completed, accompanied by the little message in the upper-right hand corner of the screen saying so. If I print a test page with the printer plugged in, I never see the job, it leaves the queue so fast. If I print a document, it almost instantly tells me the job was completed. Nothing ever prints. 

I have successfully printed a document off of a Vista machine to verify that the printer indeed works.

In the past, in a 32bit Ubuntu installation, I had this problem occur if I tried to print too much of a PDF file. Printing the PDF one page at a time resolved the issue though. Shouldn't be relevant, just... rambling I guess.

Any ideas? If I can't set this up... I'm sure I can use a VM/dualboot/some-grossly-hackish-workaround to fix this up, but that would really suck.

Willing to fresh-install ubuntu if you think it might help, not willing to back down to 32 bits (6 gigs of ram should be USED).

Anyways, thanks for the help guys.

---

### Post by garvinrick4 on 2009-08-24
Add a new printer "will be brother mfc 420cn2" by default. Make sure
you add the correct driver. Delete original printer and make #2 default printer. Worked for me. 64 bit user.

---

### Post by endersbean3k1 on 2009-08-24
I get the same behavior out of the second printer. :(

---

### Post by endersbean3k1 on 2009-08-25
*bump*

No ideas? I really need this set up. If nothing is forthcoming I think I'll install Ubuntu again tonight and try again, just for that fresh pallet.

---

### Post by endersbean3k1 on 2009-08-25
Ok, figured it out and now I feel foolish. I installed lib32dc++6 AFTER dpkg-ing the Brother drivers, because I couldn't find them at first :lolflag:. 

I guess I thought it wouldn't matter for before or after because I didn't get any sort of error during the installation, which I would expect if that's when the package was required. Although honestly, I don't really understand the functions of these packages very well at all.

So all I did was run the dpkg on the drivers again and now it works :guitar:.

---

### Post by rickypicky on 2009-11-03
I am having the exact same problem.  I have installed Ubuntu 9.10 and the MFC-7420 drivers from the Brothers website.  No errors with the install.  

Whenever I print, the CUPS page says everything is fine and job has finished - but nothing comes out of the printer.

My question to you is:

You state lib32dc++6 needed to be installed.  Do you mean libstdc++?  I cannot find any reference to lib32dc++6.

Thanks in advance!

---

