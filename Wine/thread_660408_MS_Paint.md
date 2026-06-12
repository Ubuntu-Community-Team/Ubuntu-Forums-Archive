---
title: "MS Paint"
date: 2008-01-06
forum: Wine
---

### Post by Zarathu on 2008-01-06
I desperately need MS Paint on my PC (not any alternatives; it HAS to be MS Paint).  Once this is done, my life will be complete.

```
zarathu@w00w00:~$ wine '/home/zarathu/Desktop/mspaint.exe' 
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\zarathu\\Desktop\\mspaint.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\zarathu\\Desktop\\mspaint.exe" failed, status c0000135
zarathu@w00w00:~$
```

How can I get Wine to quit QQ'ing over this and start the damn program?

---

### Post by DirtDawg on 2008-01-06
Well, you can find the .dll from the first error here: [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42u](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42u)
If I remember right, you can put it in the Windows folder of your Wine install or the folder you're trying to run Paint in. I can't remember if that's exactly right, though.

Still, that might fix your first problem, maybe even your second. Or maybe neither one.

Your insistance on MSPaint is a little surprising. I know from another thread you wrote that you have tried many different alternatives, but I will suggest one more: [MtPaint]("http://mtpaint.sourceforge.net/"). It's quit nice (if that kind of thing is your idea of nice ;) )

Also, if you are doing pixel art, you might consider checking out [this turorial]("http://www.eglug.org/gimpixel"). It is a handy guide to setting up GIMP for working with pixel art. I can vouch for its effectiveness(see: my avatar), escpecially if you have a Wacom-type tablet.

I hope this helps one way or another.

---

### Post by SunnyRabbiera on 2008-01-06
you can do better then MS paint yah know...

its far from a professional image app

---

### Post by DirtDawg on 2008-01-06
> **SunnyRabbiera said:**
> you can do better then MS paint yah know...

its far from a professional image app

But for pixel art, it's considered *the* app by some (by "some" I mean "not me").

Also, concerning the OP, have you tried using "winecfg" to switch between Windows XP, Windows 2000, or even NT? Sometimes that works.

---

### Post by Zarathu on 2008-01-06
No, I'm not doing pixel art, and I don't need anything more professional than Photoshop, which is what I currently use when I need image editing that doesn't suck.  I do need paint, though.

DirtDawg, thank you for the link...I should have gotten it on my own and tried it before posting the thread, really.  RTFM, Nick.

Anyway, I had to put it in my \WINDOWS\system folder.  :]

---

### Post by DirtDawg on 2008-01-06
Glad I could help.

---

### Post by silfiriel on 2008-07-10
So did you get ms paint to work on Ubuntu?
I really need it too, because there are no alternatives for it. 
I specifically need the ability to compress JPEGs size. 
(Ex. a digital photo of about 3MB, just by Save as...>Replace is downsized from 0.5 to 1MB depending on the photo content, and for webmasters this is great).
So far none of the Linux alternatives (mtpaint, gnupaint, kolourpaint)can't do this. And it's the only reason I still dual boot.

Help please...

---

### Post by DirtDawg on 2008-07-10
> **silfiriel said:**
> So did you get ms paint to work on Ubuntu?
I really need it too, because there are no alternatives for it. 
I specifically need the ability to compress JPEGs size. 
(Ex. a digital photo of about 3MB, just by Save as...>Replace is downsized from 0.5 to 1MB depending on the photo content, and for webmasters this is great).
So far none of the Linux alternatives (mtpaint, gnupaint, kolourpaint)can't do this. And it's the only reason I still dual boot.

Help please...

If you're doing web work (with 3MB jpgs?!), use The Gimp that comes with Ubuntu by default in Applications>Graphics>Gimp. 

The simplest method of reducing file size is to open the .jpg in question, then File>SaveAs..., and adjust the "quality" slider. You want to find a balance between quality and size. 85% or so usually gets pretty good results.

The Gimp is a very powerful tool for web graphics that can also be as simple as you would like. There are several other ways to reduce file sizes than simply reducing the quality. If you feel inclined, try looking for Gimp web graphics tutorials with your favorite search engine. I bet you find plenty to read.

---

### Post by johncliff on 2008-07-10
Microsoft Paint is an inexpensive painting program that can be used to teach students the basics of painting software.MS Paint also includes a great Help system that will have you mastering your virtual brush-strokes in minutes.

johncliff
[Credit Card Debt](http://www.stop-credit-card-debt.com)

---

### Post by FlyingIsFun1217 on 2008-07-10
> **johncliff said:**
> Microsoft Paint is an inexpensive painting program that can be used to teach students the basics of painting software.MS Paint also includes a great Help system that will have you mastering your virtual brush-strokes in minutes.

johncliff
[Credit Card Debt](http://www.stop-credit-card-debt.com)

Is... this spam, or...

WOW!, I'm confused... :/

FlyingIsFun1217

---

### Post by SBFC on 2008-07-11
> **FlyingIsFun1217 said:**
> Is... this spam, or...

WOW!, I'm confused... :/

FlyingIsFun1217

Heh, I'm wondering that as well. Sarcasm, I hope?

---

### Post by silfiriel on 2008-07-11
I know Gimp can reduce the size of JPEG with the quality slider, but a JPEG re-saved with Paint that's been downsized from 3MB to 500KB looks pretty much the same, the quality loss is unnoticeable with bare eye. But when Gimp does this the JPEG looks horrible...
Any way I found a solution, XnView under Wine (not the native linux version, does what Paint does, in the same way...)

---

### Post by shad0w_walker on 2008-07-11
With there being only two posts for the user, I'm gonna say spam/troll.

---

### Post by DeVonne on 2008-07-25
I got it to work when putting that one .dll into system32 but mspaint will only open .bmp files, which I will be trying to get working with others

---

### Post by weblordpepe on 2008-07-26
mspaint should be easy to get going in wine I would have thought. Although really as far as windows apps that are simple - mspaint is awful. It's got awful image quality & supports 0.01% of filetypes.

It has almost no options for saving filetypes and if you rely on mspaint to save images destined for the web, well its your bandwidth..

I would suggest looking through the ubuntu repositories for some command-line image converstion tools. Should be easy enough to create a icon on the desktop which you can drag/drop & convert files.

I would be happy to help if you would like to do that.
Edit: Check the Netpbm package.

---

### Post by drozel on 2008-09-29
I only use MS Paint for two features that are not well documented. If these features exist in GIMP/KolourPaint/gPaint/MtPaint, then they are not well documented either.

1) The ability to resize the brush to any size.
2) The ability to replace only one color with another color without harming the other colors.

---

### Post by meho_r on 2008-09-29
C'mon guys, are you kidding? Is this a joke? :confused:

---

### Post by wjaguar on 2008-09-30
> **drozel said:**
> If these features exist in GIMP/KolourPaint/gPaint/MtPaint, then they are not well documented either.
1) The ability to resize the brush to any size.
2) The ability to replace only one color with another color without harming the other colors.

No amount of documenting can help if users refuse to read docs. :-(
[http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC21](http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC21)
[http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC34](http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC34)
[http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC54](http://mtpaint.sourceforge.net/handbook/en_GB/chap_03.html#SEC54)

---

### Post by drozel on 2008-10-02
Well, thanks, I could not find documentation online and it failed to install. Now to see if y'all have a forum so I don't drag this topic off topic too much.

---

### Post by LennyX on 2008-10-26
The thing I like about Paint is canvas resizing by dragging a corner. It's easy and intuitive for everyone. Every alternative I've seen has a dialog box where you enter the dimensions in pixels/inches of how big you want the canvas to be.

I find it hard to believe that MS are the only ones who have figured out how to make a program do that. I'm going to devote my next holidays to making a real alternative to Paint dammit.

---

### Post by pyrofool on 2008-11-11
you can download mspaint from Microsoft at [http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe](http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe)

rune wine paintnt.exe , it will extract the needed files then just put them in a folder and run wine MSPAINT.exe and there you go. I just did this tonight and it works perfectly

---

### Post by asdfoo on 2008-11-11
fyi, Katayama Hirofumi MZ is working on getting a free software clone of mspaint into Wine, so hopefully sometime soon there will be a version automatically included with Wine.

---

### Post by katayama_hirofumi_mz on 2009-03-23
mspaint Clone
[http://www.geocities.jp/katayama_hirofumi_mz/mspaint/eindex.htm](http://www.geocities.jp/katayama_hirofumi_mz/mspaint/eindex.htm)

---

### Post by spancer_87 on 2009-05-14
I felt the same way, because the simplicity of ms paint makes image editing so easy. I bought an Asus eee900, and with the Xandros distro there came a very similar painting program with it. It's called Kolourpaint (Kpaint) and it's possible to install it through Synaptics in Ubuntu=) Just do a search through the packages and there it is;)

---

### Post by HavocXphere on 2009-05-14
Get filemon from sysinternals. Use that to scope out what DLLs its using on a Win PC..copy those dlls over. You can also use a disassembler I suppose.

Btw...the MFC in that error you're getting stands for Microsoft Foundation Class. So grabbing the C++ runtimes off the MS page will prob solve your problem.

---

### Post by DAHstra on 2009-05-30
Cool topic.  I like MS Paint for Vista even more than XPs because of the zoom out / cut paste feature and hot keys.  It seems silly, but it's a handy, fast loading program that I use a lot.

However, I can't get the Vista MSPAINT to run on Ubuntu 9x.  I did get the package listed earlier, which is great.  Ubuntu runs the XP Paint fine.

Can anyone help me find out how to get Vista Paint to run?  It tells me:

"Failed to create empty document"

I have the following support files in its directory:

MSVCRT.DLL
OLEPRO32.DLL
mspaint.exe
MFC42U.DLL
MFC42.DLL
mspaint.exe.mui

:D

---

### Post by weblordpepe on 2009-05-31
> **DAHstra said:**
> Cool topic.  I like MS Paint for Vista even more than XPs because of the zoom out / cut paste feature and hot keys.  It seems silly, but it's a handy, fast loading program that I use a lot.

However, I can't get the Vista MSPAINT to run on Ubuntu 9x.  I did get the package listed earlier, which is great.  Ubuntu runs the XP Paint fine.

Can anyone help me find out how to get Vista Paint to run?  It tells me:

"Failed to create empty document"

I have the following support files in its directory:

MSVCRT.DLL
OLEPRO32.DLL
mspaint.exe
MFC42U.DLL
MFC42.DLL
mspaint.exe.mui

:D
Quite off-topic I know and the mods will hate me for this-
But I disagree with your signature :)
Logic is universal, not personal. Logic is the benchmark by which absolute and relative are gaged.

---

### Post by DAHstra on 2009-05-31
LOL  I came up with that years ago when I was frustrated with drunks.  If you're trying to reason with a drunk, you can't.  They have their own distorted view of reality.

But I also disagree because who's to say your logic is absolute?  Are you SURE?  :p

---

### Post by ad_267 on 2009-05-31
I know you said it MUST be MS Paint, but seriously, you can't get much closer to it than [KolourPaint]("http://en.wikipedia.org/wiki/Kolourpaint").

Edit: Never mind, didn't see it had been mentioned already.

---

### Post by DAHstra on 2009-05-31
Thanks, I'll try KolourPaint too.  I had to research how to get it so that my OS would not yell at me "USE CHANNEL!"   LOL

Anyway, I installed KolourPaint.  It's not bad.  It seems to have the features I was looking for.  However, I'd still like to know how to get MSPaint Vista running.  :)  But I'll give KolourPaint a go too.

---

### Post by DAHstra on 2009-07-05
Okay, so, I'm also running Windows 7 Release Candidate.  The new paint it has is snazzy, but lacks simple features Vista and NT Paint had.  So, I'm pretty sure I know the answer to this, but I have to ask.  Will there be a Windows version of Kolour Paint?  :)  (no egg throwing please)

---

### Post by ad_267 on 2009-07-05
A lot of KDE4 is being ported to Windows, so quite possibly, but not just yet as far as I know.

---

### Post by Lantizia on 2009-07-15
```
Install Paint 5.0
-----------------
sudo apt-get install wine icoutils unzip -y
wget http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe
unzip paintnt.exe -d ~/.wine/drive_c/windows/system32/
rm paintnt.exe
wrestool -x -t14 -n2 ~/.wine/drive_c/windows/system32/MSPAINT.EXE > ~/.wine/drive_c/windows/system32/mspaint.ico
echo -e '[Desktop Entry]\nType=Application\nName=Paint\nExec=wine "C:\\\\windows\\\\system32\\\\MSPAINT.EXE"\nComment=Creates and edits drawings\nIcon='$HOME'/.wine/drive_c/windows/system32/mspaint.ico\nCategories=Utility' > ~/.local/share/applications/mspaint.desktop
```

---

### Post by lkraemer on 2010-03-03
Followed HavocXphere's instructions for using filemon from sysinternals to scope out what DLL's
needed to be added in C:/Windows/System32 to allow MSPaint to run.

**Instructions for getting Windows XP - MS Paint on Linux**
MS Paint on Ubuntu
MSPaint Version 5.1 (Build 2600.xpsp Service Pack 3)

1. Copy the following files from a Windows XP (SP3) Install to a USB Flash Drive.
   The files you need to copy are located at C:\Windows\System32\  (Files needed are...)
   mfc42.dll
   mfc42u.dll
   msisip.dll
   msvcrt.dll
   mspaint.exe
   olepro32.dll
   wshext.dll

2. SEARCH your Hard Drive for GdiPlus.dll.  (Mine was Version 6.0.3264.00 from Allen Bradley = Rockwell)
   but I also found several, and 5.1.3102.5512 was one of the choices if you can't locate 6.0.3264.0
   Copy this file to the USB Flash Drive. (Adds TIF, GIF, JPG, PNG Format Support) 

3. Copy the following Folders from a Windows XP (SP3) Install to a USB Flash Drive
   C:\Windows\AppPatch
   C:\Windows\Fonts

4. Create a Folder named MSPaint at .wine/drive_c/Program Files/
   (Substitute a ? for the SPACE in Program?Files for copying.)
   drwxr-xr-x 2 larry larry 4096 Jun 18 12:42 MSPaint

5. Copy mspaint.exe to .wine/drive_c/windows/Program Files/MSPaint
   Change the permissions of MSPaint to -rwxr--r-- 1 larry larry 343040 Apr 13  2008 mspaint.exe

6. Copy the remaining seven files to ~/.wine/drive_c/windows/system32/
   Copy the Folder AppPatch to .wine/drive_c/windows/
   Copy the Folder Fonts to .wine/drive_c/windows/

6. CREATE AN UBUNTU DESKTOP ICON:
   Right Click on the Desktop, Left Click on Create Launcher.

Name		XP-MSPaint
Description	
Command		wine "/home/youruserlogin/.wine/drive_c/Program Files/MSPaint/mspaint.exe"
Comment		Microsoft XP Paint Ver 5.1

Change ICON as needed from PNG files below, or use the Wine Icon - Wine.svg.
I used Icon Entry7.png.  I copied this png to /usr/share/icons/hicolor/48x48/apps/
with permissions of:
-rw-r--r--  1 root root  674 Jun 18 12:56 Icon Entry_1.png
-rw-r--r--  1 root root 2015 Jun 18 12:56 Icon Entry_4.png
-rw-r--r--  1 root root 3766 Jun 18 12:56 Icon Entry_7.png

7. Double click on XP-MSPaint to test Paint ver 5.1
   Be sure to Click on TEXT in the Left Menu, then draw a Box for the TEXT INPUT,
   then go to the top menu and select VIEW TEXT BOX to allow for changing the
   Font selection and size.

8. When a printer has been installed......To change Print from Portrait to Landscape,
   go to Printer settings and change it there versus the opening Print Setup screen selection.  

Things that do not work properly are:
1. Printing - When opening a LARGE BMP File, and trying to Preview, or print to paper.

Tested with Wine 1.01 and Ubuntu 9.10  03-03-2010
Tested with Wine 1.1.42 & Ubuntu 10.04 LTS  05-19-2010

Tested with Debian 6.0 & Wine-1.1.42

lk

---

### Post by weblordpepe on 2010-03-04
> **lkraemer said:**
> Followed HavocXphere's instructions for using filemon from sysinternals to scope out what DLL's
needed to be added in C:/Windows/System32 to allow MSPaint to run.

**Instructions for getting Windows XP - MS Paint on Linux**
MS Paint on Ubuntu
MSPaint Version 5.1 (Build 2600.xpsp Service Pack 3)

1. Copy the following files from a Windows XP (SP3) Install to a USB Flash Drive
   C:\Windows\System32\  (Files needed are...)
   mfc42.dll
   mfc42u.dll
   msisip.dll
   msvcrt.dll
   mspaint.exe
   olepro32.dll
   wshext.dll

2. Copy the following Folders from a Windows XP (SP3) Install to a USB Flash Drive
   C:\Windows\AppPatch
   C:\Windows\Fonts

3. Create a Folder named MSPaint at .wine/drive_c/Program Files
   (Substitute a ? for the SPACE in Program?Files for copying.)

4. Copy mspaint.exe to .wine/drive_c/windows/Program Files/MSPaint
   Copy the remaining six files to .wine/drive_c/windows/system32
   Copy the Folder AppPatch to .wine/drive_c/windows
   Copy the Folder Fonts to .wine/drive_c/windows


5. CREATE A UBUNTU DESKTOP ICON:
   Right Click on the Desktop, Left Click on Create Launcher.

Name		XP-MSPaint
Description	
Command		wine "/home/youruserlogin/.wine/drive_c/Program Files/MSPaint/mspaint.exe"
Comment		Microsoft XP Paint Ver 5.1

6. Double click on XP-MSPaint to test Paint ver 5.1
   Be sure to Click on TEXT in the Left Menu, then draw a Box for the TEXT INPUT,
   then go to the top menu and select VIEW TEXT BOX to allow for changing the
   Font selection and size.

7. When a printer has been installed......To change Print from Portrait to Landscape,
   go to Printer settings and change it there versus the opening Print Setup screen selection.  

Things that do not work properly are:
1. Printing - When opening a LARGE BMP File, and trying to Preview, or print to paper.

Tested with Wine 1.01 and Ubuntu 9.10  03-03-2010

lk

sweeeeeeeeeet

---

### Post by Bwathke on 2010-03-05
Why does everyone "need" MS Paint so badly? GIMP does what MS Paint does x10 better =/ Its less professional then Photoshop but it still is better then MS Paint and it comes with Ubuntu.

Applications >>> Graphics >>> GIMP Image Editor

---

### Post by lkraemer on 2010-03-06
Bwathke,
It's a simple answer for me.  I had some plans scanned at 600DPI and
the size in pixels was 21600 x 36000 (21.4M) 1BB.  Several of the
files were burnt to CDR and named Temp000398 thru Temp000404.  I tried
GIMP and I couldn't view or open the files.  Image Viewer, or any other
Application I have tried didn't work either.  I needed to find out what
information was contained in each file.  I finally tried MS Paint 5.1
and it worked great.  Next step was to get MS Paint running in Wine 1.0.1.

I'd much rather use GIMP, or some other Linux Application, but so
far I haven't found a way to do that yet.  Do you have any Ideas or
helpful Suggestions I could try?

I have successfully used other Windows Software running in VirtualBox to clean
up the scans and print to paper. 

Maybe I need to submit a BUG Report for Gimp not being able to open that
LARGE of a TIF file!

Thanks.

lk

---

### Post by TNAFan on 2010-05-31
> **Bwathke said:**
> Why does everyone "need" MS Paint so badly? GIMP does what MS Paint does x10 better =/ Its less professional then Photoshop but it still is better then MS Paint and it comes with Ubuntu.

Applications >>> Graphics >>> GIMP Image Editor

Very simple.  I want an easy to use select tool.

---

### Post by peterson_espacoporto on 2010-07-17
@TNAFan

Kolourpaint?

---

### Post by Jcj91 on 2010-08-26
> Why does everyone "need" MS Paint so badly? GIMP does what MS Paint does  x10 better =/ Its less professional then Photoshop but it still is  better then MS Paint and it comes with Ubuntu.

Applications >>> Graphics >>> GIMP Image EditorI can very much identify with people who would like their old trusty apps working in Linux. I am sure Gimp is capable of doing everything that MS Paint does but to me, as I have been using MS Paint since the days it was still called 'Paintbrush' in Windows 3.0, its interface feels almost instinctive and that's why I for one would very much like it to work in Ubuntu. So yes, you're probably right when you say that I and perhaps others are closed minded when it comes to learning how to use alternative applications, admittedly.
The thing that annoys me when I read forums where people (mostly) suggest alternative applications as the solution to getting a certain programme working is the fact that they are not addressing the actual question. Often the question of *how to get a certain / specific application to work* is misinterpreted by many as *how to achieve what this program normally does [in Ubuntu]*. In all except the rarest cases the person asking actually MEANT what he asked, unless you have a good reason to assume otherwise. 
Therefore, in discussions as these, please refrain from (only) suggesting alternative apps and especially from demanding the subject to justify his/her motive to use the app as this will only cause irritation and doesn't actually solve anything. Alternative software is only a real 'solution' when all else fails and there is absolutely no way to get the app working.

I have also attempted to install MS Paint in Ubuntu 10.04, but to no avail. I have a VirtualBox VM with Windows 7 on it, so theoretically I could just run Paint in there, but I hate having to use the shared folder all the time and the clipboard from the host machine to the guest machine (even though I've installed Guest Additions in the guest machine) doesn't transfer image data.

When I installed mspaint.exe first, I got the same error message:

```
joshuajones@joshuajones-desktop:~/.wine/dosdevices/c:/windows/system32$ wine mspaint.exe
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\windows\\system32\\mspaint.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\mspaint.exe" failed, status c0000135
```The solution seemed simple; just get a copy of MFC42u.dll in Wine's *system32* folder. That's what I did. Then I got a whole string of errors:

```
joshuajones@joshuajones-desktop:~/.wine/dosdevices/c:/windows/system32$ wine mspaint.exe
err:module:import_dll Library KERNELBASE.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Debug-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ErrorHandling-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-File-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Handle-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Interlocked-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LibraryLoader-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Localization-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LocalRegistry-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Memory-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Misc-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessEnvironment-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessThreads-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Profile-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-String-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Synch-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Core-SysInfo-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library API-MS-Win-Security-Base-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42u.DLL") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\windows\\system32\\mspaint.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\mspaint.exe" failed, status c0000135
```These are all just references to DLLs missing. Since my VM has Win 7 on it I just located each of these DLLs in the VM and copied them into the Wine System 32 directory. When I did that and I tried to run MS Paint again, I got this:

```
joshuajones@joshuajones-desktop:~/.wine/dosdevices/c:/windows/system32$ wine mspaint.exe
fixme:ntdll:NtQuerySystemInformation (0x00000032,0x32fad4,0x00000004,(nil)) stub
wine: Call from 0x7bc3e3b0 to unimplemented function ntdll.dll.RtlCreateTagHeap, aborting
err:module:attach_process_dlls "KERNELBASE.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\mspaint.exe" failed, status 80000100
```I'm at a dead end here ... is there anyone who can tell me where I went wrong? And more importantly, how to fix this?
And just to be frank; 'just use Gimp' is not a solution to getting MS Paint to work in Wine:-?

All help deeply appreciated:D

**[EDIT]** It must also be added that I have also followed [lkraemer]("http://ubuntuforums.org/member.php?u=365139")'s steps but that didn't work either.

---

### Post by sportfreak2020 on 2011-02-24
any updates on this thing .. i m basically stuck at this API-MS-WINE-CORE-* .DLL errors .. google hasnt been friendly today !!

---

### Post by lkraemer on 2011-06-18
For those having trouble, I believe you mis-read the copying directions.
I've updated the instructions to be more specific.  If you double check
what you did versus what should have been done, I think you can get it working.
You can check your history file to see what commands were executed.

I just installed MSPaint on Debian 6.0 with Wine 1.1.42 and it works fine.

Before you create the launcher use the following Terminal command to see
if it functions.
```

wine "/home/youruserlogin/.wine/drive_c/Program Files/MSPaint/mspaint.exe"

```

instead of this:
```

joshuajones@joshuajones-desktop:~/.wine/dosdevices/c:/windows/system32$ wine mspaint.exe

```


lkraemer

---

### Post by enduser on 2011-08-02
ok so i followed all the directions and got lots of dlls in place.
I have a few questions and am not afraid to break my build 

First off. Yes MS paint has some very basic functions which have not been adequately adapted into anything else like the background transparency toggle, the ability to select (screen capture) from a selected area and move it (this would be like select area float area move area merge layer in gimp: when in paint its a simple drag drop).  Also gimp only became tolerable after i realized i should save it as a bitmap (lossless compression) allowing me to see a preview instead of another weasel. until these minor ease of use items are properly reconciled I will always prefer paint.

1 does it matter if I copy the vista system 32 files and vista paint instead of the xp ones? (I think wine would be configured to the ME version then?)

2 I do not understand the latter part of #4 and #5. I made the folder but not the drwxr... part I assume that is something to use in the terminal. is it a straight copy paste? I am new to linux.  I know its changing read write access but what is all the after larry larry stuff?

Yes its very simple stuff for linux veterans, but no I don't know how to do it without asking yet. Is it just terminal Su password paste? or do I need to path each file in order to change it?

Could you break #4 up into logical steps to follow with the //commentary//?

Thanks

---

### Post by gyyug78fg87ogguiioioioioi on 2011-09-09
GNOME paint is microsoft paint clone for linux

[IMG]http://gnome-paint.googlecode.com/svn/wiki/Captura_de_tela.png[/IMG]

---

