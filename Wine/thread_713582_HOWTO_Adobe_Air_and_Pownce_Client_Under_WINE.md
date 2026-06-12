---
title: "HOWTO: Adobe Air and Pownce Client Under WINE"
date: 2008-03-02
forum: Wine
---

### Post by lnknpk04 on 2008-03-02
OK Folks.  Never played with a program and WINE to get it to work before, so I'll try to lay out exactly how I did it.

First off:  As of the time of this post, if you do a fresh install of Adobe Air on a Windows/Mac box and try to install the Pownce client ([www.pownce.com](www.pownce.com)) it doesn't let you.  The folks at pownce haven't updated their app for Air 1.0 since it just came out last week.  The good news is that you can still download the last Air beta before 1.0 and Pownce will install out of that.

What you need:

Pownce .air install file ([www.pownce.com](www.pownce.com))
Windows Beta3 installer for Adobe Air ([http://labs.adobe.com/downloads/air.html](http://labs.adobe.com/downloads/air.html))
WINE (I used 0.9.55)

OK.  Go to your command line, get to the directory of the installer and do "wine air_b3_win_121207.exe" (This is the filename that I downloaded off of the Adobe Labs site)

This will bring up the installer.  Go through the prompts and it will say that it installed fine.

Now, we need to install the Pownce client.  To do this, we have to run the install air application executable located in the Adobe Air folder in your "C Drive"
/home/<User Name>/.wine/drive_c/Program Files/Common Files/Adobe AIR/Versions/<version>

In this directory run the command "wine Adobe\ AIR\ Application\ Installer.exe"

A dialog box will pop up letting you browse to and select the Pownce .air install file.

This will let the program install and run by going into .../Program Files/Pownce and using the command "wine Pownce.exe".  One problem though.  You cant see anything inside of the Pownce window.

To fix this, we need to edit one of the .xml files in the Pownce folder located at 
/home/<user name>/.wine/drive_c/Program Files/Pownce/META-INF/AIR

We need to edit a value in the application.xml file.  Now, before we edit this file, may want to make a backup of it.  Doubt you'll need it, but its a habit of mine.

You will see an entry that says
<transparent>true</transparent>

Change 'true' to 'false' to show
<transparent>false</transparent>

Save the file, and run the Pownce.exe file again.  This time, it should display the contents of the window and you can log in.  Everything should work now.  

At some point, Adobe Air will say that there's a new version available and ask if you wish to download it.  Just say yes and it will update without a hitch.

I haven't tested this with any other Adobe AIR apps but I'm sure with some tweaking they will work as well.

Please let me know if I missed any steps or you run into difficulty.  Cheers :)

---

### Post by lnknpk04 on 2008-03-02
Just Tested the ebay application.  Worked out of the box w/o tweaking

---

### Post by rami on 2008-03-16
Wonderful guide!!

However the fonts are all jagged up! I tried copying the MS fonts into /.wine/drive_c/fonts

---

### Post by anojrs on 2008-03-31
This post can be closed now. as Adobe released AIR for linux ;)
Can check the guide here:
[http://anojrs.blogspot.com/2008/03/adobe-air-for-linux-works-great.html](http://anojrs.blogspot.com/2008/03/adobe-air-for-linux-works-great.html)

---

### Post by PaBLoX_CL on 2008-04-06
Until now... it works perfectly... :)

---

