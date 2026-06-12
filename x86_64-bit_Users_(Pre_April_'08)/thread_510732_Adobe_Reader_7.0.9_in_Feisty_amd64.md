---
title: "Adobe Reader 7.0.9 in Feisty amd64"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-07-26
Problem: The printers installed in CUPS do not appear in the drop-down list in the print dialog box for Adobe Reader. According to Adobe this feature was added in Reader 7.0.5, but I have never gotten it working, including up to 7.0.8. The printers I have installed in CUPS appear in the drop down list in print dialog boxes for all other applications, but in Reader all I get is a drop-down box that says "custom" as the only choice. Therefore, the only way to print is to use the box to the right where you can enter an lp or lpr command. Not only is this a PITA, but lp and lpr cannot access all the features of my printers.

Here is the long story of all I have done:

I started with Ubuntu amd64 back in the days of Hoary. At that time I ran a 32-bit chroot in order to run Reader. After Dapper came out I was finally able to install Reader directly in 64-bit Ubuntu and get rid of chroot. However, right from the beginning I was never able to see my printers in the drop-down box. Since then I have upgraded to Edgy and then to Feisty. And I upgraded Adobe Reader to 7.0.5 and later to 7.0.8. I always installed by running the shell script that comes in the tar.gz file.

In the process of doing all this over the years I found that I had multiple acroread files in various places, some of which were real and some of which were links. I decided this morning to do a complete uninstall and start over fresh by installing 7.0.9 which is now listed in Synaptic. I searched the entire filesystem and deleted everything relating to Reader that I found. I also removed the .adobe folder in my home directory, just in case there was some configuration issue.

Finally I installed acroread 7.0.9 from Synaptic. The installation went fine, except it failed to install a launch menu item. I launched it instead from the command line. I got an error message about PPKLite being missing, but it launched fine otherwise. Now, here's the weird part: When I go into Help > About it says it is Adobe Reader 7.0.8, not 7.0.9. Version 7.0.8 is the last version I had before I nuked everything. Evidently I didn't nuke everything. There must be some file somewhere that Reader relies on to figure out what version it is, but I'll be darned if I can find it. More important, if such a file exists, what else exists that I didn't find? Might there be something else that I should have deleted, something that is causing the problem with CUPS printers not appearing?

Since that didn't help I went back to Synaptic and did a complete uninstall. Having done so I downloaded the tar.gz file from Adobe and installed it using the INSTALL script. Again, it installed fine, although it still did not create a launch menu item. When I went to launch it from the command line I got the same error message about PPKLite, but it launched OK otherwise. And when it was up and running the Help > About still said I had 7.0.8. And the printers still do not appear in the print dialog box.

I hope someone has some suggestions, because I'm out of ideas.

---

### Post by John Jason Jordan on 2007-07-27
I have discovered some additional facts. About a month ago I built myself a brand new computer and installed Feisty amd64 as the only OS. It is a completely fresh install. I installed Adobe Reader 7.0.9 from Synaptic (after adding the extra repositories). Looking at the Help > About I find that it is also 7.0.8. I don't know what is going on, but whether you install Reader 7.0.9 from Synaptic (where it is called "7.0.9"), or whether you install from the 7.0.9 tarball that you download from Adobe, the Help > About still says you have 7.0.8.

Furthermore, the print dialog box still does not display your CUPS printers in the dropdown list. All you get is "custom" and no other choices.

So now I'm wondering if the lack of the dropdown box for CUPS printers is an amd64 issue. According to Adobe the dropdown box was added to the print dialog box in 7.0.5 for Linux. Does anyone else have Reader 7.0.5 or later installed on amd64, and does your print dialog box show a dropdown list for the printers you have installed in CUPS? Does anyone have a 32-bit version of Ubuntu installed with Reader 7.0.5 or later, and does your print dialog box show a dropdown list for printers installed in CUPS?

And also, does anyone have any version of Reader installed where the Help > About says 7.0.9? And does anyone know where the Help > About gets the version number from?

---

### Post by stmiller on 2007-07-28
Do you need Adobe Reader for specific documents? Or can you try evince or kpdf ?

---

### Post by John Jason Jordan on 2007-07-28
> **stmiller said:**
> Do you need Adobe Reader for specific documents? Or can you try evince or kpdf ?
Thanks for the response. I should have said at the beginning that I have tried extensively Kpdf, Evince, and all the other open source PDF viewers, and none are acceptable. Kpdf comes closest, but it uses Ghostccript for rendering. Ghostscript is slower than the second coming, and I have occasional problems with incorrect output. Yes, I know I can report the bug, but I am running a business. When I need 100 copies of a document I need them now, not a month from now after the Ghostscript developers have fixed the problem. I can't do without the Adobe PDF print engine. I can print from Adobe Reader using an lp or lpr command, but then I can't access many of the features in my printers that lp and lpr have no syntax for.

I have also posted this query on a local Linux e-list where I have had several responses. Two reported that they have the drop-down box, one running Kubuntu 32-bit and one OpenSuse 32-bit. One other responded that he did not have the drop-down box, and he is running Feisty amd64. Add my two Feisty amd64 computers where I do not have the drop-down box, and a picture is starting to appear. At this point the primary suspect is something missing in the 32-bit libraries for 64-bit Ubuntu. I need more feedback, however. There are other 64-bit distros, so what if the drop-down box appears in them but not in 64-bit Ubuntu? Then we can compare what 32-bit stuff they install that 64-bit Ubuntu does not.

---

### Post by stmiller on 2007-07-29
Have you installed all 32bit libraries?

In synaptic search for ia32 and install all of that stuff.

EDIT: Could be this problem if that adobe reader is just 32bit: [http://ubuntuforums.org/showthread.php?t=348984](http://ubuntuforums.org/showthread.php?t=348984)

And see if this helps: [http://ubuntuforums.org/showthread.php?t=467983](http://ubuntuforums.org/showthread.php?t=467983)

---

### Post by Kilz on 2007-07-29
> **stmiller said:**
> Have you installed all 32bit libraries?

In synaptic search for ia32 and install all of that stuff.

EDIT: Could be this problem if that adobe reader is just 32bit: [http://ubuntuforums.org/showthread.php?t=348984](http://ubuntuforums.org/showthread.php?t=348984)

And see if this helps: [http://ubuntuforums.org/showthread.php?t=467983](http://ubuntuforums.org/showthread.php?t=467983)

This is an issue with all 32bit applications. The printing application is 64bit and the 32bit applications cant use it. But they should be able to print to a file, and then the file can be opened up with a 64bit application and printed out.

---

### Post by John Jason Jordan on 2007-07-29
> **Kilz said:**
> This is an issue with all 32bit applications. The printing application is 64bit and the 32bit applications cant use it. But they should be able to print to a file, and then the file can be opened up with a 64bit application and printed out.
I can print from Adobe Reader 7.0.8 on my Feisty amd64 computers. The issue is that there is no drop-down list of printers that I have insalled via CUPS, so I must use an lp or lpr command. 

If this is a 32-bit issue, how is it that Opera (which is 32-bit) runs just fine and also displays a drop-down list of my installed printers?

---

### Post by Kilz on 2007-07-29
> **John Jason Jordan said:**
> I can print from Adobe Reader 7.0.8 on my Feisty amd64 computers. The issue is that there is no drop-down list of printers that I have insalled via CUPS, so I must use an lp or lpr command. 

If this is a 32-bit issue, how is it that Opera (which is 32-bit) runs just fine and also displays a drop-down list of my installed printers?

Acrobat is 32bit, it cant use the 64bit cups. Why Opera can, I dont know. Why not file a bug report.

---

### Post by John Jason Jordan on 2007-07-29
> **Kilz said:**
> Acrobat is 32bit, it cant use the 64bit cups. Why Opera can, I dont know. Why not file a bug report.
I know the beta for Adobe Reader 8.1 for Linux is closed. I assume that means the release is not too far off. Therefore, a bug report on 7.0.5 - 7.0.9 would probably be pointless. I do have the ear of the person in charge of the beta and I have informed him of the 64-bit issue. I just wish I had more data than "two 32-bit users see the drop-down box and three 64-bit users do not." I wish I had data from users of other distros as well. And I wish Adobe wasn't the most tight-lipped software vendor on the planet. We don't know if they are even going to make a separate 64-bit edition this time, and they won't say.

---

### Post by cacycleworks on 2007-08-27
I'm 64 bit user #3. kubuntu 7.04 
16:53 chris@outside:~$ uname -a
Linux outside 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

Further, Adobe reader seems to have broken konqueror. It opens and simply says "stalled" with a blank background. 

I installed adobe reader b/c none of the other readers would render my proof of insurance... :P should have just sent it to a windows box.

---

### Post by John Jason Jordan on 2007-08-27
> **cacycleworks said:**
> I'm 64 bit user #3. kubuntu 7.04 
16:53 chris@outside:~$ uname -a
Linux outside 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

Further, Adobe reader seems to have broken konqueror. It opens and simply says "stalled" with a blank background. 

I installed adobe reader b/c none of the other readers would render my proof of insurance... :P should have just sent it to a windows box.
I believe Cabaret can do editable PDF forms. I've been told it can even save the edited form:

[http://www.cabaret-solutions.com/de/downloads/handle_download?path=/home/downloads/files/cabaretstage_3.1.1_linux_x86-64.tar.gz](http://www.cabaret-solutions.com/de/downloads/handle_download?path=/home/downloads/files/cabaretstage_3.1.1_linux_x86-64.tar.gz)

It's free for personal use, but not open source. But then, neither is Adobe Reader.

---

### Post by cacycleworks on 2007-08-28
Thanks for the reply, I'll look in to that.  :-)

btw, I removed adobe reader and upon reboot, konqueror worked again. *phew*

---

