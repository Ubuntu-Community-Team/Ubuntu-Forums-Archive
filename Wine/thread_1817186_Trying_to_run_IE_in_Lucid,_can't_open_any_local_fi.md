---
title: "Trying to run IE in Lucid, can't open any *local* files"
date: 2011-08-03
forum: Wine
---

### Post by gangasrotagati on 2011-08-03
Hello! I am working making timelines with Simile Timeline. To do this, I need to open an HTML file (located in my Documents folder) with a browser. The problem is, there is a bug that Simile Timeline has with Firefox that prevents you from looking at any timeline with B.C. dates. This bug doesn't exist if you use Internet Explorer- that is the only reason why I am trying to run Internet Explorer!

Anyways, I downloaded PlayOnLinux 3.7.3 in order to run IE 7. I have IE working- I can use it to display web pages, but when I try to load the HTML file by pasting it into IE 7, it shows an error message saying "Windows cannot find 'file:///home/administrator/Documents/TimelineWork/complete.html.' Please check the spelling and try again." If I right click on the HTML file icon and select IE from the popup menu,  I get an error message saying  "There is no windows program configured to open this type of file".

:confused: Thank you so much for any tips, I've been trying to figure this out all day and I'm going nuts! I am running Lucid Lynx 10.04.

P.S. I also tried using Wine (Wine 1.2.2) to do the same thing, but when I try to run IE from Wine I get the following error message:

Archive:  /home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe
[/home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe or
          /home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe.zip, and cannot find /home/administrator/.wine/dosdevices/c:/Program Files/Internet Explorer/iexplore.exe.ZIP, period.

Again, thank you!

---

### Post by bodhi.zazen on 2011-08-03
Move your your html document into your .wine folder =)

---

### Post by sadaruwan12 on 2011-08-03
Let me try this in my Virtual Box and recreate your issue to find a better solution for you please hold on.

---

### Post by gangasrotagati on 2011-08-03
Well, now I have a new problem. I have put my HTML files into my Wine folder, but when I open up IE in Wine, it has no navigation bar- it is just like a special "Wine Only Internet Explorer" that has various links to Wine related things. How can I open files with this thing?

---

### Post by sadaruwan12 on 2011-08-03
Did you tried IE 8 does that gives you the same problem?

---

### Post by gangasrotagati on 2011-08-03
I don't think it's possible to run IE 8 yet on Wine... Is it?

---

### Post by sadaruwan12 on 2011-08-03
> I don't think it's possible to run IE 8 yet on Wine... Is it? 

You're running PlayOnLinux which is a GUI for the actual wine so in terms of POL it's not there and gives the user the feel of that cannot be done but with the actual wine you can but you've to do some work to get it running.

So before that lets get this on up and running for your OK.

---

### Post by Elfy on 2011-08-03
Thread moved to Wine.

---

### Post by gangasrotagati on 2011-08-03
OK, so I finally figured out how to get Wine to open Internet Explorer and have a search bar ([http://www.dangibbs.co.uk/journal/installing-internet-explorer-6-ie6-on-linux-ubuntu](http://www.dangibbs.co.uk/journal/installing-internet-explorer-6-ie6-on-linux-ubuntu)) But it still is doing the same thing it was doing before- it says "Windows cannot find 'file:///home/administrator/.wine/drive_c/Program%20Files/Internet%20Explorer/complete.html'. Please check the spelling..."

@bodhi.zazen, is that what you meant by "Move your your html document into your .wine folder" ? Much thanks for your help!
 				 				[URL="http://ubuntuforums.org/member.php?u=89054"][COLOR=#980101][B]
[/B][/COLOR][/URL]

---

### Post by bodhi.zazen on 2011-08-03
Yes, you need to move it into drive_c, you will see a windows file structure there, you should see My documents and what not.

Then you have to use the proper path, not sure how IE is going to like that.

---

### Post by gangasrotagati on 2011-08-03
You have to click on Open>Browse, then click on the file.

Thanks, my problem has been solved now!

---

