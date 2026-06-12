---
title: "Ubuntu + WINE + Overdrive Media Console"
date: 2008-09-22
forum: Wine
---

### Post by halitech on 2008-09-22
Hello everyone

I've been searching for a way to do this but so far I'm come up blank. I would like to be able to download content from my local library but they use a program called OverDrive Media Console that is only available for Windows users. I have tried installing the program in WINE but it fails to run after installing. It requires WMPlayer (which I have installed through WINE-Doors along with IE6, dcom98 and a few other programs I thought might help)

The only link I can find in the forum is this one:
[http://ubuntuforums.org/showthread.php?t=459857&highlight=overdrive](http://ubuntuforums.org/showthread.php?t=459857&highlight=overdrive)

I have contacted my local library and they are in contact with Over Drive but I'm hoping someone might have an idea to try (other then a VM as I don't have any copies of Windows anymore)

---

### Post by untappedpilot2 on 2008-12-16
I would really enjoy this myself.. I've actually been looking for pirated ebook websites so I can actually enjoy a few ebooks on Linux. My local library provides ebooks for free however I too need this ODM Console. Would it be possible to have WINE add the program?

---

### Post by untappedpilot2 on 2008-12-16
So I started looking all over on the web trying to get this application to install for WINE and I think I have the solution. When I downloaded the ODMediaConsoleSetup.exe file from [http://www.overdrive.com/]("http://www.overdrive.com/") I tried installing it with WINE by launching the file with a right click "Open with Wine - Program Loader" whatever. Anyway the setup would launch but ended with the .msi file that was being downloaded in the not trusted category. Anyway I looked all over to find a way around this and it hit me

```

wget http://www.overdrive.com/file/ODMediaConsoleSetup.msi
wine msiexec /i ODMediaConsoleSetup.msi

```

It's actually installing as I type this so no word on if it works or not. I'll post the results later, but so far the install seems to be going fine. It's even added a few shortcuts to the desktop.

---

### Post by locutus42 on 2008-12-22
just finished a two hour excursion into this and so far, it looks like Overdrive Media Console works.

Here's an overview of the process taken:
[LIST=1]
[*]install wine
[*]attempted to install ODMediaConsoleSetup.msi but it said it failed.
[*]Ran the mediaconsole.exe which was installed and one by one migrated dll's to the wine system32 directory
[LIST]
[*]wmvcore.dll
[*]wmasf.dll
[*]quartz.dll   set native
[*]devenum.dll  set native
[*]jscript.dll  set native
[/LIST]
[*] found that Windows Media Player was required and installed v9 for 98/me/2k as per this webpage:
[http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html)
this includes some of the dll's listed above, installing msxml3.msi and klcodec442f.exe
[*]reran Overdrive Media Console and was able to play the notice audio book packaged with the system.
[/LIST]

The Overdrive Media Console install package was obtained with wget from here:
[http://www.overdrive.com/files/ODMediaConsoleSetup.msi]("http://www.overdrive.com/files/ODMediaConsoleSetup.msi")
and I just followed what was listed to get the WMP installed. NOTE: After WMP was installed, it was automatically started and just opened and closed over and over. I had to click on the 'File' menu when I could see it and exit. Then, using the Wine menu, I started WMP and it seemed to open just fine.

The next step is to see if I can get a book from the local library and get it to play on the computer then see about transferring it to a Sansa MP3 player.

---

### Post by patrickscott on 2009-02-07
Thanks for the detailed information. I will try intalling Wine and then the Overdrive Media Console (Ubuntu 8.10). I presume you are still having no problems downloading and listening to audiobooks using overdrive media console.

---

### Post by halitech on 2009-02-07
I still haven't gotten it to work so I went another route, I started applying pressure to my local politicians and the library to get them to apply pressure to OverDriveMedia. Seems it made a bit of a difference as they at least now have software for Mac so hopefully not too far away for a native linux application.

---

### Post by Westerberg on 2009-03-28
> **locutus42 said:**
> just finished a two hour excursion into this and so far, it looks like Overdrive Media Console works.

Here's an overview of the process taken:
[LIST=1]
[*]install wine
[*]attempted to install ODMediaConsoleSetup.msi but it said it failed.
[*]Ran the mediaconsole.exe which was installed and one by one migrated dll's to the wine system32 directory
[LIST]
[*]wmvcore.dll
[*]wmasf.dll
[*]quartz.dll   set native
[*]devenum.dll  set native
[*]jscript.dll  set native
[/LIST]
[*] found that Windows Media Player was required and installed v9 for 98/me/2k as per this webpage:
[http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html)
this includes some of the dll's listed above, installing msxml3.msi and klcodec442f.exe
[*]reran Overdrive Media Console and was able to play the notice audio book packaged with the system.
[/LIST]

The Overdrive Media Console install package was obtained with wget from here:
[http://www.overdrive.com/files/ODMediaConsoleSetup.msi]("http://www.overdrive.com/files/ODMediaConsoleSetup.msi")
and I just followed what was listed to get the WMP installed. NOTE: After WMP was installed, it was automatically started and just opened and closed over and over. I had to click on the 'File' menu when I could see it and exit. Then, using the Wine menu, I started WMP and it seemed to open just fine.

The next step is to see if I can get a book from the local library and get it to play on the computer then see about transferring it to a Sansa MP3 player.

Did you really get this to work?  Because when I enter 
```
wine msiexec /i ODMediaConsoleSetup.msi
```

I get "fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msi281.tmp""

Also, winehq reports ODMC is [COLOR="Red"][**_not installable_**]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14894&iTestingId=34890")[/COLOR].

---

### Post by tcman on 2009-05-15
> **locutus42 said:**
> just finished a two hour excursion into this and so far, it looks like Overdrive Media Console works.

Here's an overview of the process taken:
[LIST=1]
[*]install wine
[*]attempted to install ODMediaConsoleSetup.msi but it said it failed.
[*]Ran the mediaconsole.exe which was installed and one by one migrated dll's to the wine system32 directory
[LIST]
[*]wmvcore.dll
[*]wmasf.dll
[*]quartz.dll   set native
[*]devenum.dll  set native
[*]jscript.dll  set native
[/LIST]
[*] found that Windows Media Player was required and installed v9 for 98/me/2k as per this webpage:
[http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html)
this includes some of the dll's listed above, installing msxml3.msi and klcodec442f.exe
[*]reran Overdrive Media Console and was able to play the notice audio book packaged with the system.
[/LIST]

The Overdrive Media Console install package was obtained with wget from here:
[http://www.overdrive.com/files/ODMediaConsoleSetup.msi]("http://www.overdrive.com/files/ODMediaConsoleSetup.msi")
and I just followed what was listed to get the WMP installed. NOTE: After WMP was installed, it was automatically started and just opened and closed over and over. I had to click on the 'File' menu when I could see it and exit. Then, using the Wine menu, I started WMP and it seemed to open just fine.

The next step is to see if I can get a book from the local library and get it to play on the computer then see about transferring it to a Sansa MP3 player.

----------------------------------------------------------

Hi locutus42,

what version of Ubuntu and Wine are you using?
I am trying to download the same software and am able to get Media Player 9 dowload and install, but the Overdrive software gets as far as downloading and reading the msi file, and generates a log file, but doesn't seem to install.  I'm using 9.04 Remix and Wine 1.1.12. Any suggestions on getting this to install?  

Thanks

---

### Post by asdfoo on 2009-05-15
> **tcman said:**
> ----------------------------------------------------------

Hi locutus42,

what version of Ubuntu and Wine are you using?
I am trying to download the same software and am able to get Media Player 9 dowload and install, but the Overdrive software gets as far as downloading and reading the msi file, and generates a log file, but doesn't seem to install.  I'm using 9.04 Remix and Wine 1.1.12. Any suggestions on getting this to install?  

Thanks

Just post in one thread at a time, I already replied to you here: [http://ubuntuforums.org/showthread.php?t=1159826](http://ubuntuforums.org/showthread.php?t=1159826)

---

### Post by tcman on 2009-05-16
Will do. Thanks for reply.

---

### Post by ponderworks on 2009-07-02
Hey!  Why don't we try to get as many people as possible to write to:

[info@overdrive.com]("info@overdrive.com")

and ask for a linux version.  Since they've gotten a MAC version out there perhaps they'd be able to quickly offer a Linux version too.

Send them an e-mail today!

Thanks!

---

### Post by rykel on 2009-07-27
> **ponderworks said:**
> Hey!  Why don't we try to get as many people as possible to write to:

[info@overdrive.com]("info@overdrive.com")

and ask for a linux version.  Since they've gotten a MAC version out there perhaps they'd be able to quickly offer a Linux version too.

Send them an e-mail today!

Thanks!


I just did exactly that, and below is a copy of my email to OverDrive.   :)


> Dear Sir/Madam,

Greetings and I hope this email finds you well.

I am from Singapore and I am attempting to use library materials from the Singapore National Library, which require OverDrive Media Console.

Unfortunately, I am using Ubuntu Linux as my operating system and OverDrive is not available for the operating system. I do not have any Windows nor Mac license, so installing the 2 operating systems is out of the question.

Would you please release a Linux version of your software and advise me on what I should do in the meantime?




Best Regards,


Rykel™
[http://rykel.blogspot.com](http://rykel.blogspot.com)
[http://bit.ly/acaiberry](http://bit.ly/acaiberry)
[http://bit.ly/howtoinum](http://bit.ly/howtoinum)



---

### Post by chaos51 on 2009-07-27
I've been asking for a number of months now, usually about once a month and this is the usual response I get:

> Unfortunately, OverDrive Audiobooks are not available for Linux as there
is not presently a Linux version of Windows Media Player that supports
copy-protected Windows Media Audio (WMA) files. OverDrive Audiobooks are
delivered in the WMA format. We hope to make our files available in a
format amenable to you in the future. Thank you for your interest in
OverDrive Audiobooks.

It is my understanding that Microsoft will not (or at least not has not in the past) licensed the Windows DRM/Windows Media Player to a linux desktop.  Note: they have licensed it to embedded systems, mobile devices, and set-top boxes that run linux.  I've also sent requests to Microsoft which might be the proper place to send requests or maybe to a government agency or representative.  I at least am in the United States and my tax dollars pay for the library service but I want to use Linux and even though my local library has Windows based PC's available they don't have Overdrive media console installed.

The funny thing is that all I want to do is to download and transfer the Library audio books to my Portable player, don't really care so much for being able to play it on my linux box but it's irritating that I have to find a Windows box to transfer the files to my player.  So I will continue to send my requests to Overdrive as well.

Thanks to everyone for the support and to ponderworks for starting this thread.

---

### Post by greenwom on 2009-11-22
I just installed it with no problems (as far as it running)

installed wine
installed klight codecs
installed wm-player 9

The problem is the WM-player security upgrade will not run and downloaded files will not open due to the security "not able to verify version"

Any work around this?

---

### Post by xodis on 2010-02-12
I'm stuck at the same point, I've gotten everything working except for the WMP DRM. I've tried with various combinations of WMP 9 & 10 and IE 6 & 7, but no luck so far.

---

### Post by NoBugs! on 2010-04-03
Good news, they made a linux version! Well, at least an android-linux version.
[http://www.overdrive.com/software/omc/](http://www.overdrive.com/software/omc/)
Instructions on running android-os programs in Linux can be found here:
[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)

---

### Post by tck on 2010-10-07
> **NoBugs! said:**
> Good news, they made a linux version! Well, at least an android-linux version.
[http://www.overdrive.com/software/omc/](http://www.overdrive.com/software/omc/)
Instructions on running android-os programs in Linux can be found here:
[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)


tried and failed.. it seems to freeze after trying to download app..

---

### Post by hashky on 2010-12-10
Has anyone been able to get Overdrive to work in Ubuntu?  I have an ereader and I would like to be able to download books from my local library.

---

### Post by SisterNotes on 2011-03-12
Ok, I got an Android emulator set up. I then downloaded the overdrive media console app - it takes a while to load (10 min?).

Now, I've a little android on my desktop and I was able to use my library account to download two books in Overdrive.

But, I can't figure out where the files went. I can open the book files. Overdrive is set up to download them to the "virtual" SD card in the emulator's android. I would just rather not read them in the little Android window.

Any ideas? [OK, I figured this out! See below.]

I set up my emulated android with an SD card. This means that an image file (sdcard.img) is created in the avd folder for my android. I named my android "Softpedia" since I was following the instructions in post #17
So now I resort to the trusty terminal commands...

First, navigate to the folder where your image file is stored
     $ cd ~/.android/avd/Softpedia.avd
Then loop mount the image file to the location of your choice, I chose my Desktop
     $ sudo mount sdcard.img /home/username/Desktop -o loop
Presto! The virtual SD card is mounted and ready to open, now close your terminal session
     $ exit
Resources:
[http://developer.android.com/guide/developing/devices/emulator.html]("http://developer.android.com/guide/developing/devices/emulator.html") [COLOR="Purple"]scroll down to "Working with Emulator disk images"[/COLOR]

[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")[COLOR="Purple"] Lots of good info on mounting/unmounting[/COLOR]

---

### Post by SisterNotes on 2011-03-12
> **tck said:**
> tried and failed.. it seems to freeze after trying to download app..

I tried and got it to work, it just took a long time to load and install the app...I think ~10 min.

---

### Post by rykel on 2011-03-12
Hi, Just to share that even if you get the Android Overdrive Media Console to work in Ubuntu, you might be disappointed to find that many titles available to the desktop version are not available to the mobile Android version.

For example, I would like to borrow and read "Launching A Leadership Revolution - Mastering The Five Levels Of Influence", a book by my personal mentor and friend, from the Singapore Library. However, Android Overdrive informs me that the book is not available for loan on the platform.

Go figure.

:(

---

### Post by pmac95 on 2011-05-04
> **halitech said:**
> Hello everyone

I've been searching for a way to do this but so far I'm come up blank. I would like to be able to download content from my local library but they use a program called OverDrive Media Console that is only available for Windows users. I have tried installing the program in WINE but it fails to run after installing. It requires WMPlayer (which I have installed through WINE-Doors along with IE6, dcom98 and a few other programs I thought might help)

The only link I can find in the forum is this one:
[http://ubuntuforums.org/showthread.php?t=459857&highlight=overdrive](http://ubuntuforums.org/showthread.php?t=459857&highlight=overdrive)

I have contacted my local library and they are in contact with Over Drive but I'm hoping someone might have an idea to try (other then a VM as I don't have any copies of Windows anymore)
try this link it worked for me : [http://libertysys.com.au/node/86](http://libertysys.com.au/node/86)

---

### Post by Geremia on 2011-06-23
It can easily be done with [FONT=Comic Sans MS]winetricks[FONT=Arial]:[/FONT][/FONT]
```
winetricks wmp10
```
Then install the Windows version of the OverDrive Media player from here: [http://www.overdrive.com/software/omc/](http://www.overdrive.com/software/omc/)

That's it! Right-click on your launcher bar and add a launcher that runs the command:```
wine "~/.wine/drive_c/Program Files/OverDrive Media Console/MediaConsole.exe"
```

Then you can open your ODM files, have OverDrive Media console download them, and get the resultant MP3 files *without DRM* in "~/My Media/MP3 Audiobooks/"!

---

### Post by pawn0_o on 2011-07-13
hello i cant get it to work it seems that it doesnt want to install overdrive media with wine. any ideas?

---

### Post by GhostCard on 2011-07-25
I was able to install both WMP 10 and the Overdrive Console and both run. The problem i now have is that security update to WMP in outdated and Overdive will not update it from the tools menu. After a few tries the WMP10 open but tells me I am not connected to the internet so the update fails. I have not found a way to fix the WMP problem


Ubuntu 11.04
Wine 1.2

---

### Post by hawthorne62 on 2011-08-02
I am trying to get Overdrive to work for me.  I've tried downloading the Android version, per post 16, but nothing happens when I attempt to download Android from softpedia.  I've tried installing Git, and it's not happening.  

When I go to download the Android version directly from Overdrive.com, the tools folder that the softpedia instructions indicate isn't there.

I've also tried looking for winetricks per post 23, but I can't find it.

Any ideas?  I'm not the most code-literate, so please be clear.

Thanks.

---

### Post by kdmw on 2012-01-31
Hi,

I've got wmp 9 more or less running with wine, but when I try to install the overdrive software, I get this:
> kate@kate-laptop:~$ wine msiexec /i ODMediaConsoleSetup.msifixme:msi:MsiGetMode unimplemented run mode: 4
err:msi:ITERATE_Actions Execution halted, action L"VSDCA_VsdLaunchConditions" returned 1603
It also produced a log:
> TASK    CoInitializeEx - COM initialization Apartment Threaded 
TASK    Enumerating table using SQL statement: SELECT * FROM `_VsdLaunchCondition` 
TASK    MsiGetActiveDatabase 
TASK    MsiDatabaseOpenViewW - Prepare Database to view table 
TASK    MsiViewExecute - Open Database view on table 
Checking a launch condition 
TASK    Getting the condition to evaluate 
TASK    MsiRecordGetStringW - Fetching value 
TASK    MsiRecordGetStringW - Getting value from column 1 
TASK    Evaluating condition 'VersionNT>=600 OR WMP9_EXISTS <> ""' 
RESULT    Condition is false 
TASK    MsiRecordGetStringW - Fetching value 
TASK    MsiRecordGetStringW - Getting value from column 2 
TASK    MsiSetPropertyW - Setting Property Value 
TASK    MsiSetPropertyW - Setting property HideFatalErrorForm to TRUE 
RESULT    Custom Action Succeeded.    uiRet = 1603
I'd greatly appreciate any help.

---

### Post by tessem11 on 2012-08-03
You could always install windows media player ten and then install the msi file by right clicking on it and choosing run with wine program loader and run the mediaconsole.exe when installed. It should work, It worked for me.

---

