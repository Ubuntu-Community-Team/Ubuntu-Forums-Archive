---
title: "Installing Adobe Digital Editions using WINE"
date: 2008-02-19
forum: Wine
---

### Post by 587rober on 2008-02-19
At present Adobe Digital Editions does not support LINUX with a promissed version due in the future.  

I need to run Adobe Digital Editions (DE) to make use of an academic website (Athens) that uses the DRM elements of DE to loan out articles to the user for a defined period of time.  

Two pre requirements of DE when running on Vista are: Adobe Flash 9.0 and Adobe READER 8.0.   I have got both these running using the linux versions of the software.  

I had hoped to run DE using WINE, but I am figuring that as the application is a Rich Internet Application (RIA) it does not download and install as a normal .exe file.

Any clues or help?  Are their any alternatives?

---

### Post by danstever on 2008-05-29
I have been trying to figure out how to get DE running for awhile as well. I don't have the same requirements as you, but I have a few PDFs that I need DRM authorization for.

I am currently trying to get DE to authorize my PDFs. I have it installed. What I did was look at the shortcut in Windows and find where the .exe was being pulled from. The default location in Windows XP is: C:\Documents and Settings\(USER)\Application Data\Macromedia\Flash Player\www . macromedia.com\bin\digitaleditons1x5\digitaleditions1x5.exe

(NOTE: The spaces in the path above are because the board keeps changing the link name to a hyperlink.)

I copied this .exe and installed it with Wine. It runs great, but I have not been able to read any DRM PDFs. Yet.

Hope this helps.

---

### Post by ianfromrocky on 2008-07-26
I got Adobe Digital Editions to work using WINE as well. I just went to the folder where the program is on my windows partition (as already listed above) and right clicked it in Nautilus and told it to open via WINE. It then went about installing it into WINE. After that I copied the Digital editions folder from my windows to my WINE 'c' drive -- creating the exact folders C:/Documents and Settings/.../www.mac.../...

I then drag-and-dropped my DRM'd book into the running program. It was either here or when installed it that it asked me to authorize my computer with my adobe user name and password (received by registering on the adobe web-site -- otherwise it threatens to tie the ebooks down to your hardware to make sure your not given into the temptation of a pirates life on cyber seas).

It runs just like it does in WinXP now. My theory is that all one needs to do is get a hold of the install file without having to go through the flash install utility on the adobe website. -- I'd tried that with Firefox running in WINE but it would always give me an error message after downloading the installer.

---

### Post by globalenigma on 2008-11-06
I was able to get it to work as well...  If anyone needs the installer just post here and I will see if I can direct you to the right place for download...

---

### Post by CalderCoalson on 2008-11-06
I've been looking for it for 20 minutes and can't trick the download site into thinking I have windows.  That would be great if you could post it.

---

### Post by globalenigma on 2008-11-09
[http://www.2shared.com/file/4253402/a13d5351/digitaleditions1x5.html](http://www.2shared.com/file/4253402/a13d5351/digitaleditions1x5.html)

---

### Post by CalderCoalson on 2008-11-10
Thanks, installing now!

---

### Post by Fuge on 2008-11-18
Thanks for the excellent info above. Just want to add that after getting the EXE from a windows machine and copying it to an arbitrary directory on my machine I installed it using Crossover Office 7.1. It works fine so far. When I purchased some ebooks they download as an "ascm" file. In Windows they automatically launch Adobe DE but in Linux they just land on your Desktop. Dragging them onto the DE icon that Crossover left on the Desktop completed the cycle and DE then downloads them perfectly.

---

### Post by jttucker on 2008-12-31
I'm trying to read e-books on a Thinkpad 600E running XUBUNTU (Intrepid) using Adobe Digital Editions v1.5. I successfully installed ADE using WINE and the method outlined above. But I haven't been able to authenticate, so can't open my e-books. I suspect others were able to do this because they had previously authenticated using MS Windows on the same PC (dual booting). I don't have that option. Anyone know how to authenticate using WINE on a pure XUBUNTU installation?

Thanks in advance. JTT

---

### Post by muriel on 2009-03-13
updated link for version 1.7: [http://www.2shared.com/file/5072448/c47e1f1/digitaleditions.html](http://www.2shared.com/file/5072448/c47e1f1/digitaleditions.html)

---

### Post by J-Rod on 2009-05-12
Anyone with Windows maybe want to help out with an updated link to the new version? I'll send you an e-cookie!

---

### Post by BrooksGarrett on 2009-05-18
[http://www.2shared.com/file/5840283/32573bf1/digitaleditions.html](http://www.2shared.com/file/5840283/32573bf1/digitaleditions.html)

Version 9.0.1085.27 of the installer. Captured from Adobe on 5/18/2009. Hope this helps ;-)

---

### Post by codyhilton on 2009-05-29
Here is the current Digitial Editions .exe file directly on Adobe's website:

[http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe](http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe)

---

### Post by shadowlands on 2009-06-20
more info please?  My book will not open.  > **Fuge said:**
> Thanks for the excellent info above. Just want to add that after getting the EXE from a windows machine and copying it to an arbitrary directory on my machine I installed it using Crossover Office 7.1. It works fine so far. When I purchased some ebooks they download as an "ascm" file. In Windows they automatically launch Adobe DE but in Linux they just land on your Desktop. Dragging them onto the DE icon that Crossover left on the Desktop completed the cycle and DE then downloads them perfectly.

---

### Post by leorochael on 2009-06-22
No need to scavenge your windows folders or count on the kindness of strangers to install Adobe Digital Editions on Wine, just visit [Adobe Digital Publishing Technology Center]("http://www.adobe.com/devnet/digitalpublishing/"), appease the bridge troll with your registration credentials (the same ones you'll use on the D.E. software anyway) and download the installer.

---

### Post by shadowlands on 2009-06-23
Never mine.  I stepped away calmed down and reloaded the program and all is right in the written world again.> **leorochael said:**
> No need to scavenge your windows folders or count on the kindness of strangers to install Adobe Digital Editions on Wine, just visit [Adobe Digital Publishing Technology Center]("http://www.adobe.com/devnet/digitalpublishing/"), appease the bridge troll with your registration credentials (the same ones you'll use on the D.E. software anyway) and download the installer.

---

### Post by mrvanes on 2009-07-20
I successfully installed DE on my Linux box, using WINE, but when I try to open a real .acsm file I get the following error:

MovingPictures.acsm:
IO Error on local file open

Path:
Z:\home\martin\Documents\E-books\MovingPictures.acsm

Event Detail:
Error #2038
--- end ---


Anyone encountered this error? I googled for error #2038 and found this site, but that didn't help much:
[http://www.ebookmall.com/knowledge-collection/adobe-reader-faq.htm#7b](http://www.ebookmall.com/knowledge-collection/adobe-reader-faq.htm#7b)

---

### Post by jasonparekh on 2009-08-03
> **mrvanes said:**
> I successfully installed DE on my Linux box, using WINE, but when I try to open a real .acsm file I get the following error:

MovingPictures.acsm:
IO Error on local file open

Path:
Z:\home\martin\Documents\E-books\MovingPictures.acsm

Event Detail:
Error #2038
--- end ---


Anyone encountered this error? I googled for error #2038 and found this site, but that didn't help much:
[http://www.ebookmall.com/knowledge-collection/adobe-reader-faq.htm#7b](http://www.ebookmall.com/knowledge-collection/adobe-reader-faq.htm#7b)

Hit the same error if I tried to open the file via the menu.  Instead, drag and drop your ACSM file into the Digital Editions window (via Nautilus if nothing else works).

---

### Post by Mander on 2009-09-30
Have any of you had trouble with it printing?  I'm supposed to be able to print one copy of the article I bought, but Adobe just says "this document could not be printed".

---

### Post by misha680 on 2009-11-03
So I am not sure this is "allowed" but it's second on Google and very helpful.

[http://www.pdfunlock.com/ebook](http://www.pdfunlock.com/ebook)

Worked for me for Adobe Digital Editions.
Misha

---

### Post by Abadon125 on 2009-11-19
> **misha680 said:**
> So I am not sure this is "allowed" but it's second on Google and very helpful.

[http://www.pdfunlock.com/ebook](http://www.pdfunlock.com/ebook)

Worked for me for Adobe Digital Editions.
Misha

It says you have to have 32bit and windows.  I am using neither.
EDIT: and it appears as though the service was shut down.  Does anyone have the newest Adobe Digital Editions?  Thanks

---

### Post by commonplace on 2009-11-21
> **jasonparekh said:**
> Hit the same error if I tried to open the file via the menu.  Instead, drag and drop your ACSM file into the Digital Editions window (via Nautilus if nothing else works).

I can't get it to open an ACSM file no matter what I do. I get the error above if I do 'open with' or if I use the open menu item from Digital Editions itself, and when I dragged and dropped, it said "Unknown command line file type".

Any ideas? Digital Editions seems to run fine under WINE but if I can't open an ACSM file... it won't do me any good. :)

/Kevin

---

### Post by shayguitarra on 2009-11-28
I've got ADE working and I can read ebooks I bought on a windows pc.

But here is my question. Does anyone know how I would go about getting it to recognise my Sony Reader so I can transfer ebooks between them?

Thanks.

EDIT: Just after I wrote that I tried to copy and paste the ebook I bought, from my ADE folder straight to my Sony Reader. It's not encrypted, and I can read it perfectly. I have no idea why. When I try to open it in the normal E-book viewer I'm told it's protected by DRM. I'd be interested to hear any theories.

---

### Post by rainbowgoblin on 2009-11-30
Yeah, I have the same problem as Kevin... I can download a urllink.acsm file, but I can't open it with ADE via "add item to library" or drag and drop it into the window ("unknown command line file type")


Also, for anyone who's thinking of just trying an older version of ADE, it won't work... it checks whether there's an updated version, and closes if you refuse to download it.

---

### Post by rainbowgoblin on 2009-12-02
> **shayguitarra said:**
> 

But here is my question. Does anyone know how I would go about getting it to recognise my Sony Reader so I can transfer ebooks between them?


The trick is apparently to use a Windows box ONCE in order to validate your reader with ADE. Here's what worked for me (with Windows... I'll get to what I was finally able to get working with Linux after).

1. Install Sony eBook Library on the Windows system (this is apparently necessary for the drivers).
2. Install ADE and use the same email/password that you will use with your ebooks.
3. ADE will ask you to validate the device. Do it.  It really does ask you, and there's no way to get it to probe for the device explicitly, so try rebooting if it doesn't work. And this works with Windows 7, although both Adobe and Sony seemed to think their software wasn't Win 7-supported.

OK, so on to the Linux struggle... I still can't get ADE to open .acsm files, so I installed QEmu+KVM +WinXP, and got ADE and Sony Library working there, only I'd get the virtualized Blue Screen Of Death if I opened ADE (in KVM) with the reader activated (in KVM, with the -usbdevice flag). Not a problem with Sony Library, just ADE. So instead I run KVM with a samba connection to a Linux folder, validate ebooks with ADE (in KVM), then move them to the Linux folder, then transfer them to my reader with Calbre. Phew!  In point form:

1. Open the .acsm with ADE in a virtual Windows environment.
2. Copy the DRM-ified epub from the "My Digital Editions" folder in virtual Win to a shared Linux folder.
3. Use Calibre in native Linux to transfer the epub to your Reader.

This will only work if you are able to activate your reader with ADE first! Good luck!

---

### Post by commonplace on 2009-12-02
> **rainbowgoblin said:**
> The trick is apparently to use a Windows box ONCE in order to validate your reader with ADE. Here's what worked for me ...

Thanks for the workaround! I might give this a go. Hopefully Adobe makes this easier in the future. :)

/Kevin

---

### Post by nostromo1984 on 2010-05-19
I've successfully installed ADE 1.7.2 with Wine on Ubuntu 10.4. Just D'n'drop the downloaded URLLink.acsm on ADE-Windows.  Works without any Problems.

---

### Post by OLFP on 2010-06-04
1.7.2 works for me on 64bit 9.04 too. 

I'm also able to transfer files to my Astak EZReader. You just have to mount it before starting ADE. ADE detected it and authorised it, no problem. It took a little while and the dialogue box went blank, but it did work.

---

### Post by stevo1977 on 2010-06-28
I just successfully installed and authorized ADE 1.7.2 under WINE, but the drag-and-drop feature doesn't do anything at all.  I have an ACSM file that I got from my local library, and dropping that on ADE does nothing.  Am I doing this wrong?

Cheers,
stevo

P.S. When I start up ADE, it says "Could not find Digital Editions folder."  There is such a folder, and it was created by the installer.  Why do people make programs that don't let you browse for "missing" folders?

---

### Post by asdfoo on 2010-06-28
> **stevo1977 said:**
> I just successfully installed and authorized ADE 1.7.2 under Wine, but the drag-and-drop feature doesn't do anything at all.  I have an ACSM file that I got from my local library, and dropping that on ADE does nothing.  Am I doing this wrong?

Cheers,
stevo

P.S. When I start up ADE, it says "Could not find Digital Editions folder."  There is such a folder, and it was created by the installer.  Why do people make programs that don't let you browse for "missing" folders?

which version of Wine are you using?  wine-1.2-rc5 is the most recent.

to find out, open a terminal and type:
wine --version

---

### Post by stevo1977 on 2010-06-28
Thanks for the reply, asdfoo.  I was using 1.0.1, so I added the WINE repositories and upgraded to 1.2.  I then opened ADE, but had the same problem as before.  It can't find the Digital Editions folder, and won't interact with drag-and-drop.

Cheers,
stevo

---

### Post by stevo1977 on 2010-06-29
Turns out all I needed was to install Adobe Reader.  Very annoying, but at least it works now.

Cheers,
stevo

---

### Post by sunrise-7 on 2010-07-13
After a month of requesting assistance from KoboBooks and elsewhere to get access to an e-book I purchased from them and wanted to run on Ubuntu 10.04, and asked several times for my money back .. I did get the following to work. Adobe Digital Editions is required to Download the ebook, after which it can be read on ADE or another epub reader.

Here you go with my last response to them: :popcorn:
[B][SIZE=+2][COLOR=#006633] Setting up Adobe Digital Editions to run in Ubuntu 10.04 WINE[/COLOR][/SIZE]
2010-07-13 --- this cannot be done without access to a Windows XP or 7  system!
[/B]

[LIST=1]
[*]**[B]You MUST run ADE version 1.7.2 to access and download  any KoboBooks. **[/B]
[*]**[B]An earlier version of ADE WILL download & run  in Ubuntu WINE. **[/B]
[*]**[B]The earlier version will NOT allow access to  KoboBooks after May, 2010? **[/B]
[*]**[B]Version 1.7.2 of ADE has a Significant  modification, incompatible with Linux. **[/B]
[*][B][B]Attempts to download 1.7.2 from Adobe website  with Ubuntu will raise this message:
"Sorry but your system does not meet the minimum system requirements  ..."
and you may be transferred to a problem solving index of pages. [/B][/B] 
[*][B][B]A link below the warning message will access 
[ http://kb2.adobe.com/cps/403/kb403051.html]("http://kb2.adobe.com/cps/403/kb403051.html")
Adobe Digital Editions does not install on Windows or Mac OS
(which is irrelevant for Linux/Ubuntu). [/B][/B] 
[*][B][B]If you download the Setup.exe file to a folder on  Ubuntu and attempt to open it with Ubuntu WINE, you will get a message  that THIS exe file is NOT executable.
WHY, is at this [ Link]("https://wiki.ubuntu.com/Security/ExecutableBit"): [https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit) [/B][/B][INDENT] **[B]Software in Ubuntu needs to be "executable" (sometimes called  "trusted"), both in the sense that the software is a program, and that  it is marked as an "executable file" via file permissions. Normal  software is available for installation via the Software Center; this is  the primary source of software in Ubuntu.   **[/B]**[B]Files downloaded from other locations are not marked as  "executable" since they did not get installed via a trusted software  repository. Because of this, attempting to open downloaded files that  are software will fail. The primary reason for blocking this software is  to help unsuspecting users avoid malware (i.e. malicious software like  trojan horses, worms, and viruses).   **[/B]
**[B]Ubuntu Policy requires that software not marked as  executable not be runnable. One of the most common ways this happens is  by having a package ship a .desktop file for a MimeType which executes  the target file (.EXE, .JAR, etc). This is not allowed unless the target  file is already executable (or installed by a trusted software  repository) **[/B]
[/INDENT]  
[*][B][B]The MEANING of the above is that as of July 13, 2010  -- and from the beginning of June or before, Adobe are satisfied to  release software which is insecure, and KoboBooks management have no  concern for non-Windows users and have made NO effort to provide ANY  technical support or development to support their Customer Service  Agents ( who seem to be challenged to work from their own potentially  limited experience, and, be at the mercy of PROSPECTS and Customers  willing to SPEND huge amounts of time and effort to experiment on their  own, within User Groups ... and, hopefully, SHARE, with NO encouragement  or benefit, with other lost souls through the Kobo ticket system,  and/or back in the User Groups. 

 [/B][/B]**[B]WORK AROUND: **[/B]
[*][B][B]Get access to a Windows XP or System 7  computer connected to thr Internet.
If you don't have a dual boot, triple boot or quadra boot Linux-Windows  system, which I haven't had for 6 months, and you still want this to  work (?!?!), beg or borrow the use of a Windows system from a friend,  enemy, or stranger.  [/B][/B]
[*]**[B] You will require your Username and  password to sign-in to the Adobe site. **[/B]
[*]**[B]Sign-in and download Version 1.7.2 to a selected  (so you can find it) Folder in Windows.  **[/B]
[*]**[B]With permission, install the Setup on the Windows  computer. **[/B]
[*]**[B]Start up the Adobe Digital Editions (ADE)  program. **[/B]
[*]**[B]In a browser, go to your Adobe Account. **[/B]
[*]**[B]Select Library. **[/B]
[*]**[B]Find your PURCHASED ebook. **[/B]
[*]**[B]Select the DOWNLOAD link. **[/B]
[*]**[B]SAVE the .ascm file into a known folder. **[/B]
[*]**[B]Use the Library "Add Selection" link in ADE. **[/B]
[*]**[B]Browse to your .ascm file and select. **[/B]
[*]**[B]ADE will NOW access and download your ebook. **[/B]
[*][B][B]In Win7, it will likely be saved into Win-7  Librairies/My Documents.
---- and NOT into either of Computer/Downloads, Favorites/Downloads,  Library/Downloads, or, Computer/Program Files (X86)/Adobe [/B][/B] 
[*]**[B]COPY all of the files of the installed ADE (now in  Windows/Computer/Program Files (x86)/Adobe, there will be  "digitaleditions.exe", an "uninstall.exe", .. together with your ebook,  now in epub format, into a known folder. **[/B] 
[*]**[B]COPY this "collection" folder to a backup medium that  you can take to your Ubuntu system. **[/B]
[*]**[B]Start your Ubuntu system. **[/B]
[*]**[B]Go to usr/share/applications/Browse C: Drive and  open the folder. **[/B]
[*]**[B]Open the subfolder: "Program Files" **[/B]
[*]**[B]Copy and Paste your collection folder into the  "Program Files" folder. **[/B]
[*]**[B]Navigate into your collection folder and right  click on "digitaleditions.exe". **[/B]
[*]**[B]select MOVE to Desktop, and it WILL be there, as  an icon-shortcut. **[/B]
[*]**[B]"digitaleditions.exe" will no longer be in the  "Program Files" folder. **[/B]
[*]**[B]Open the Desktop icon-link whenever you want to  use ADE. **[/B]
[*]**[B]ADE will now work correctly on Ubuntu 10.04. **[/B]
[*]**[B]You may right click on the icon and have the link  also added to the Launch Panel at the top of the display. **[/B]
[*]**[B]Do NOT make the error of deleting the Desktop  icon, or, the Launch Panel shortcut will NOT work, and you will have to  copy your "collection folder" content back into the Ubuntu WINE Program  Files folder .... **[/B]
[*]**[B]If you don't want the hassle, do NOT buy any  KoboBooks for exclusive use on Ubuntu before Adobe provide a more secure  program file. **[/B]
[*]**[B]You can thank me for SPENDING a severe amount of  time and effort to work through this, including many misdirections, when  I would have been much better off to CANCEL the order, Buy the  hardcover online, and be reading it, in hand, in a WEEK, not the MONTH  it has taken. **[/B]
[/LIST]

---

### Post by buan on 2010-07-19
I just installed Adobe Digital Editions v1.7.1 (and v1.7.2 later) on one of my Ubuntu 10.04 x86_64 boxes to read some rental books from elib.se.

**1. Install Wine**
```
sudo aptitude install wine
```




**2. Download the Adobe Digital Editions stand-alone installer for Windows**

**Adobe Digital Editions downloads are located at:** [https://www.adobe.com/cfusion/entitlement/index.cfm?e=digitaleditions](https://www.adobe.com/cfusion/entitlement/index.cfm?e=digitaleditions)
**Version 1.7.1 direct download link:** [http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe](http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe)
**Version 1.7.2 direct download link:** [http://download.macromedia.com/pub/developer/digitalpublishing/digitaleditions_172.exe](http://download.macromedia.com/pub/developer/digitalpublishing/digitaleditions_172.exe)




**3. Install**
Make the installer file executable, doubleclick to install, and follow the instructions.
An Adobe ID is required to use Adobe Digital Editions.

Done.

---

### Post by sunrise-7 on 2010-07-20
Glad you found success, Buan.

The stumbling point seems to be HOW to MAKE the downloaded Windows exe file executable.

I did follow the direct links you found and did download the much smaller exe file than I had been directed to earlier.

I did select for it to be opened with WINE, only to receive the same error message from UBUNTU that the file is not recognized as executable by Ubuntu.

How do you make the exe file executable by Ubuntu?

---

### Post by TedyBear on 2010-07-23
> **sunrise-7 said:**
> Glad you found success, Buan.


How do you make the exe file executable by Ubuntu?

You right click on the file, under properties -> Permissions you check the box at "execute: Allow executing file as program"

//TedyBear

---

### Post by roellipsch on 2010-07-24
Ok I had trouble with the registration phase, when initialising ADE.

This is how I tackled it (after 2 days ;) ):
1. Installed Wine using the ubuntu software center.
2. I have set the properties of the whole .wine folder (view by CTRL H) in my personal folder read and write.
3. Downloaded setup.exe from the Adobe site. So I did NOT install it through IE6. Started the download in the Programm Folder of .Wine.
4. Make sure your Adobe registration account has not been blocked, by too often trying :D
5. Start-up ADE and follow its instruction.

I am not sure which step 2. or 3. did the trick. However before I kept on having the error message: Can not find de Digital Editions Folder.

Good luck

Roel

---

### Post by david-emm on 2010-07-30
Thanks Roel, I had been trying to get Digital Editions running for about a week. I followed your instructions and made my .wine directory read/write/execute (chmod -R 777 .wine). I ran the Adobe setup.exe (which was in my Downloads directory) and Digital Editions installed into the wine Programs file and the program found the 'My Digital Editions' folder OK.  So it would seem to be a permission issue and making the wine folders read/write/execute to all is a work around until Adobe release a Linux version. Thanks again.

---

### Post by Neo40 on 2010-07-31
I just bought my first ebook from internet. Now, I had to download a xxx.acsm file. I chose to save it, but now what I need to do to get my ebook? I'm very lost. I think I need Adobe Digital Editions? I have installed it but what's next? I have a Kobo as ereader. Anyone can give me a howto? 
Thank you for your help!

---

### Post by terryeden on 2010-08-01
> **Neo40 said:**
> I just bought my first ebook from internet. Now, I had to download a xxx.acsm file. I chose to save it, but now what I need to do to get my ebook? I'm very lost. I think I need Adobe Digital Editions? I have installed it but what's next? I have a Kobo as ereader. Anyone can give me a howto? 
Thank you for your help!

Right click on the .acsm file.
Choose "Open With"
Choose "Other Application"
Select "Wine Windows Program Loader"

That should cause Wine to open Adobe Digital Editions.  After a moment, it will begin to download the file.

HTH

---

### Post by m2calabr on 2010-08-04
> **stevo1977 said:**
> I just successfully installed and authorized ADE 1.7.2 under WINE, but the drag-and-drop feature doesn't do anything at all.  I have an ACSM file that I got from my local library, and dropping that on ADE does nothing.  Am I doing this wrong?

Cheers,
stevo

P.S. When I start up ADE, it says "Could not find Digital Editions folder."  There is such a folder, and it was created by the installer.  Why do people make programs that don't let you browse for "missing" folders?

To install I had to way the default windows version to Win98,
then when I ran it I got the same error.  When I switch the windows version back to WinXP it worked beautifully.

---

### Post by kasun141 on 2010-08-26
its work


thanks...............:popcorn:

---

### Post by zilvia on 2010-09-05
Easiest way for me:

[LIST=1]
[*]Install Wine - I chose Windows 7 as windows version
[*]Install Adobe Reader - download from [http://ardownload.adobe.com/pub/adobe/reader/win/9.x/9.3/ita/AdbeRdr930_it_IT.exe](http://ardownload.adobe.com/pub/adobe/reader/win/9.x/9.3/ita/AdbeRdr930_it_IT.exe)
remember to make the .exe file executable by ticking the box in the Properties->Permissions window
This creates the DIgital Editions folder
[*]Download Digital Editions - any version will do, I downloaded this one [http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe]("http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe")
[*]Copy the executable file in /home/[your home folder]/.wine/dosdevices/c:/Program Files/Adobe/Adobe Digital Editions  - replace 
[*]Make it executable by ticking the box in the Properties->Permissions window
[*]Install the damn thing - it worked no problem
[*]Insert your credentials
[*]Drag and drop the .acsm file
[/LIST]

---

### Post by Moochman on 2010-09-09
Nice walkthrough zilvia! Just a couple of minor additions:

It turns out there is a page with a link to the newest version after all! (which as it turns out is already one point number greater!) Just go to [http://kb2.adobe.com/cps/403/kb403051.html](http://kb2.adobe.com/cps/403/kb403051.html)
and look under the heading "Manually install Adobe Digital Editions for Windows".

Likewise if you go here: [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)
you can select Windows 7 and choose your language and get the newest version of Reader.

The only confusing aspect of your walkthrough is the part about copying the executable to the Adobe Digital Editions folder. In my experience just installing Adobe Reader, followed by installing Digital Editions worked like a charm, no further preparation necessary.

Cheers

---

### Post by lushous on 2010-11-02
:KS Thanks! Couldn't have done it without all of your help! Installing Adobe Reader (Linux, not in WINE) was the magical step for me. Digital Editions wouldn't work before I installed it.

---

### Post by gnerdman on 2010-11-03
I have successfully installed ADE and I have books in the library. But I can't figure out how to transfer them to my Kobo reader. The reader isn't recognized in ADE under wine, so no drag-n-drop. I tried adding the books in the My\ Digital\ Editions folder under the .wine subdir to a Calibre library and then adding them from there, but the Kobo insists they're locked. Does anyone know a cure for this? Or some other method for successfully transferring ADE books to a Kobo? Thanks in advance.

---

### Post by lynxags on 2010-12-14
I am also trying to figure out a way for sony reader.
> **gnerdman said:**
> I have successfully installed ADE and I have books in the library. But I can't figure out how to transfer them to my Kobo reader. The reader isn't recognized in ADE under wine, so no drag-n-drop. I tried adding the books in the My\ Digital\ Editions folder under the .wine subdir to a Calibre library and then adding them from there, but the Kobo insists they're locked. Does anyone know a cure for this? Or some other method for successfully transferring ADE books to a Kobo? Thanks in advance.

---

### Post by Barquero on 2010-12-19
Works great, thanks.

---

### Post by wiggy25 on 2010-12-22
Hi all, only been using Ubuntu 10.10 for the last week so be very patient with me!
Thanks to this forum and particular this thread I have managed to install ADE, the latest version via WINE.

I have the ADE icon on my desktop and it does contain some books that I have bought.
Problem I get now is as soon as I click on **Places** and any of the folders ADE opens up and shows all my books.

I have to select **Places**>**Computer **which shows the Nautilus window I can then select any of the folders no problem.
If I select **Places**>**System** the system icon is shown on the desktop although ADE still opens up.
I can then double click on the system icon for it to open the Nautilus window.

Is anybody else having this problem?
I can only see it being a bug running ADE under WINE but as I'm very new to this OS don't really know.

Cheers

Ian

---

### Post by pmagas on 2011-01-13
> **gnerdman said:**
> I have successfully installed ADE and I have books in the library. But I can't figure out how to transfer them to my Kobo reader. The reader isn't recognized in ADE under wine, so no drag-n-drop. I tried adding the books in the My\ Digital\ Editions folder under the .wine subdir to a Calibre library and then adding them from there, but the Kobo insists they're locked. Does anyone know a cure for this? Or some other method for successfully transferring ADE books to a Kobo? Thanks in advance.

Having the same problem with my Nook. When should ADE try to acknowledge hardware? I don't see any menu items to add devices or even look for other devices or in other places. I've read another post re: the adobe.digital.editions folder -  [http://forums.adobe.com/thread/626420](http://forums.adobe.com/thread/626420) - it doesn't do anything for me. No matter what I try, I can't get ADE to see the Nook. 

Thanks in advance for any help you can offer!

Regards,
Penny

---

### Post by relic70 on 2011-01-18
> **Mander said:**
> Have any of you had trouble with it printing?  I'm supposed to be able to print one copy of the article I bought, but Adobe just says "this document could not be printed".

Same problem here. Can read the ebooks but cannot print. Had the same message that the document could not be printed as you. 

I can print from the notepad application installed as a default application, but not from ADE. There is another separate post with the same problem.

I've not found a solution anywhere on the web. Really would like to be able to print the pages for my project.

Anybody else have the same problem?

---

### Post by Fred_C on 2011-02-23
I've got ADE up and running with wine, but can't seem to get it to find my ereader. I'm using a Nook. 

Is there any way to get past these cursed DRM's on books and use some other library manager, like calibre?

---

### Post by embryonichappyperson on 2011-02-24
I'm having the same problem and I need ADE to find my Kobo...*rolls eyes* Also having issues with DRM.

---

### Post by Robertjm on 2011-03-04
I'm running  one of the latest versions of calibre, which I downloaded through a PPA and it sees the Nook Color as soon as I plug it into the USB port.

However, you need to use ADE to actually read the eBook on your Linux computer.

I'm stuck at the point where I cannot upload the eBook to my Nook Color. When I try it tells me there's no software for that type of file on the device. It looks like I have to authorize the device (Nook Color) but I ADE won't recognize the fact I've plugged the device in. If I can't get past that step, I can't get the book on the device.

 
> **Fred_C said:**
> I've got ADE up and running with wine, but can't seem to get it to find my ereader. I'm using a Nook. 

Is there any way to get past these cursed DRM's on books and use some other library manager, like calibre?

---

### Post by twisted_steel on 2011-03-13
> **Fred_C said:**
> I've got ADE up and running with wine, but can't seem to get it to find my ereader. I'm using a Nook. 

Is there any way to get past these cursed DRM's on books and use some other library manager, like calibre?

I managed to get this working with some steps from this WINE HQ page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951).  Note that I have a regular nook (not color), so I don't know if it is any different for that reader.

These are the (slightly different) steps that worked for me in 10.10.

[LIST=1]
[*]Plug in the nook and it should auto-mount to /media/nook.  [*]Open the Wine Configuration tool (Applications->Wine->Configure Wine) and click on the Drives tab.
[*]Find and click on the drive mapping for /media/nook.  In my case this was the I: drive.
[*]Click the Show Advanced button and from the Type drop-down, select Floppy disk.
[*]Click Apply and leave the Configuration window open. In my case, whenever I clicked OK or closed the window, it would not save the settings.  This could be an issue on my end.
[*]Open Adobe Digital Editions and the nook should appear in the list.
[/LIST]

---

### Post by embryonichappyperson on 2011-03-17
For some reason I CANNOT get ADE to open with WINE.

---

### Post by twisted_steel on 2011-03-17
> **embryonichappyperson said:**
> For some reason I CANNOT get ADE to open with WINE.

What version of WINE do you have?  I am running **1.2.2-1ubuntu1~maverick2** from the Ubuntu WINE PPA: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by embryonichappyperson on 2011-03-18
> **twisted_steel said:**
> What version of WINE do you have?  I am running **1.2.2-1ubuntu1~maverick2** from the Ubuntu WINE PPA: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

I just installed the latest one, 1.3. I put the commands from the Winehq in to the terminal and it did it for me.

Maybe it's my computer.

---

### Post by SisterNotes on 2011-03-24
twisted_steel, thank you for your post. I tried the configuration steps that you described and still, I'm not able to see my nook in ADE.
Does the nook show up immediately when you open ADE?

I'm using the latest version of ADE and it is working in WINE with the exception of not recognizing the nook.

---

### Post by sadastronaut on 2011-03-29
> **twisted_steel said:**
> I managed to get this working with some steps from this WINE HQ page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951).  Note that I have a regular nook (not color), so I don't know if it is any different for that reader.

These are the (slightly different) steps that worked for me in 10.10.

[LIST=1]
[*]Plug in the nook and it should auto-mount to /media/nook.
[*]Open the Wine Configuration tool (Applications->Wine->Configure Wine) and click on the Drives tab.
[*]Find and click on the drive mapping for /media/nook.  In my case this was the I: drive.
[*]Click the Show Advanced button and from the Type drop-down, select Floppy disk.
[*]Click Apply and leave the Configuration window open. In my case, whenever I clicked OK or closed the window, it would not save the settings.  This could be an issue on my end.
[*]Open Adobe Digital Editions and the nook should appear in the list.
[/LIST]

Thanks!  I'll have to try this when I get home.  I will hardly need Windows for anything if this works.

---

### Post by Dan51 on 2011-04-06
How to get Kobo ebooks on to Ubuntu 9.10 and Kobo Ereader 
(this is for DRM protected files)
1.Install Wine 
2.Download setup.exe file from [http://kb2.adobe.com/cps/403/kb403051.html#main_Windows%20solutions](http://kb2.adobe.com/cps/403/kb403051.html#main_Windows%20solutions)
3.Right click on setup.exe file and select “Open With Wine Windows Installer” this will install Adobe DRE 1.7.2   :Note The radio button on the adobe site will tell you your system does not meet the minimum requirements. The above http will get you directly to the file you need.
4.Adobe DRE will open upon installation
5.Register your Computer with the radio button provided in the application. 
6.You can now download or add a previously downloaded, purchased or free Ebooks ,which are DRM protected, from the Kobo Site to your computer. The filename will always be “ URRLink.ascm” for DRM protected files.
7.Drag and drop the file URRLink.ascm from you download directory to the library view in Adobe DRE.
8.At this point you will be able to read the Ebook on your computer.
9.Close Adobe DRE
10.Connect the Kobo Ereader to the usb port on the computer and select the “Manage Library” option on the Kobo Ereader. Wait until the Kobo Ereader  indicates “Connected”
11.Reopen Adobe DRE: Applications; Wine; Browse C:\ Drive; Program Files; Adobe; Adobe Digital Editions : Right click on “digitaleditions.exe” and select “Open With Wine Windows Installer”
12.You will now be prompted to register your new device from the radio button in the application.
13.After the Kobo reader is registered it will appear at the bottom of the library selections on the left side of the window.
14.To add a book from your computer to the Kobo Ereader simply drag and drop the ebook from the library file  to the Kobo icon at the bottom of the list.
15.This should work on other versions of Ubuntu
16.For pdf and epub files I found the easiest way was to use Calibre which can be downloaded from “[http://calibre-ebook.com/”](http://calibre-ebook.com/”)
Good Luck

---

### Post by twisted_steel on 2011-04-11
> **SisterNotes said:**
> twisted_steel, thank you for your post. I tried the configuration steps that you described and still, I'm not able to see my nook in ADE.
Does the nook show up immediately when you open ADE?

I'm using the latest version of ADE and it is working in WINE with the exception of not recognizing the nook.

I just checked out another book and was able to try this again.  The nook showed up when I opened ADE.  I also followed my posted steps when doing it, so I think they are correct (at least in my configuration).  I did a dist-upgrade to 11.04 Natty Beta and it still works.  When I opened the downloaded file, it showed up in the open ADE window and I was able to drag it over to the nook.  I did keep the Wine configuration window open when I opened ADE, so I don't know if that helped.

---

### Post by NewBotanist on 2011-06-08
Hi all,

I have a python script that I'm trying to run in wine with the following result. I've installed the 32 bit windows versions of python and pycrypto. 

~$ wine explorer /desktop=name,1024x768 python.exe "C:\script.pyw"
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library tcl85.dll (which is needed by L"C:\\Python27\\DLLs\\_tkinter.pyd") failed (error c000007b).
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library tk85.dll (which is needed by L"C:\\Python27\\DLLs\\_tkinter.pyd") failed (error c000007b).
Traceback (most recent call last):
  File "C:\script.pyw", line 49, in <module>
    import Tkinter
  File "C:\Python27\lib\lib-tk\Tkinter.py", line 38, in <module>
    import FixTk
  File "C:\Python27\lib\lib-tk\FixTk.py", line 65, in <module>
    import _tkinter
ImportError: DLL load failed: Module not found

I guess I need tcl85.dll and tk85.dll. Anyone have any ideas or know where I can download these safely?

Many thanks!

---

### Post by donnagarnet on 2011-06-11
I've tried several times to install ADE using the instructions Dan51 kindly posted, & each time I get an error message telling me my attempt is blocked & scolding me because  the file is not executable.  I've uninstalled ADE 1.5 (which insisted I update to the new version whenever I tried it), in an attempt to get a "clean install" but nothing works.

---

### Post by JMichaelAnderson on 2011-06-14
ADE is currently working great!  However, it is asking me to upgrade....does anyone have the new upgrade link available as previously posted?--Michael

---

### Post by abjdiat on 2011-07-02
> **JMichaelAnderson said:**
> ADE is currently working great!  However, it is asking me to upgrade....does anyone have the new upgrade link available as previously posted?--Michael

I just downloaded the lastest edtion of ADE and it's working great , even better than the previous versions, i hope there is a way to disable "you must upgrade" feature out of ADE ;)

---

### Post by crikeymaximus on 2011-07-11
> **twisted_steel said:**
> I managed to get this working with some steps from this WINE HQ page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951).  Note that I have a regular nook (not color), so I don't know if it is any different for that reader.

These are the (slightly different) steps that worked for me in 10.10.

[LIST=1]
[*]Plug in the nook and it should auto-mount to /media/nook.
[*]Open the Wine Configuration tool (Applications->Wine->Configure Wine) and click on the Drives tab.
[*]Find and click on the drive mapping for /media/nook.  In my case this was the I: drive.
[*]Click the Show Advanced button and from the Type drop-down, select Floppy disk.
[*]Click Apply and leave the Configuration window open. In my case, whenever I clicked OK or closed the window, it would not save the settings.  This could be an issue on my end.
[*]Open Adobe Digital Editions and the nook should appear in the list.
[/LIST]


Awesome, worked for me using the new Nook Touch.  Had to restart ADE a few times but it recognized it eventually.

---

### Post by pawn0_o on 2011-07-12
um guys you dont need a windows box lulz. just download crossover free trial install adobe digital editions. btw it expires in 30 days oh no! 
well my friends there is a workaround.:D
needed items:updated wine ,crossover, ubuntu box(hehe) ,adobe digital editions version 1.7.2 oh and adobe just(just so you dont jinx yourself.)
step3(ooh shiny)install crossover 30 day free trial and then use that to install digital editions (this is the hard part,if you made it this far congratz:P) heres how to uninstall crossover sudo ~/cxoffice/bin/cxuninstall
step2 delete everything you just did(btw why would i want to do that?) ah my friends thats what i did lulz i became tired of no support so i quit.
step3(became bored and decided to try again now with wine)install adobe digital editions version 1.7.2 with wine make sure its the installer
step4(oh man its alot of steps your really burned out)hehe. just sit down and relax man/woman/goat you now have compatibilty.just get your .ascm files off the internet and it should open automatically. (did for me) 

congratz you have completed a 4 step process give youself a pat on the back you deserve it.

helpfully-
pawn- linux newbie
<(-.0)>

---

### Post by sadastronaut on 2011-07-21
> **twisted_steel said:**
> I managed to get this working with some steps from this WINE HQ page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545&iTestingId=59951).  Note that I have a regular nook (not color), so I don't know if it is any different for that reader.

These are the (slightly different) steps that worked for me in 10.10.

[LIST=1]
[*]Plug in the nook and it should auto-mount to /media/nook.
[*]Open the Wine Configuration tool (Applications->Wine->Configure Wine) and click on the Drives tab.
[*]Find and click on the drive mapping for /media/nook.  In my case this was the I: drive.
[*]Click the Show Advanced button and from the Type drop-down, select Floppy disk.
[*]Click Apply and leave the Configuration window open. In my case, whenever I clicked OK or closed the window, it would not save the settings.  This could be an issue on my end.
[*]Open Adobe Digital Editions and the nook should appear in the list.
[/LIST]


Awesome!  I finally got this to work.  The key thing is step #4, which I forgot.  Thanks so much!

---

### Post by Shinto314 on 2011-07-30
> **twisted_steel said:**
> I just checked out another book and was able to try this again.  The nook showed up when I opened ADE.  I also followed my posted steps when doing it, so I think they are correct (at least in my configuration).  I did a dist-upgrade to 11.04 Natty Beta and it still works.  When I opened the downloaded file, it showed up in the open ADE window and I was able to drag it over to the nook.  I did keep the Wine configuration window open when I opened ADE, so I don't know if that helped.

It does seem that that keeping the Wine configuration window is necessary for this to work.  However, there is a way to make it persist, so that you won't have to make this change in Wine Configuration (and leave the window open) every time.
[LIST=1]
[*]Make sure ADE is closed.
[*]Plug in your Nook, make note of where it mounts (mine is /media/MyNOOKcolor).  Case-sensitive.
[*]Eject/unmount/unplug your Nook
[*]Run 'Configure Wine' ("winecfg" from the command line)
[*]Click on the Drives tab, then click Add. Choose a drive letter (like I: ), and enter the path where your Nook appears when it's mounted (so "/media/MyNOOKcolor" in my example).
[*]Click Show Advanced, then select the type as 'Floppy disk', then Apply and OK.
[*]Plug in your Nook, and open ADE.  You should see the Nook on the list, and be able to drag & drop books, etc.
[/LIST]

So by adding your Nook's mount path and preferences ahead of time, Wine will now save these changes.  I hope this helps.

---

### Post by Weidbrewer on 2011-08-24
Shinto314 - so what you're saying is that, by this method, the Nook will be detected every time?  I was searching for a solution as my wife uses ADE, and I want something fire-and-forget for her so that she doesn't need to worry about a terminal or menu-searching every time.

---

### Post by Weidbrewer on 2011-08-25
Okay, from my experiments, the above instructions *work*, but they are not automatic, meaning that they have to be done every time you want to use your nook in ADE.  Is there any way to make this automatic?

---

### Post by Chicagoan on 2011-09-18
I got as far as downloading Adobe Digital Editions, and it opens and show me an empty bookcase, and tells me I have 45 days until I need to upgrade, blah blah blah.

I checked out a book from my library (Chicago Public) and downloaded it, and tried dragging the  .acsm  files into the ADE window, and nothing happened. Am I doing something wrong?

I'm operating off of ubuntu 10.04, if it matters.

---

### Post by gacb on 2011-10-03
I works well with Wine in Gnome 3 (11.10 Oneiric) but not in previous versions.

I don't have any problems installing and using it so far, but I have all sorts of issues in 11.04. It installs and validates, but that's about it.

---

### Post by Robertjm on 2011-10-03
That's great news! I'm on Lucid right now. Guess I'll be chefking out the upgrade process shortly! One less this to do under Windows!!!

Robert

> **gacb said:**
> I works well with Wine in Gnome 3 (11.10 Oneiric) but not in previous versions.

I don't have any problems installing and using it so far, but I have all sorts of issues in 11.04. It installs and validates, but that's about it.

---

### Post by pchenrrt on 2011-11-03
I'm using 11.10.  System specs. Asus 1005ha BIOS 1601 and Sony Reader Pocket edition (PRS-350).  I was able to install ADE under wine and validate my computer and borrowed 3 books from the library which read and work properly under ADE.

When I plug in my ereader Ubuntu acknowledges it and brings up a window but ADE does not seem to know of its existence.  I followed the above directions for the Nook hopeful that they would work for the Sony Reader a couple of times with minor variations but there has been no change.  Any suggestions?

---

### Post by dan000 on 2012-03-02
I just found a successful, fairly simple way to use Adobe Digital Editions under wine and open acsm files.

First, manually download the setup.exe from [http://kb2.adobe.com/cps/403/kb403051.html](http://kb2.adobe.com/cps/403/kb403051.html)

Install it in wine by opening the command line and typing "wine setup.exe"

Once it's installed, open the Wine explorer by typing "wine explorer.exe" in the command line. Within the file explorer, locate the acsm file you downloaded. If you downloaded it to the Downloads folder within your home folder, you may be able to find the file at Z:\home\[username]\Downloads\[filename].acsm, or perhaps at My Documents\Downloads\[filename].acsm.

Right-click the file, and click "Open." It should open within ADE.

In my wine installation, the windows home folder is under C:\windows\profiles\[username], or in Linux at ~/.wine/drive_c/windows/profiles/[username]. Also ~/.wine/drive_c/windows/profiles/[username]/My Documents is symlinked to ~. So, the epub that is imported to your ADE Library can be found at ~/My Digital Editions. If you know how to strip adobe drm (hint, it's called inept), you can now strip the drm from the epub file in that directory and open the file in a native linux app (for example, FBReader).

---

### Post by chingchong on 2012-08-27
Here's a link for wine:
[http://helpx.adobe.com/digital-editions/kb/cant-install-digital-editions.html#main_Windows_solutions](http://helpx.adobe.com/digital-editions/kb/cant-install-digital-editions.html#main_Windows_solutions)

---

### Post by Doublehelix22 on 2012-11-19
> **chingchong said:**
> Here's a link for wine:
[http://helpx.adobe.com/digital-editions/kb/cant-install-digital-editions.html#main_Windows_solutions](http://helpx.adobe.com/digital-editions/kb/cant-install-digital-editions.html#main_Windows_solutions)

The link pointing to the Installer v1.7 is broken and sends you back to the Adobe front page for DE

Current installer is v2.0 for that site. It installed via WINE but wouldn't open, no error messages were generated 

I edited my software sources in Ubuntu Software Centre and added    *ppa:ubuntu-wine/ppa *under the Other Software tab

Did an update and grabbed the latest WINE copy, when I opened WINETRICKS it gave me the option to install Digital Editions 

Install went fine, Digital Editions opened and seems to work OK, except the search function crashes it every time

For my next trick I'll work out how to open the textbook I just bought :)

---

### Post by Robertjm on 2012-11-19
More power to you!! Just so I understand, the v2 will open and let you read the .acsm files, just not search within their content, right?

Robert

> **Doublehelix22 said:**
> The link pointing to the Installer v1.7 is broken and sends you back to the Adobe front page for DE

Current installer is v2.0 for that site. It installed via WINE but wouldn't open, no error messages were generated 

I edited my software sources in Ubuntu Software Centre and added    *ppa:ubuntu-wine/ppa *under the Other Software tab

Did an update and grabbed the latest WINE copy, when I opened WINETRICKS it gave me the option to install Digital Editions 

Install went fine, Digital Editions opened and seems to work OK, except the search function crashes it every time

For my next trick I'll work out how to open the textbook I just bought :)

---

### Post by MHK99 on 2013-05-23
I got the ADE installed on my desktop. I am unable to open it. What is wrong?

---

### Post by Robertjm on 2013-05-23
No offense, but that's kind of like yelling, "HEY, WHAT COLOR IS THE SKY RIGHT NOW??" But you haven't told us where in the World you are. :D

Are you saying the program doesn't launch at all, or are you saying that you cannot open any .acsm files on your computer?Give

What version of Ubuntu are you using? What version of WINE are you using? What version of ADE are you using? Do you have Flash/Air installed? (I can't remember if either of those are required as I'm doing this from memory and am not on my Ubuntu computer right now).

Are you trying to run it from a desktop icon that the installer created, or from within the WINE console? If the former, try running it from within WINE instead to see if that launches the program.


The last time I tried using ADE, I was able to install the program, HOWEVER, the interface was basically blank without any mouse pointer due to some issues with the way it was running under the Unity desktop. I don't remember the specifics because I eventually got a Windows laptop and install programs that way, or directly through Overdrive, on my Android tablet.

Give us some additional details, and perhaps someone will be able to help you better.

Good luck!!

Robert
--------------------------------------------

> **MHK99 said:**
> I got the ADE installed on my desktop. I am unable to open it. What is wrong?

---

### Post by MHK99 on 2013-06-28
Sorry about that. I now have installed Winetricks and reinstalled the ADE. I am happy to say that it is working and I can read my books.

BTW i am running Ubuntu 13.04 on an Intel core 2 duo triple install with Windows 8 in one HDD and Ubuntu in another and Mint Olivia in a USB HD. 

Thanks for the comment.

---

### Post by texaswriter on 2013-08-13
Talk about a necroposting... Is the original post still relevant? 

It might be more useful to start a new thread if you are asking questions or start a new thread if somebody is interested in a new "howto" for Adobe digital versions.

---

### Post by edwardsah3 on 2014-01-16
> **codyhilton said:**
> Here is the current Digitial Editions .exe file directly on Adobe's website:

[http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe](http://www.adobe.com/support/digitaleditions/ts/documents/kb403051/digitaleditions1x7x1.exe)

Thanks. This worked perfectly using a wine install. What is nicer is that the when I downloaded the book from Dover in linux, ADE came up automatically, and displayed the book.

---

### Post by MountainX on 2014-03-30
I installed version 1.7.2 of Adobe Digitial Editions in Ubuntu 12.04. I registered my computer successfully with Adobe. But I cannot download my purchased ebook (using the .acsm file). I get error #2038. Anyone know of a solution for this error? (I get the same error in both wine and Crossover Linux.) Newer versions of ADE do not work in wine, afaik.

---

### Post by MountainX on 2014-03-30
> **texaswriter said:**
> Talk about a necroposting... Is the original post still relevant? 


Yes, it is relevant because it comes up first in a Google search. I think we should learn from newer sites like StackExchange and keep the relevant stuff together in one thread especially one that has good Google visibility.

---

### Post by dunwich42 on 2014-04-01
Awesome, this is what worked for me!

> **twisted_steel said:**
> 
These are the (slightly different) steps that worked for me in 10.10.

[LIST=1]
[*]Plug in the nook and it should auto-mount to /media/nook.
[*]Open the Wine Configuration tool (Applications->Wine->Configure Wine) and click on the Drives tab.
[*]Find and click on the drive mapping for /media/nook.  In my case this was the I: drive.
[*]Click the Show Advanced button and from the Type drop-down, select Floppy disk.
[*]Click Apply and leave the Configuration window open. In my case, whenever I clicked OK or closed the window, it would not save the settings.  This could be an issue on my end.
[*]Open Adobe Digital Editions and the nook should appear in the list.
[/LIST]


---

