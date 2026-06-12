---
title: "Finally MS Office 2010 works on Ubuntu."
date: 2011-11-22
forum: Wine
---

### Post by BC59 on 2011-11-22
I installed MS Office Professional 2010 on my Ubuntu computers and it's working fluently.

I followed the instructions from the Wine website. The whole procedure is only for experimental purposes.

1. Install Wine 1.3.35 beta through PPA.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3
```

2. Now start a new wine prefix or rename the hidden folder .wine in your Home directory (if you had Wine installed before).

From winetricks, 

Choose "Select the default wineprefix" then "Install a windows DLL or component" and from there install the **dotnet20** and **msxml6**, following the instructions.
Again from "Select the default wineprefix" choose "install a font" and select the **corefonts**.

From winetricks and "Select the default wineprefix" choose run "winecfg". From there go to tab "Libraries" and click on ***msxml6** then "Edit" and choose "Native (windows)".

3. Run the MS Office 2010 Professional x86 installer you have.
I used an .exe file. On Wine website they used an .iso mounted  (MS Office Pro Plus x86 2010). Choose to install only Word, Excell and Powerpoint.
I used a valid key and the online activation worked perfectly.

During the installation the installer was hang for a while but finally it completed the installation.

4. On winecfg as instructed above to the tab "Libraries" and from "new override for library" click the small arrow and choose to "Add" **riched20** and **gdiplus**. Then click on both, "Edit" and as above change their override to "Native (windows)".

5. Final steps.
Open Word, Excell and Powerpoint to see if they work. Then go to **each one** to File-options-Trust Center->Trust Center Settings, lower the security to none in every option and uncheck the Enable Protected View options. Word and Excell are working perfectly, the only problem is with Powerpoint which is not very dependable.

6. I succeed to install MS Office 2010 only to my Vaio AMD Laptop. On my desktop computer I tried a lot but failed. So I copied my .wine folder to it and everything worked like a charm.

Please post your experiences and your workarounds, because the installation is not easy, so far.

---

### Post by BC59 on 2011-11-22
I think before everything, on 64bits computers should be installed the package **ia32-libs**. The package concerns 32bits shared libraries for use on amd64 and ia64 systems.

It's because Wine is installing only the 32bits MS Office.

Install the package through Synaptic.

---

### Post by BC59 on 2011-11-23
And a screenshot with Office 2010 working with Office buttons on Unity Launcher.

---

### Post by BC59 on 2011-11-23
If you like to put the links of the Office 2010 apps to the Unity Launcher do the following:

Open the dash and write "word".

It appears the app Microsoft Word 2010. You click and drag it out to the desktop.

While on desktop it's loosing the icon view of Microsoft, but right click on it and go to Properties--Permissions-->Allow executing file as program and check it.

Now the icon view appears again.

You can drag the icon now up to Unity launcher. It stays there. Do the same for the rest of apps.

Problem: On the desktop stays the copy of the link, don't delete it because Unity link, is going as well.

So if you don't like to have the links on the desktop, create a folder on Home, with a name like .links and move them there. Then you have to drag and drop them again to Unity.

---

### Post by drmrgd on 2011-11-23
Very cool!  I can't wait to try this out when I get home.  I keep running into compatibility issues with some of my Excel macros and such in Libre Office.  As sad as this sounds, it will be excellent to be able to run MS Office again on my home computer!

---

### Post by 14218f4114b1fd99 on 2011-11-30
[FONT=Comic Sans MS][COLOR=RoyalBlue]Please may I have a copy of the .wine folder in a ZIP-file,  BC59

[/COLOR][/FONT]> **BC59 said:**
> So I copied my .wine folder to it and everything worked like a charm.
[FONT=Comic Sans MS][COLOR=RoyalBlue] [COLOR=Black]
[/COLOR][/COLOR][/FONT][FONT=Comic Sans MS][COLOR=RoyalBlue]This is what it said[/COLOR][/FONT]
[FONT=Comic Sans MS][COLOR=RoyalBlue][COLOR=Black]
[/COLOR][FONT=Verdana][COLOR=Black]> Setup encountered an error and has rolled back all changes[/COLOR] [/FONT][/COLOR][/FONT][FONT=Comic Sans MS][COLOR=RoyalBlue]:(](*,)

Thanks.[/COLOR][/FONT]

---

### Post by BC59 on 2011-11-30
The folder .wine has a size of 2GB. It's a little difficult to share.

---

### Post by 14218f4114b1fd99 on 2011-11-30
> **BC59 said:**
> The folder .wine has a size of 2GB. It's a little difficult to share.
I do not mind heavy downloads :KS

---

### Post by Lalaith on 2011-12-02
Hi BC59, 
it is a really interesting thread, thanks a lot. 

I already have installed MS Office 2007 with wine 1.2.3 (the available one from the repository) and I found a little annoying problem: when you try to shrink or cut images with Word, the page turns black while you're using this function, so you can't see the process when the image is changing, but only the results.

Could you check if it happens this to you?

Thank you.

---

### Post by BC59 on 2011-12-03
> **Lalaith said:**
> Hi BC59, 
it is a really interesting thread, thanks a lot. 

I already have installed MS Office 2007 with wine 1.2.3 (the available one from the repository) and I found a little annoying problem: when you try to shrink or cut images with Word, the page turns black while you're using this function, so you can't see the process when the image is changing, but only the results.

Could you check if it happens this to you?

Thank you.

No, I checked it and there isn't a problem like that.
Maybe you should install the latest Wine 1.3.32

---

### Post by Lalaith on 2011-12-03
> **BC59 said:**
> No, I checked it and there isn't a problem like that.
Maybe you should install the latest Wine 1.3.32

Sure I'll do, now that you've checked everything is ok with this version :D

---

### Post by BC59 on 2011-12-03
> **Lalaith said:**
> Sure I'll do, now that you've checked everything is ok with this version :D

Correction: The last version now on the WinePPA is Wine 1.3.33.

---

### Post by IWantFroyo on 2011-12-03
@BC59
Great instructions. This looks like HOWTO material. Have you thought about asking a mod to move it?

---

### Post by BC59 on 2011-12-03
> **IWantFroyo said:**
> @BC59
Great instructions. This looks like HOWTO material. Have you thought about asking a mod to move it?

I have no idea how I could do this.

---

### Post by IWantFroyo on 2011-12-03
Just click the "report abuse" button and ask for it to be moved. Report abuse is for getting to the mods more than actually reporting abuse (unless spam is involved).
It's at the bottom of each person's post.

You could also just PM a mod, but they'll probably appreciate it more if you just use the abuse button.

---

### Post by BC59 on 2011-12-03
Thanks, i'll try to do it.

---

### Post by Lalaith on 2011-12-08
I followed your instructions and now I have MS Office running without problems. I have installed the wine 1.3.34, though. 

I still have that "fade out to black" when I work with a picture but I still can see how is changing the image, so it's much moooore better. Furthermore, I'm suspecting this has nothing to do with wine and MSOffice. ;-)

---

### Post by BC59 on 2011-12-08
Yes you have right, it's already Wine 1.3.34 on the repository.
Very glad you manage to do it.

---

### Post by Dlambert on 2011-12-09
Just a question, why not just run LibreOffice? Just curious

---

### Post by IWantFroyo on 2011-12-09
> **Dlambert said:**
> Just a question, why not just run LibreOffice? Just curious

Sometimes you just need it for work. Although LO can do a lot, sometimes your job requires you to use it.

Or you just use it so much at work that you use it at home too, for consistency.

---

### Post by Dlambert on 2011-12-09
> **IWantFroyo said:**
> Sometimes you just need it for work. Although LO can do a lot, sometimes your job requires you to use it.
 
Or you just use it so much at work that you use it at home too, for consistency.
 
Ah, interesting. Thanks!

---

### Post by kurt18947 on 2011-12-10
> **Dlambert said:**
> Just a question, why not just run LibreOffice? Just curious

I am not in this position right now but if I were in a position of having to "round trip" MS formatted files, I'd probably need to use MS Office.   Round trip meaning receiving a file from an an MS office user, open it, edit it and send it onto another MS Office user.  Libre Office is very good but I don't know that LO's MS Office import/export utilities are perfect.

---

### Post by ojdon on 2011-12-12
I find that Office 2007 works, but is a little laggy using WINE 1.3 how does Office 2010 perform compared to 2007?

---

### Post by BC59 on 2011-12-12
> **ojdon said:**
> I find that Office 2007 works, but is a little laggy using WINE 1.3 how does Office 2010 perform compared to 2007?

It's very similar in performance. But has the advantage of being faster than 2007.

---

### Post by ojdon on 2011-12-12
I assume the trial installs correctly like the full version?

---

### Post by BC59 on 2011-12-12
I didn't try it but I cannot see why not.

---

### Post by cptrohn on 2011-12-13
I use 2007 with Play on Linux...  really simple to install that way.. Not sure if they have it ready for 2010 yet though.

There isn't a whole lot of difference between 2007 and 2010 though.

As for the question of why not just use LO?  Alot of times the table don't transfer correctly between Office and LO from my experience, I like LO, but it just isn't quite there completely yet... if they get those issues worked out I would use it all the time.

---

### Post by BC59 on 2011-12-14
> **cptrohn said:**
> I use 2007 with Play on Linux...  really simple to install that way.. Not sure if they have it ready for 2010 yet though.

There isn't a whole lot of difference between 2007 and 2010 though.

As for the question of why not just use LO?  Alot of times the table don't transfer correctly between Office and LO from my experience, I like LO, but it just isn't quite there completely yet... if they get those issues worked out I would use it all the time.

I understood he was speaking for difference under Wine. 2007-2010 as programs have a lot of differences, but as programs working under Wine they share a lot of common problems, like the ugly fonts.

---

### Post by gio10 on 2011-12-30
Thanks Guys!
It works with Lucid Lynx + wine 1.3.35.
Installation completed and the programs start without problems.

I have a question about registration. I have a legal copy but I'd like to be able to reinstall if needed in the future. For example if I do a new Ubuntu installation from scratch.
Do you know if this is possible? What kind of information are kept during registration? Software code, hw serial number?
Can I reuse the .wine directory "as is" in a new Ubuntu installation?

Thanks
gio10

---

### Post by BC59 on 2011-12-30
The problem with Microsoft programs is that you have a limited number of installations permitted. So if you exceed the number your code is considered hacked. It's better to reuse the .wine folder. Make a copy and you can use it in all your computers and as many times you want.

---

### Post by Cee Jay on 2012-01-02
Hi all!
First, thanks a lot guys for all your work. I really do appreciate that you re offering so much help to people like me. I m sorry for burdening you guys but I m really getting desperate...

I ve installed Ubuntu 11.10 (32 bit) and followed your instructions on how to get a legal copy of MS Office Home and Student 2010 to work (using the latest wine from the repositories and the MS Office 2010 DVD), but the installation was cancelled due to an "error during the installation process". As the installation procedure recommends, I ve included "Shared Office Features", "Office-Tools" and "Microsoft Visio Viewer", but I don t think this does disturb anything, does it?
The installation itself works alright up to the final step of applying updates. This step is going on forever (about half an hour) and finally leads an error which cancels the installation.
I ve tried to install MS Office 2010 before using PlayOnLinux but it doesn't work for Excel, which kept crashing while it was starting up. That s why I wanted to try your instructions hoping to finally succeed (after a couple of times formatting my whole system).

I ve already tried to use the repair function of the setup itself but it looks as if this doesn't start at all (the screen "Microsoft Office 2010 Home and Student is been repaired..." appears, but it doesn t do anything for at least half an hour until I cancelled the process). I ve also installed gdiplus, riched20 and vcrun2005 in order to succeed in installing Office 2010 properly, but it didn t work out, too.

Another try of repairing Office 2010 did start the proces, but failed ("Installation was unable to finish" or something like that). I don t think that it might be a problem that I m using a German version of Office 2010, would it?
During the repair process the terminal (in which started the install app using "wine setup.exe") reported some errors:
> err:msi:msi_install_assembly Failed to install assembly L"C:\\users\\cee\\Temp\\msid5.tmp\\Microsoft.VisualStudio.Tools.Applications.AddInAdapter.v10.0.dll" (0x00000001)
err:msi:ACTION_InstallFiles Failed to install assembly
err:msi:ITERATE_Actions Execution halted, action L"InstallFiles" returned 1603
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x1139ec), expect failure

Trying to remove Office 2010 has led to the errors:
> err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x112d74), expect failure
wine: Unhandled page fault on write access to 0x1100f849 at address 0x7bc468f9 (thread 0027), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --auto 14 36") (1115)
Read the Wine Developers Guide on how to set up winedbg or another debugger
 and to the abortion of the process ("Removing Office 2010 was not successful")

Changing the installed Office Applications leads to numerous errors reported in the terminal, but doesn t succeed either.

Do you have any idea what else I could try?
Thanks a lot in advance!
Best wishes,
Cee

---

### Post by tarjafan2011 on 2012-01-04
Hi

Only install the **whole** (so you get also the features of syllabication) word, powerpoint and excel, disable **all** the other dependencies. Removing is easy: just delete the whole ~/.wine, uninstall winetricks and wine so you are able to restart with the process.

Another tip for all users:
If you look for &quot;wingding.ttf&quot; in google, download the first link the font (alternatively you can copy it from your existing C:/windows/Fonts folder legally!) and put it in ~./wine/drive_c/windows/Fonts, restart Word/PP/Excel and then use the strange looking bullet points one by one; click on the ones which are made with the font called &quot;Bookshelf Symbol 7&quot; and set it to wingdings font. Then click &quot;bullet tab&quot; in the menu list above, &quot;add new bullet&quot; and use the new ones. So you get the &quot;usual&quot; bullets back!

BUT: Please remember this font is by windows, you SHOULD copy it ONLY if you have a valid windows license!  Edit: I use the german Office Plus version and it is working great for me, so it has nothing to do with the language package.

---

### Post by BC59 on 2012-01-09
> **Cee Jay said:**
> Hi all!
First, thanks a lot guys for all your work. I really do appreciate that you re offering so much help to people like me. I m sorry for burdening you guys but I m really getting desperate...

I ve installed Ubuntu 11.10 (32 bit) and followed your instructions on how to get a legal copy of MS Office Home and Student 2010 to work (using the latest wine from the repositories and the MS Office 2010 DVD), but the installation was cancelled due to an "error during the installation process". As the installation procedure recommends, I ve included "Shared Office Features", "Office-Tools" and "Microsoft Visio Viewer", but I don t think this does disturb anything, does it?
The installation itself works alright up to the final step of applying updates. This step is going on forever (about half an hour) and finally leads an error which cancels the installation.
I ve tried to install MS Office 2010 before using PlayOnLinux but it doesn't work for Excel, which kept crashing while it was starting up. That s why I wanted to try your instructions hoping to finally succeed (after a couple of times formatting my whole system).

I ve already tried to use the repair function of the setup itself but it looks as if this doesn't start at all (the screen "Microsoft Office 2010 Home and Student is been repaired..." appears, but it doesn t do anything for at least half an hour until I cancelled the process). I ve also installed gdiplus, riched20 and vcrun2005 in order to succeed in installing Office 2010 properly, but it didn t work out, too.

Another try of repairing Office 2010 did start the proces, but failed ("Installation was unable to finish" or something like that). I don t think that it might be a problem that I m using a German version of Office 2010, would it?
During the repair process the terminal (in which started the install app using "wine setup.exe") reported some errors:

Trying to remove Office 2010 has led to the errors:
 and to the abortion of the process ("Removing Office 2010 was not successful")

Changing the installed Office Applications leads to numerous errors reported in the terminal, but doesn t succeed either.

Do you have any idea what else I could try?
Thanks a lot in advance!
Best wishes,
Cee

The installation works only with certain versions of MSOffice. I had the same problem with ones and succeeded with others.
The best way to get rid of a bad installation is to remove the folder .wine from home directory and force Wine to create a new one. Unless you have important Windows programs installed inside.
If you don't like to create a new .wine folder you can remove manually MSOffice, deleting the folders. In that case you have to manually clean the registry as well.

---

### Post by Juanchitoman on 2012-02-01
Thanks a lot :D

The only 'issue' I have is that the icons are the wine glasses, making it annoying to distinguish, is there a way to assign the right icon of "word" to "word" and respectively? or will I have to stay forever with the wine glass icon?

Thanks :))

---

### Post by BC59 on 2012-02-01
Of course there is way to do it. You can download icons from internet. Search for icons .png and size 32 or 64 I'm not sure. 
You have to store them to somewhere, like in the .wine folder, for example. 
Then drag a Word link from dash to the desktop. Right click and you have the properties. From there push the icon of Wine and opens the browse dialogue. Browse up to the downloaded icons. Choose the Word .png and that's it.

---

### Post by Juanchitoman on 2012-02-01
I want to thank for three things:

First, thanks for your availability to answer my question and others';
Second, thanks for answering right away, even though the last post was 3 weeks ago;
And finally, thanks for the answer and the post itself, now I can have the potential of MS office on my Ubuntu

Thanks!

---

### Post by BC59 on 2012-02-01
Any time!

---

### Post by GemJonno on 2012-02-02
Hi,

I followed your instructions to the letter yet still cannot install MS Office 2010. Just under half-way through installation I get "..encountered an error during setup".


I'm getting really desperate here, any ideas?

---

### Post by BC59 on 2012-02-02
I think that the only version you can install is the MS Office 2010 Professional 32b.
Even if your computer uses 64b architecture, the Wine machine should be of 32b.
Here are the instructions on how to do it:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by GemJonno on 2012-02-02
This is already as it should be. I've tried literally everything.

EDIT: The programs appear in my Wine menu, but when I click them nothing happens.

---

### Post by BC59 on 2012-02-02
With Wine 1.4 almost ready I think it will be easier to do it.
[http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/](http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/)
You have to wait a few days more.

---

### Post by GemJonno on 2012-02-02
> **BC59 said:**
> With Wine 1.4 almost ready I think it will be easier to do it.
[http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/](http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/)
You have to wait a few days more.

My Wine version is showing as Wine 1.4-rc1

---

### Post by BC59 on 2012-02-02
Well in that case you have to try downloading from internet, of another Office copy, to see if there is a difference in the installation.

---

### Post by allen303allen on 2012-02-09
Thanks BC59! According to your steps, I get a successful installation of office 2010 Professional Trial, but find some annoying problems:
1. With word, everything seems fine until I click the save button, without any response, and the cursor shows working status, the terminal keeps printing "err:clipboard:ChangeClipboardChain hWndViewer is lost", and the process ends in some minutes.
2. With powerpoint, I can't input any Chinese words(I use the Chinese version of office), and as soon as I press F5, shows a prompt "PowerPoint detected that your graphics card may be configured incorrectly , can not get the best slide show experience"(the description is translated by me), when I click OK, the screen turns black, and nothing more happen, seems dead, I can only kill the process.

Any help will be very appreciated.
allen

PS: I work on ubuntu 10.10 with wine 1.3.36.

---

### Post by BC59 on 2012-02-10
> **allen303allen said:**
> Thanks BC59! According to your steps, I get a successful installation of office 2010 Professional Trial, but find some annoying problems:
1. With word, everything seems fine until I click the save button, without any response, and the cursor shows working status, the terminal keeps printing "err:clipboard:ChangeClipboardChain hWndViewer is lost", and the process ends in some minutes.
2. With powerpoint, I can't input any Chinese words(I use the Chinese version of office), and as soon as I press F5, shows a prompt "PowerPoint detected that your graphics card may be configured incorrectly , can not get the best slide show experience"(the description is translated by me), when I click OK, the screen turns black, and nothing more happen, seems dead, I can only kill the process.

Any help will be very appreciated.
allen

PS: I work on ubuntu 10.10 with wine 1.3.36.

Did you try to make a new installation to see if the problems, doesn't appear in the new machine? You could rename .wine folder and keep it aside. Then try again the whole procedure (wine automatically creates a new .wine folder). If there is no solution ,delete the newly created folder and restore the old one.

---

### Post by forrestcupp on 2012-02-10
> **Lalaith said:**
> 
I already have installed MS Office 2007 with wine 1.2.3 (the available one from the repository) and I found a little annoying problem: when you try to shrink or cut images with Word, the page turns black while you're using this function, so you can't see the process when the image is changing, but only the results.

I just installed Office 2007 from steps I found on another site that were almost identical to the original post here, except I'm still using the stable Wine 1.2.3. It works perfectly, even resizing images. You don't have to have the latest beta of Wine to fix that; you just have to do all of the dll and font stuff from Winetricks, and it works. I couldn't use the Wine beta because some regressions caused something else to not work well. You might have to have the beta for 2010, though, I don't know.

But I'll say that I'm pretty impressed with 2007 running with Wine. It seems just as fast as on Windows, and Word opens in a fraction of the time that Writer takes to open.

---

### Post by wieman01 on 2012-02-15
Did anyone get **Office Home & Student 2010** to work? It crashes halfway through when I try to install it although I am following these instructions.

I am on Kubuntu 11.10 and installed Wine from the repositories.

---

### Post by wieman01 on 2012-02-19
_**UPDATE:**_

I installed the latest version of Wine (1.3) last night and was able to install Microsoft Office 2010 (Home and Student) with no further issues.

---

### Post by forrestcupp on 2012-02-19
> **wieman01 said:**
> _**UPDATE:**_

I installed the latest version of Wine (1.3) last night and was able to install Microsoft Office 2010 (Home and Student) with no further issues.

1.3 must be necessary for 2010, but not 2007.

---

### Post by Dlambert on 2012-02-19
Might as well install 1.4-RcX for latest performance.

---

### Post by forrestcupp on 2012-02-20
> **Dlambert said:**
> Might as well install 1.4-RcX for latest performance.

As long as there aren't any regressions. I'm kind of afraid to. I have a couple of things that work in 1.2.3 that won't work with 1.3.

---

### Post by TheFu on 2012-02-20
> **Dlambert said:**
> Just a question, why not just run LibreOffice? Just curious

When you work with a team, slight font differences cause major issues in layout, pagination, even section headings are screwed.  Also, LibreOFfice "**track changes"** probably does not play well with MS-Office users.  I haven't tried it recently, but last time using track changes corrupted the file so that the MS-Office people couldn't open it.

Another reason is embedding MS-Visio diagrams.  For me, **MS-Visio is THE killer app** with no alternative. Adding Visio diagrams inside LibreOFfice docs didn't work the last time I tried it - sure, I could embed an image, but not the "object".

In a mixed corporate environment, 100% compatibility is mandatory. I'm unwilling to be "that guy" who can't play well with others at work.

When I work alone, I use LibreOffice because I prefer the interface. 
When I'm sharing documents in a team inside and outside my company, MS-Office is mandatory.  

I wish the world were different.

---

### Post by JSinghJ on 2012-03-06
Thanks for this so much!!!! Im new to Ubuntu and realised that I could not live without MS word because LibreOffice Writer is not up to standards. :KS:P

---

### Post by wieman01 on 2012-03-07
> **JSinghJ said:**
> Thanks for this so much!!!! Im new to Ubuntu and realised that I could not live without MS word because LibreOffice Writer is not up to standards. :KS:P
:-# Don't say that, you will cause a flame war in here. :-) But I am with you.

---

### Post by forrestcupp on 2012-03-09
> **forrestcupp said:**
> As long as there aren't any regressions. I'm kind of afraid to. I have a couple of things that work in 1.2.3 that won't work with 1.3.

Everything I had works well with 1.4 rc6. That makes me happy.

---

### Post by deepla on 2012-03-10
Hi 
I am getting this error

sudo add-apt-repository ppa:ubuntu-wine/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

Can someone help please
Thank you

---

### Post by deepla on 2012-03-10
I have already installed wine 1.3 through synaptic. I was trying to install dotnet20 msxml6 but they are not downloading.so i tried updating and found that the wine updates are not being downloaded for lack of authentication key. So i tried the above method to add the repositories and got the error. 
I am on HP 210 mini netbook with ubuntu 11.1

The internet connection is fine and i changed the download servers but same result............

---

### Post by lammrag on 2012-03-10
Thanks for the install manual.

I have the following comments:

[LIST]
[*]Winbind has to be installed (sudo apt-get install winbind)
[*]I copied /etc/mono/2.0/machine.config (cp /etc/mono/2.0/machine.config ~/.wine/drive_c/windows/Microsoft.NET/Framework/v2.0.50727/CONFIG/)
[*]For me, setup.exe just closed when only showing about 70% progress and I thought it failed, but then I had Word, Excel and Powerpoint in my start menu and all work fine
[/LIST]

---

### Post by deepla on 2012-03-10
> **deepla said:**
> Hi 
I am getting this error

sudo add-apt-repository ppa:ubuntu-wine/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

Can someone help please
Thank you

I was using the wifi(automatic DHCP). But then i tried with my mobile broadband connection which uses automatic PPP I and i could add the repository. Then i could update with update manager with my wifi connection. I had to check for updates again in update manager before i could install them.(without that, it was giving error that winetricks is not safe source to download or something like that )  But i could not install dotnet20 and msxml6 with the wifi. But with mobile broadband i could do it. I am not sure but it may be to do with opening of port 11371 in the router of wifi.
link

---

### Post by claysql on 2012-03-12
I was able to connect and update the repository as root.[FONT=monospace]

[/FONT]

---

### Post by byline on 2012-04-07
If anyone with a WORKING Office 2010 installation under Wine could post the DLL overrides they have set under Configure Wine, Libraries that might be helpful to me.

---

### Post by forrestcupp on 2012-04-07
> **byline said:**
> If anyone with a WORKING Office 2010 installation under Wine could post the DLL overrides they have set under Configure Wine, Libraries that might be helpful to me.

The first post tells you exactly what you need to do to get it working. You may have to uninstall it and redo it exactly like that post says. If you already have the latest version of Wine, you can skip to section 2.

---

### Post by byline on 2012-04-07
Installed as described, but cannot open or save files under Word 2010.  So I wanted to make sure there wasn't something simple I could correct.  Have purchased a copy of Office 2010 University edition so I'm not sure I can re-install on the same computer or not.

---

### Post by forrestcupp on 2012-04-07
> **byline said:**
> Installed as described, but cannot open or save files under Word 2010.  So I wanted to make sure there wasn't something simple I could correct.  Have purchased a copy of University edition so I'm not sure I can re-install on the same computer or not.

You should be able to reinstall it with no problems, if it's on the same computer.

If it's not working for you, you may want to try installing it with PlayOnLinux, instead. PlayOnLinux is in the repos. It only comes with support for installing up to Office 2007, but [here is a link](http://www.playonlinux.com/repository/?script=801) to an official PlayOnLinux script to install Office 2010. Just download the link, open up PlayOnLinux, and go to **Tools->Run a local script**. Then point it to the script you downloaded, and it will go through the process to install Office 2010 for you.

If you use PlayOnLinux, it makes it very easy to install things properly, but you won't be able to associate your Word and Excel files easily. If you want to do that, check out [this HowTo](http://ubuntuforums.org/showthread.php?t=1940522) I wrote to take you through manually setting up Ubuntu to associate your files with the Office that is installed with PlayOnLinux. The HowTo is for 2007, so you might need to change some names that will be obvious.

I would remove your Wine installation of Office first.

---

### Post by byline on 2012-04-08
Forrestcupp,

Well, I went into Synaptic and marked wine1.3 for complete removal, then went to my home directory to make sure the ./.wine directory was deleted.  Installed dotnet20 and msxml6 using wineprefix, and set a DLL override for *msxml6 to Native (Windows).  Installed corefonts as described at beginning of thread.

Then ran the Office 2010 setup.exe file again under wine and installed Excel, Word, Office shared features and Office tools alone.  You're right, no problem re-installing this MS software on the same hardware - I wasn't sure what kind of nonsense Microsoft was up to these days.

Via winetricks set DLL overrides for riched20 and gdiplus to Native.

Have the same issue with Word (can't open or save files) and Excel (comments that the .xlsx file is of a different format than what is indicated by the file extension, still seems to work though) as before.

Maybe I'm not interpreting the "lower the security settings to none in every option" instruction correctly and that is causing problems ?  There doesn't appear to be as simple an option as selecting "none".  For example, on the Trust Center ActiveX page does that mean selecting "Enable all controls without restriction and without prompting?" (see attachment)

---

### Post by forrestcupp on 2012-04-08
> **byline said:**
> Forrestcupp,

Well, I went into Synaptic and marked wine1.3 for complete removal, then went to my home directory to make sure the ./.wine directory was deleted.  Installed dotnet20 and msxml6 using wineprefix, and set a DLL override for *msxml6 to Native (Windows).  Installed corefonts as described at beginning of thread.

You might have to have Wine 1.4 for it to work completely, but I'm not sure.

If you're still having trouble, you should remove it again, and try installing it using PlayOnLinux and the Office 2010 script, like I said in my previous post. I'll bet you can get it working if you do it that way.

---

### Post by byline on 2012-04-08
wine1.3 is actually the package name - basically wine1.3 being the beta version and wine1.2 being the stable version.  The current version of the beta (from the ubuntu-wine/ppa repository) is actually 1.4 which is what I tried.

I completely uninstalled wine as before, and installed playonlinux as you suggested.  Then ran the Office 2010 installation script listed for it under the Applications, Testing page.  It automatically installs a particular version of wine, and sets many DLL overrides, etc as this ubuntuforums.org thread has previously described.  Not identical, but similar.

At any rate, the errors I described above are still occurring for Word 2010 and Excel 2010 and I note that [www.codeweavers.com](www.codeweavers.com) lists fairly low "bronze" compatability ratings for both Excel 2010 and Word 2010.  So my experiences aren't that far off of that.

I will wrap this up for the time being and start investigating running Windows under a virtual box and installing Office 2010 on that.  Oh well.

---

### Post by forrestcupp on 2012-04-09
> **byline said:**
> 
I will wrap this up for the time being and start investigating running Windows under a virtual box and installing Office 2010 on that.  Oh well.
Sorry it didn't work out for you. I'm running 2007, so I don't really have experience with 2010. Maybe someone else will come along later that can help. This is a pretty long thread, and no one else has complained about something that is used as much as what you're talking about. There has to be some way to get it to work.

However, I also have Office installed in a virtual machine because things like Publisher and Access won't work at all in Wine. VirtualBox has progressed to the point that I'm pretty impressed with it. It's still not as handy as being able to just open Word from Ubuntu, though. If you do that, maybe check out the seamless mode, and it might make things a little better for you.

---

### Post by Lockheed on 2012-04-24
This how-to omits a very important thing - if you have a 64-bit system, it will fail on installation of Net2.0 and MSXML.

Therefore, you need to manually install those two files:
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523)
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276)

---

### Post by forrestcupp on 2012-04-24
> **Lockheed said:**
> This how-to omits a very important thing - if you have a 64-bit system, it will fail on installation of Net2.0 and MSXML.

Therefore, you need to manually install those two files:
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523)
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276)

I never had that problem before I switched to Precise. I was wondering if it has to do with Multiarch. Anyway, I tried installing the x64 versions manually, and still couldn't get things to work. Did you actually get everything to work by doing that? I ended up resorting to PlayOnLinux.

---

### Post by Lockheed on 2012-04-24
Installation of net2.0 64 goes through, but fails at the end, which I did not notice before. I was still able to run the office 64 installer, but it crashed at around 70%.

So I am no trying to get it installed at 32bit, and I did, but it is not what I wanted (no Office shortcuts in menus, missing bullet point formats etc).

---

### Post by aku506 on 2012-04-24
It doesn't work on me. It installed well but I'm not able to use some pop-up menus like page number one. This does software useless. Does it work on others? And do somebody know how to fix this?

I've 12.04 LTS beta and 11.10 and bug affects on both computers.

---

### Post by forrestcupp on 2012-04-24
Since I switched to Precise, I ended up having to use PlayOnLinux to install Office correctly. PlayOnLinux can manage multiple versions of Wine, and it uses an older version to run Office. I installed 2007, but their web site has a good script to plug into it that will install Office 2010 perfectly.

The only problem is that PlayOnLinux doesn't set it up so that you can associate files or have menu entries. Lucky for you guys, [I made a HowTo](http://ubuntuforums.org/showthread.php?t=1940522) that explains how to do all of that manually. :)

---

### Post by Jongast on 2012-05-17
Hey I've been perusing this thread a while and I was wondering if anyone was getting a similar bug when installing Office 2010, I've tried several times and if anyone has had a similar issue I'd be grateful for any help here's a screen shot of my bug, almost installs  then at the last percentage I get this message:


EDIT: I'd missed out on one of the steps after going native windows override in the librairie section, works perfectly now, thanks a lot to everyone who posted on this forum to help out beginners like me (Especially BC59)

---

### Post by fabricio.lemos on 2012-05-29
It's is not working for me in Precise 12.04 64. The dotnet20 install fails saying it cannot install in a 64 bit OS. I also tried PlayOnLinux, but it requires a DVD or an ISO, which I don't have.

I purchased Office Home 2010 in Microsoft Store and the installer is an exe file.

---

### Post by MBybee on 2012-05-29
> **forrestcupp said:**
> Since I switched to Precise, I ended up having to use PlayOnLinux to install Office correctly. PlayOnLinux can manage multiple versions of Wine, and it uses an older version to run Office. I installed 2007, but their web site has a good script to plug into it that will install Office 2010 perfectly.

The only problem is that PlayOnLinux doesn't set it up so that you can associate files or have menu entries. Lucky for you guys, [I made a HowTo](http://ubuntuforums.org/showthread.php?t=1940522) that explains how to do all of that manually. :)

PlayOnLinux is good - and their Office2010 installer works pretty well. Lots of issues with Outlook SP1+ though.
If you can get the pre-SP1 32bit version it apparently works.

---

### Post by winjeel on 2012-07-31
Thanks for the instructions, BC59.

I've tried to follow the instructions, but I wasn't sure was was meant by "Now start a new wine prefix or rename the hidden folder .wine in your Home directory".  It is already there. Otherwise, I had wine and winetricks freshly installed already and followed all of the other instructions precisely. I'm using 12.04 64-bit, and Wine 1.4, with MS Office 2010. The error message I get is:
> Setup is unable to proceed due to the following error(s):
The instillation of Microsoft Office 2010 requires that MSXML version 6.10.1129.0 be installed on your computer. Install this component and re-run setup.
Correct the issue(s) listed above and re-run setup.How? Thanks in advance for the help.

---

### Post by KaisaUbun2 on 2012-08-04
> **BC59 said:**
> I think before everything, on 64bits computers should be installed the package **ia32-libs**. The package concerns 32bits shared libraries for use on amd64 and ia64 systems.

It's because Wine is installing only the 32bits MS Office.

Install the package through Synaptic.

I wish somebody had told me this step earlier. I have a partial of the msi thing installed now i cannot reinstall it, what do i do?

---

### Post by bookcrazy on 2012-09-06
When I get to step 3, I get this message:

"This program requires XP (or later) operating system"

The version of office I have is:
English Office Professional Plus 2010 W32

Any ideas?



> **BC59 said:**
> I installed MS Office Professional 2010 on my Ubuntu computers and it's working fluently.

I followed the instructions from the Wine website. The whole procedure is only for experimental purposes.

1. Install Wine 1.3.35 beta through PPA.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3
```

2. Now start a new wine prefix or rename the hidden folder .wine in your Home directory (if you had Wine installed before).

From winetricks, 

Choose "Select the default wineprefix" then "Install a windows DLL or component" and from there install the **dotnet20** and **msxml6**, following the instructions.
Again from "Select the default wineprefix" choose "install a font" and select the **corefonts**.

From winetricks and "Select the default wineprefix" choose run "winecfg". From there go to tab "Libraries" and click on ***msxml6** then "Edit" and choose "Native (windows)".

3. Run the MS Office 2010 Professional x86 installer you have.
I used an .exe file. On Wine website they used an .iso mounted  (MS Office Pro Plus x86 2010). Choose to install only Word, Excell and Powerpoint.
I used a valid key and the online activation worked perfectly.

During the installation the installer was hang for a while but finally it completed the installation.

4. On winecfg as instructed above to the tab "Libraries" and from "new override for library" click the small arrow and choose to "Add" **riched20** and **gdiplus**. Then click on both, "Edit" and as above change their override to "Native (windows)".

5. Final steps.
Open Word, Excell and Powerpoint to see if they work. Then go to **each one** to File-options-Trust Center->Trust Center Settings, lower the security to none in every option and uncheck the Enable Protected View options. Word and Excell are working perfectly, the only problem is with Powerpoint which is not very dependable.

6. I succeed to install MS Office 2010 only to my Vaio AMD Laptop. On my desktop computer I tried a lot but failed. So I copied my .wine folder to it and everything worked like a charm.

Please post your experiences and your workarounds, because the installation is not easy, so far.

---

### Post by Koen82 on 2012-09-20
Thanks for the instructions!

I'm using Ubuntu 12.4 and Microsoft Office Professional Plus 2010 and it seems to work perfect.

---

### Post by Koen82 on 2012-09-20
Go to Wine configuration and select Windows XP.

---

### Post by winjeel on 2012-09-20
I used Play on Linux. It is really easy to use, and it installed Wine and all components needed, and now I have Office 2010 running on a 64bit 12.04LTS, no problem, no sweat.

---

### Post by bookcrazy on 2012-09-22
Thank you! I took your advice and installed Office 2010 Pro, that I got through my university, through Play on Linux and it works like a charm! Now I just need to read back through and find the post where people were talking about how to integrate office icons into the launcher.

Thanks again! 

> **winjeel said:**
> I used Play on Linux. It is really easy to use, and it installed Wine and all components needed, and now I have Office 2010 running on a 64bit 12.04LTS, no problem, no sweat.

---

### Post by winjeel on 2012-09-22
> **bookcrazy said:**
> Thank you! I took your advice and installed Office 2010 Pro, that I got through my university, through Play on Linux and it works like a charm! Now I just need to read back through and find the post where people were talking about how to integrate office icons into the launcher.

Thanks again!

Play On Linux put buttons on the desktop, so I don't need to spend too much time trying. I've also installed Classic Menu Indicator, so it shows the old style Ubuntu menu. Using the Classic Menu Indicator you can find the Wine menu and you'll see the icons there... I just checked, it doesn't. Hmm. Let me know if you've found a way. :p

---

### Post by fmacademia on 2012-10-01
Good day!

I was installing MS Office 2010 through wine. I canceled the installation because I need to do something else. When I was trying to install Ms Office 2010 again, it won't reach the installation like before. How can I make it work again?

---

### Post by eugen_nicoara on 2012-10-03
Hey!
I'm trying to install Office 2010 on a Ubuntu 12.04 64 bits virtual machine. I've tried with Playonlinux (as described here: [http://mylinuxexplore.blogspot.com/2012/07/how-to-install-ms-office-2010-in-linux.html]("http://mylinuxexplore.blogspot.com/2012/07/how-to-install-ms-office-2010-in-linux.html")), I'va also tried as described in this thread, I've tried with 32 and 64 bits MS Office releases but none of these worked.
Those of you who succeeded, can you please come up with a more detailed description? I'm especially looking for Linux 64 bits details as most of the post I've found with Google doesn't make and distinction between 32 and 64 bits Linux releases.
Regarding this particular post I've quoted, I managed to install the 64 bits version of msxml6 (msxml6_x64.msi) but the dotnet (NetFx64.exe) installation always fails.
Thanks!

> **Lockheed said:**
> This how-to omits a very important thing - if you have a 64-bit system, it will fail on installation of Net2.0 and MSXML.

Therefore, you need to manually install those two files:
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6523)
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6276)

---

### Post by eugen_nicoara on 2012-10-25
Finally I've made it! Here is how I installed MS Office 2010 32 bits on Ubuntu 12.04 64 bits:
0. [OPTIONAL] Remove the .wine folder in case you don't have any other apps already installed on wine. This would ensure a clean install.
```
rm -rf ~/.wine
```
1. Install ia32-libs package (~156MB)
```
sudo apt-get install  ia32-libs
```
2. Install latest and greatest from Wine (~358 MB)
```
sudo add-apt-repository ppa:ubuntu-wine/ppa; sudo apt-get update; sudo apt-get install wine1.5
```
3. Open a console (assuming bash is the default shell). All the subsequent commands shall be run using this console.
4. Set the WINEARCH environment variable to win32
```
export WINEARCH=win32
```
5. Run winetricks
```
winetricks
```
Choose "Select the default wineprefix" > "Install a windows DLL or component" and install dotnet20 and msxml6. You'll have to download dotnetfx.exe, run winetricks and do this step again.
Choose "Install a font" > "corefonts".
Choose "Run winecfg" > "Libraries" > "*msxml6" > "Edit" and choose "Native (windows)"
6. Exit winetricks
7. Run whatever MS Office 2010 Professional x86 32 bits installer you've got. I downloaded the 60 days trial version.
```
wine ./X17-75058.exe
```
8. Run winetricks
```
winetricks
```
Choose "Select the default wineprefix" >  "Run winecfg" > "Libraries" >  select riched20 and gdiplus from "new override for library" and choose to "Add" and then edit and select "Native (windows)" for each of them
9. If you're using Gnome (like I do) go to Applications > Wine > Programs > Microsoft Office and launch the applications. If you're using Unity, just type the name of the application (e.g. Word).
10. Enjoy!
Note: This is a compilation of other posts.

---

### Post by miatawnt2b on 2012-10-31
Problem is the activation.  I cannot activate using latest wine/office 2010 32bit/ubuntu 12.04 64bit.

-J

---

### Post by crazyg4merz on 2012-11-04
> **BC59 said:**
> I installed MS Office Professional 2010 on my Ubuntu computers and it's working fluently.

I followed the instructions from the Wine website. The whole procedure is only for experimental purposes.

1. Install Wine 1.3.35 beta through PPA.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3
```

2. Now start a new wine prefix or rename the hidden folder .wine in your Home directory (if you had Wine installed before).

From winetricks, 

Choose "Select the default wineprefix" then "Install a windows DLL or component" and from there install the **dotnet20** and **msxml6**, following the instructions.
Again from "Select the default wineprefix" choose "install a font" and select the **corefonts**.

From winetricks and "Select the default wineprefix" choose run "winecfg". From there go to tab "Libraries" and click on ***msxml6** then "Edit" and choose "Native (windows)".

3. Run the MS Office 2010 Professional x86 installer you have.
I used an .exe file. On Wine website they used an .iso mounted  (MS Office Pro Plus x86 2010). Choose to install only Word, Excell and Powerpoint.
I used a valid key and the online activation worked perfectly.

During the installation the installer was hang for a while but finally it completed the installation.

4. On winecfg as instructed above to the tab "Libraries" and from "new override for library" click the small arrow and choose to "Add" **riched20** and **gdiplus**. Then click on both, "Edit" and as above change their override to "Native (windows)".

5. Final steps.
Open Word, Excell and Powerpoint to see if they work. Then go to **each one** to File-options-Trust Center->Trust Center Settings, lower the security to none in every option and uncheck the Enable Protected View options. Word and Excell are working perfectly, the only problem is with Powerpoint which is not very dependable.

6. I succeed to install MS Office 2010 only to my Vaio AMD Laptop. On my desktop computer I tried a lot but failed. So I copied my .wine folder to it and everything worked like a charm.

Please post your experiences and your workarounds, because the installation is not easy, so far.

Tried using this tutorial but failed at halfway of office2010 installation. Showed a mscorsvc.exe(if I'm not wrong)
error. Anybody?

---

### Post by Nube101 on 2012-11-08
I installed MS Office 2010 and works fine, but I can't get it to activate. every time a try I get a "Microsoft Professional plus 2010 configuration did not complete successfully" Message. I contacted Microsoft for help. They don't have support for wine, and recommended I should buy windows 8 and install it.

---

### Post by miatawnt2b on 2012-11-08
same activation problem here. are you running 64bit ubuntu?

I think the best option here if you want to run Office and bot be plagued with bugginess is to load windows7 in a Virtualbox VM, and run Office 2010 from there.  With Seamless Mode, it's almost like running it natively.  Would be nice if you could set program launchers in gnome to launch an application in a VM.

I heavily rely on Office, Visio, & Powerpoint for work.  I have been running these under wine/cxoffice for quite a while. They are buggy no matter how you cut it. I am moving to a VM solution as I can't rely them to be stable in native linux.  Shame really.

-J

---

### Post by Nube101 on 2012-11-09
> **Nube101 said:**
> I installed MS Office 2010 and works fine, but I can't get it to activate. every time a try I get a "Microsoft Professional plus 2010 configuration did not complete successfully" Message. I contacted Microsoft for help. They don't have support for wine, and recommended I should buy windows 8 and install it.

I am looking for a solution that won't require me to purchase windows, my budget is a bit tight after having to have purchased MS Office 2010.

---

### Post by maschmagic on 2012-11-19
I too am having problems activating MS Office 2010 on PlayonLinux with Ubuntu.

Any ideas?

---

### Post by t.rei on 2012-11-21
Playonlinux worked for me. I had to upgrade to the latest version from their ppa before it would finish, but as far as I can tell it works smoothly now. Still need to create proper launchers for menu and dock, but that's probably easy as pie.

---

### Post by eugen_nicoara on 2012-11-22
Have you found a solution for the activation issue?

---

### Post by alexbungker on 2012-11-27
> **BC59 said:**
> I think before everything, on 64bits computers should be installed the package **ia32-libs**. The package concerns 32bits shared libraries for use on amd64 and ia64 systems.

It's because Wine is installing only the 32bits MS Office.

Install the package through Synaptic.

I wonder how you did the things.. I use ubuntu 12.10 64bit and it says "MSXML6.0 not supported on the current processor type" and I did not manage to setup the dotnet as the installer says I already have the newest one.

I'm using wine 1.5 I installed from ppa.

any thought very much appreciated!

---

### Post by maschmagic on 2012-11-28
> **eugen_nicoara said:**
> Have you found a solution for the activation issue?

Yeah, I finally got it working.

First of all, you must check if you are using KMS to activate, which is a license server installed at your college/workplace. If you are using a MAK, then I'm not sure.

To do this, go to a Windows machine (I tried with Win7) that is connected to your college/work network. Open a command prompt and type (without brackets).
[FONT=&quot]"slmgr /dlv" 

Wait a while, and a popup will appear detailing the Software licensing service details. Look carefully and find "KMS machine name from DNS". This is your KMS ip address, write it down. The last 4 digits of the ip address is the port number. (So really all up to the last :xxxx is your ip address excluding the port number).

Now open PlayOnLinux. Choose Install A Program.
Next to the search field, tick on Testing.

Then search for Microsoft Office 2010 Activation.

It will ask you for your IP address, and your port number.

After keying in those, and finishing the install, close PlayOnLinux and restart it again.

Now open Word 2010 or Excel 2010, and it should activate.

Good luck! Let me know if this works (or doesn't)

[/FONT]

---

### Post by burning-daylight on 2012-12-13
Having problems enabling solver. Excel crashes when i go to 
File -> options -> Add-Ins -> Manage Excel Add-Ins (Go) -> enable "Solver" -> OK
Program crashes :(

Also can't make OriginPro graph embedding work. I can "paste", but whenever I click "edit" on it later on (or just double click) - MSWord crashes.

---

### Post by chrisc200 on 2013-01-01
Can someone please share their font experiences with office 2010? for example I noticed all the fonts in general look blurry. Have tried everything like font smoothing etc.

What was the experience with fonts when installing with play on linux?

---

### Post by SirKingChase on 2013-02-16
Are you guys able to save and open files?

I installed it using the directions in this thread, however I can not save or open  files.

EDIT:Broke down and just installed playonlinux, works flawlessly.  I think it didnt work because I am using latest version of wine.  PlayonLinux doesnt bother with trying to make it work with the latest version.  It downloads a version of Wine that is known to be compatible with it and configures it that way, pretty smart app.

---

### Post by rmcellig on 2013-06-29
So far I can access Word, Excel and Powerpoint but the app I really need to get working is MS Outlook. It does not work. What do I need to do to get it to work?

---

### Post by Fincer on 2014-04-14
If someone needs instructions on how to install and activate Office 2010 products (Word, Excel, Powerpoint + Project + Visio) in the recent Wine versions (1.7.X), download the following tutorial:

[http://www61.zippyshare.com/d/25626769/46436/HOWTO%20-%20Installation%20of%20Office%202010%20under%20Wine.pdf](http://www61.zippyshare.com/d/25626769/46436/HOWTO%20-%20Installation%20of%20Office%202010%20under%20Wine.pdf)

By following the instructions, activation of Office 2010 is possible.

PlayOnLinux is not required.

If you need to uninstall Office products, simply delete the prefixes you create.

---

