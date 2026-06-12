---
title: "Fix - Google Sketchup 6 and Missing OpenGL"
date: 2008-01-25
forum: Wine
---

### Post by MaxVK on 2008-01-25
Iv seen quite a few posts that mention the problem with Sketchup 6, where it stops during loading and warns you that you do not have OpenGL available. I had this problem.

Fix:
Open your wine menu and open the C drive (/home/user/.Wine)
Open the Windows Folder
Find Regedit.exe and run it with Wine
Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1
Run Sketchup 6
No more error on startup and the program seems to run just fine on NVIDIA 6600, Ubuntu 7.10

Good luck

---

### Post by K.Mandla on 2008-01-25
Moved to Wine subforum.

---

### Post by IanW on 2008-01-26
In my case, this cures Sketchup not starting, but then it froze trying to open the "Instructor" window.

I fixed it by using Regedit.exe as above to find the "/Google/Sketchup6/SnappyInstructor" key, and changing the "show" entry to 0 (zero).
Sketchup can then start from the Wine menu entry as normal, and you can turn the Instructor window back on from Sketchup's "Window" menu.

This was with a fresh download of the latest version of Sketchup from Google, and Wine 0.9.53

---

### Post by MaxVK on 2008-01-26
I had something similar, although not a freeze-up, but that was only because I already said 'No' to allowing it to download Gecko. As soon as I allowed that everything worked just fine.

---

### Post by Epic Plecostomus on 2008-02-02
HOORAY!  IS FIXED!

Only one tiny annoying glitch-bug... my menu-bar and icons (in sketchup) go black, I can mouse over them to spot them but it's annoying.

HOWEVER!   At least the core function of the program is working.    *happy dance*

---

### Post by Muscar on 2008-02-03
I still won't work, I start it up, it says: starting google sketcup then it just disappears. :confused:

---

### Post by Epic Plecostomus on 2008-02-03
The more information we have the better we can help.   What can you tell us about your WINE setup?   How about your video card?   What sort of computer?

---

### Post by realthor on 2008-02-04
Hi, I had the same problem with my gutsy install and I did the regedit.exe thing but no luck, it wouldn't pop the error any more but the program would die silently. I run it from a terminal and got:

florin@Maya:~$  wine "C:\Program Files\Google SketchUp 6\SketchUp.exe"fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  153 (Composite)
  Minor opcode of failed request:  1 ()
  Serial number of failed request:  22
  Current serial number in output stream:  26

Then I suspected something related to Compiz must be to blame and after I disabled the desktop effects sketchUp started no pb.

The only problem is that it requests wine to install gecko but the download window that appears does nothing and another problem there is with the cursor, which is framed by a square white rectangleof about 40x40 pixels or so.

Any ideea on what should we do to make compiz work with sketchUp?

Thanks.

---

### Post by pejcaofrito on 2008-02-08
> **Epic Plecostomus said:**
> HOORAY!  IS FIXED!

Only one tiny annoying glitch-bug... my menu-bar and icons (in sketchup) go black, I can mouse over them to spot them but it's annoying.

HOWEVER!   At least the core function of the program is working.    *happy dance*

I'm having the same issue; Now for what I can see here, you guys seem to be using wine from other repositories than gutsy's (ATM wine is 0.9.46); So please, could you mind pointing me to the repo u r using? Does "that" wine works as gutsy's (that has "Applications"->"wine"->"etc" at the panel) ?

For general Info: I use standard repos, have a Nv 8800GTS 320, using proprietary Nv driver from restricted modules 100.14.19, winecfg stock (haven't messed around), and yes, OpenGL works like like a charm (compiz, games, etc. Even Half-life & CS & DoD via steam works @ 100%)

Thx.

---

### Post by sethtriggs on 2008-02-15
I'm having the same black menu issue as well with my Sketchup - I know I could just go ahead and start drawing but it's going to kill my workflow to not be able to see the menus right off the bat when drawing.

I'd love to see what it's looking for. Do you think this is an issue with the .NET framework? That is something that the Windows version has as a prerequisite, recall.

-Seth

---

### Post by sethtriggs on 2008-02-15
> **pejcaofrito said:**
> I'm having the same issue; Now for what I can see here, you guys seem to be using wine from other repositories than gutsy's (ATM wine is 0.9.46); So please, could you mind pointing me to the repo u r using? Does "that" wine works as gutsy's (that has "Applications"->"wine"->"etc" at the panel) ?

For general Info: I use standard repos, have a Nv 8800GTS 320, using proprietary Nv driver from restricted modules 100.14.19, winecfg stock (haven't messed around), and yes, OpenGL works like like a charm (compiz, games, etc. Even Half-life & CS & DoD via steam works @ 100%)

Thx.

I'm fairly sure mine came from a standard repository - but how do I tell for sure? Mine has the Applications-Wine -> tree too, and is version 0.9.46. I have a NVidia GEforce FX 5500 using a NVIDIA accelerated graphics card driver. (Restricted modules). My menu is turning black though. I didn't even do anything else with Winecfg.

How is yours working? Is it perhaps a better video card?

-Seth

---

### Post by bismark on 2008-03-21
I'm trying to get this to work on my Hardy x64 install /w fglrx ATI drivers and the wine 0.9.57 from the repository.

So far I can get the farthest when I disable DRI in my xorg.conf.  When I do this SketchUp starts but the drawing window has a black background and my cursor is a surrounded by a white block.

When I try to enable DRI it won't even load and gives me the ```
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

```

Any ideas?

---

### Post by dbsoundman on 2008-03-28
I just installed and had the OpenGL issue, so I modified the regedit thing from 0 to 1 as stated, and Sketchup now dies silently. What is it I need to do to make it work now? I saw something about compiz but I'm not familiar with that...

Thanks,
Dan

---

### Post by GrantF on 2008-04-16
I have confirmed this problem on Hardy-Heron (Ubuntu 8.04).
Some of the following information will be duplicated from prior posts, but I wanted to capture my entire timeline for any developers out there.

[LIST]
[*]I first installed & configured wine according to [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[*] To make sure the install was good, I launched the notepad program, and it runs just fine.
[*]Again, using the guidance from the wine-wiki, I installed Google Sketchup 6 (henceforth known as "GSU-6").
[*]I launched GSU-6 via wine and got the "missing OpenGL" pop-up error as described earlier.
[*]I applied the registry "tweak" for HW-OK as described in the root post of this thread and tried to launch GSU-6.  Now it just silently dies.
[*]Then I replaced my compiz window manager with metacity by executing this command in the terminal:
```
metacity --replace &
```
[*]I re-launced GSU-6 and it works just fine (although I now get the pop-up errors for Gecko).
[/LIST]
It seems to me that compiz is a very likely candidate for further investigation.
I would be happy to provide any information I can that would help people track down this problem.

Here are my system vitals:
[LIST]
[*]Ubuntu 8.04(alpha-6) on amd64
[*]nvidia GeForce 6600 GT (rev a2)
[/LIST]

---

### Post by bismark on 2008-04-17
> **GrantF said:**
> 
[*]Then I replaced my compiz window manager with metacity by executing this command in the terminal:
```
metacity --replace &
```
[*]I re-launced GSU-6 and it works just fine (although I now get the pop-up errors for Gecko).

I'm using Xubuntu so I'm using Xfce and not metacity so this doesn't work for me. :(

---

### Post by johnnybgood115 on 2008-05-08
I tried all the steps listed here from the registry edit to the metacity --replace  

However, now when I run GSU6 I no longer get the error, I simply see the program flash on the desktop then disappear.  I guess it loads then crashes right away? Any ideas or hints?

Thanks in advance!

---

### Post by briandu on 2008-05-21
I have this working on Hardy 64 with Nvidia 9600GT on a Q6600

What I did was:

[LIST=1]
[*] install Nvidia driver to version 173.1 (look in archives)
[*]ensure all system updates are installed
[*]install wine to latest version (it updated today)
[*]fresh install sketchup v6 from site
[*]disabled all special effects (system/prefs/appearance and visual effects tab -disable)
[*]have fun it works!
[*]oh yes, I then went back to enable all special effects (system/prefs/appearance and visual effects tab) and it still works - great! :popcorn:
[/LIST]

---

### Post by ethanthekiwi on 2008-05-27
When I first tried to run the program, which I installed using wine-doors, it would show an error saying that it needed openGl. I tried some of the above suggestions, and now the program will run but the screen is **black**. I can see all the menus and tool bars, but the work area is completely black.
I am using an Hp Compaq nx6325 laptop with ATI x700 graphics. I am running Ubuntu Hardy Heron.

---

### Post by nikkkko on 2008-06-09
Hi,

I just came to this on Friday and I thought I'd add in my 10 cents.  

Running 8.04 and Wine 1.0-rc4, (from the WineHQ repositories), and with both registry adjustments as earlier described, Sketchup runs fine, including menus and without the black screen problem.  

However, it runs so grindingly slowly as to make it completely unusable, I presume because there is no 3D acceleration.

lspci output for graphics controller: 

```
VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
```

OpenGL drivers are installed and working fine under Ubuntu, all visual effects are turned off.

So close and yet so far...

---

### Post by Crazy Buddhist on 2008-06-09
> **ethanthekiwi said:**
> When I first tried to run the program, which I installed using wine-doors, it would show an error saying that it needed openGl. I tried some of the above suggestions, and now the program will run but the screen is **black**. I can see all the menus and tool bars, but the work area is completely black.
I am using an Hp Compaq nx6325 laptop with ATI x700 graphics. I am running Ubuntu Hardy Heron.

There is a fix [here]("http://ubuntuforums.org/showthread.php?p=5116774#post5116774") for the people with ATI cards in their machines getting black screens. Basically once you get to the point of having a black screen you uninstall the drivers installed with EnvyNG and it all works.

May be a case of uninstall and reinstall the graphics card driver and it works. Not been tested further yet.

Crazy

---

### Post by naught101 on 2008-06-15
I'm having the same problem as described by ethanthekiwi - everything works fine, except the viewport is black (with red and white lines at the top, as if the resolution were wrong or something, see attachment)

The only major difference is that I'm using the intel driver (915 chipset), so none of the above solutions work for me. Perhaps this is just a problem with wine and the intel915: [http://bugs.winehq.org/show_bug.cgi?id=13305](http://bugs.winehq.org/show_bug.cgi?id=13305)

I'm running hardy kubuntu.

Anyway, I'd love to know if anyone finds a solution for the intel driver, I've tried looking, but haven't found anything that works yet.

---

### Post by naught101 on 2008-06-15
Just to confirm, I tried replacing kwin:
kwin --replace &
but nothing changed. On the off chance it might help, I also installed and tried this with metacity. No luck.

Does anyone know if framebuffer settings in xorg.conf might effact this?

---

### Post by tzedek on 2008-06-22
Tried this "fix", didnt work.  It did stop the gl error however.  Im using wine 1.0 which supposedly also fixes this issues.  Quite laughable IMO.

---

### Post by triplepoint on 2008-07-08
Ahoy,
 First of all, thanks for the work so far in this thread.  I managed to get Sketchup to at least accept input.  I'm using stock Ubuntu 8.04 with all updates, with the wine-hq repo delivering wine v1.1.

  I applied the first registry change (the HW_OK bit flip), and that got me as far as the startup window before it crashed.  I applied the second registry change (the SnappyInstructor bit flip) and that carried me into a 'usable' state.

  But any file load/save action crashes the program.  Has anyone else had this one?
- TP

  Edit: Hell I say that, but then just now I attempted to save a file in the default directory (the My Documents directory) and it worked.  Also, loading from Google's Components directory worked.  Hmm, chalk this one up as an intermittent error.  Still, has anyone seen this behavior and nailed it down?
 - TP

---

### Post by timswait on 2008-07-09
Sounds like my situation triplepoint. Installed Wine using "Add/Remove Applications", so I presume it's the latest. Installed SketchUp 6. Got the OpenGL error. Looked on here and found this thread so applied both Regedit fixes. It does now work, but it still crashes intermittently. I can't really use it as it just keeps crashing and loosing what I've done.
On a slightly unrelated issue is there any way to close a program that's not responding like Alt Cntl Del in windows and task manager? I tried sending the error report to Google after one of the crashes (politely suggesting they should release a Linux version ;) ) and the sending window froze sending the report. There was no close button on the window mso I ended up having to reboot my computer to get rid of it!

---

### Post by kid-pro-quo on 2008-07-09
I had the same problem with the bug-reporting window.

You can run xkill from the alt-f2 dialog box, then just click the dead window and it'll disappear.

---

### Post by C.S.Cameron on 2008-07-18
SU worked great right off on my son's computer with 8800 gt,
When I installed it on a thumbdrive running Umbuntu on my desktop with 8800gts I got the OGL thing.
changed the 0 to 1 and it launched with the black curser, then soon bug splat.
Launched it again and quickly went to window, Preferences,OpenGL, and changed to #9.
Everything seems to be working and stable now, including shadows, and animation, materials, etc.

---

### Post by timswait on 2008-07-18
What do you mean? I went to Window>Preferences>OpenGL but I only have two options, 1 and 2. They look the same except 1 doesn't have shadows. It crashed again while I was fiddling with these settings anyway!

---

### Post by C.S.Cameron on 2008-07-18
Try the one without shadows, (I still get shadows).
Try setting your setting to 2 and exiting before it can bug splat.
Hopefully it shoulg start up ok.
Are you getting a black box on your curser?

---

### Post by zenithdave on 2008-08-09
Thanks those first 2 registry tweaks and IT WORKS! :guitar:

---

### Post by zenithdave on 2008-08-09
Then it broke again after installing xserver-xgl

compizconfig-settings-manager :(

---

### Post by zenithdave on 2008-08-09
But! after enabling 'Proposed updates' in system/software/ sources/updates/proposed updates (Hardy proposed)lots of files were downloaded and sketchup works again :KS

Thanks.

Im finding it hard to crash now !

Thanks for all the work :D

---

### Post by dankegel on 2008-11-23
If you have any problem running Sketchup with current Ubuntu and Wine, please see [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup) for our page of tips.  And let us know if you find any new bugs, we'll try to fix them.
Thanks!
Dan Kegel (for the Wine project)

---

### Post by RavanH on 2008-11-24
> **dankegel said:**
> If you have any problem running Sketchup with current Ubuntu and Wine, please see [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup) for our page of tips.  And let us know if you find any new bugs, we'll try to fix them.
Thanks!
Dan Kegel (for the Wine project)

Dan, I installed Sketchup 7 under Wine 1.1.9 on a Ubuntu 8.10 AMD64 system. Running it, I get past the Welcome screen -- after unchecking "show at startup" and doing the regedit manipulation -- but then, sadly, it show a completely scrambled drawing area. The buttons and menu are fine, but the mouse pointer has a white square around it when hovering the drawing area. 
EDIT: I shold maybe mention I am using radeon open source drivers and have Desktop Effects (Compiz) enabled...

Any related fixes around ? Tnx !

---

### Post by paradroid on 2009-06-01
MaxVK, your solution worked fine !!! :popcorn:

> **MaxVK said:**
> Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1


---

### Post by MaxVK on 2009-06-02
Sweet! :D

Shame the same trick doesn't seem to work on Sketchup 7 and Jaunty!

---

### Post by Citizen_Kane01 on 2009-09-13
Stumbled across this by accident:

Sketchup 7
Wine 1.2
Karmic Alpha 5

Had the same openGL problem so I installed Firefox in Wine in an 'stab in the dark' attempt to auto-install drivers from the Intel site to wine. Needless to say, this did not work (the Intel bit that is, Firefox worked just fine)

Next time I started Sketchup 7 the openGL problem was gone and Sketchup seems to perform as well as under W*ndows, if not better! Seems as if Firefox somehow magically fixed openGL in Wine.

This may not work for you, but worth a try.

---

### Post by Flip_1974 on 2009-11-01
Wow! I just want to confirm that the fix described above works. I also had the issue with the black screen after running Sketchup in Wine. I installed Firefox for windows (flawless under Wine) and from that moment Sketchup works fine, black screen gone. 

Hurray!

---

### Post by pashaahsj on 2009-12-24
I just installed this using Crossfire Professional and used this technique !! worked like a charm !! awesome thanx !! =D
(btw i did not pay for the pro version, if you know what i mean)

---

### Post by juky on 2010-10-05
> **MaxVK said:**
> Iv seen quite a few posts that mention the problem with Sketchup 6, where it stops during loading and warns you that you do not have OpenGL available. I had this problem.

Fix:
Open your wine menu and open the C drive (/home/user/.Wine)
Open the Windows Folder
Find Regedit.exe and run it with Wine
Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1
Run Sketchup 6
No more error on startup and the program seems to run just fine on NVIDIA 6600, Ubuntu 7.10

Good luck

I have installed GoogleSketchup8 and used above instructions - everything works good now on my old FS E8010 Notebook with Intel graphics.

Cheers,
juky

---

### Post by RavanH on 2010-10-11
> **juky said:**
> I have installed GoogleSketchup8 and used above instructions - everything works good now on my old FS E8010 Notebook with Intel graphics.

Cheers,
juky

And where, may I ask, did you get GoogleSketchup version 8 ? ;)

---

### Post by greenman-23 on 2011-06-05
I followed the basic instructions here and installed wine 1.2 and then tried to install sketchup pro6 4.112 and got a non executable error message.... 

I solved this though by uninstalling wine 1.2 and installing the beta version which then installed sketch up fine.... 

I then uninstalled the beta version of wine and reinstalled 1.2 

perhaps a little complicated (I could have perhaps left the beta version installed?) but sketchup appears to work just fine... 

yet another nail into the coffin of windows........ 
MS-RIP (May Sh#! Rest In Peace)

---

