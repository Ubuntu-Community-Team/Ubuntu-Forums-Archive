---
title: "[SOLVED] Missing Text? - Steam under WINE"
date: 2008-06-21
forum: Wine
---

### Post by greyfox1 on 2008-06-21
Hi, I can't seem to find any solution to this problem.  I'm running the latest version of WINE and just installed Steam.  See attachment for what I see when I try to start Steam.  In addition, I get the following output when I run Steam from Terminal:
```

fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
```

I searched for that error and I did find [this thread]("http://ubuntuforums.org/showthread.php?t=409286"), but the solutions mentioned there didn't help.  I'm confused about that because according to [this post]("http://ubuntuforums.org/showpost.php?p=2459203&postcount=17"), this problem was fixed upstream over a year ago.  

Here is what I've tried:

-Install the Tahoma font to ~/.wine/drive_c/windows/fonts/
-Substitute the Tahoma font for another font by editing ~/.wine/system.reg
-Uninstall/reinstall Steam
-Reinstall WINE
-Manually install/reinstall the xrender headers

I haven't completely removed WINE at any point, although I made a fresh install of Hardy shortly after release, so my original WINE installation isn't very old.


So, I'm at a loss.  Any help would be greatly appreciated.

---

### Post by cogadh on 2008-06-21
Wine now includes its own version of the Tahoma font and you no longer need to add one. By making changes to that, you may have screwed it up. I recommend you completely uninstall Wine, delete your "fake Windows" directory, then reinstall Wine and create a new "fake Windows" directory:
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

BTW - When you do update to a new version of Wine, you need to run "wineboot -u" to update your "fake Windows" directory with any changes made from the previous version. If you didn't do that, it may explain what happened, though I have never heard of that causing such a specific font problem.

---

### Post by greyfox1 on 2008-06-21
Thanks for the reply.  I followed your recommendations, but no luck. I know I did successfully remove the entire ~/.wine directory (I checked before I reinstalled) so even with a clean installation, I'm stuck.  One thing I forgot the first time around is that I do see text when I launch the program after the initial installation (see attached) but again, after this, I'm back to EXACTLY the same situation pictured in my original post.  Pls help!

---

### Post by |{urse on 2008-06-21
nvm forum blindness

---

### Post by greyfox1 on 2008-06-22
bump

---

### Post by Fred_E _krugar on 2008-06-24
I guess my only question at this point is which steam install did ya use the .msi or the .exe ??

---

### Post by greyfox1 on 2008-06-24
Good point-- I should have mentioned.  I'm using the latest msi installer.

---

### Post by Fred_E _krugar on 2008-06-24
After you installed steam did you do a wineboot??

---

### Post by greyfox1 on 2008-06-24
TBH I'm not quite sure if I did a wineboot since I removed WINE and reinstalled, but here's what I got when I did it just now:

```
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/rick/.wine' has been updated.
rick@rick-desktop:~$ fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:ViewObject_SetAdvise (0x1f0770)->(1 00000002 0x1132330)
fixme:shdocvw:PersistStreamInit_InitNew (0x1f0770)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1f0770)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1f0770)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1f1410)->(1 00000002 0x1132370)
fixme:shdocvw:PersistStreamInit_InitNew (0x1f1410)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1f1410)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1f1410)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,0,2): stub!
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,233,2): stub!
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time


```

...at which point the Steam window opens (again appearing just as in my original post).  When I close the Steam window, I get this:

```
err:ole:RevokeDragDrop invalid hwnd 0x20030
err:ole:RevokeDragDrop invalid hwnd 0x2002c
err:ole:RevokeDragDrop invalid hwnd 0x10036
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1f0770)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1f0770)
fixme:shdocvw:OleObject_Close (0x1f0770)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1f1410)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1f1410)
fixme:shdocvw:OleObject_Close (0x1f1410)->(1)
```

---

### Post by greyfox1 on 2008-06-25
Some more info: the full Terminal output that I get currently is below.  It appears to have changed a bit (more errors?) since my original post, but the Steam window looks exactly the same.

```
$ env WINEPREFIX="/home/rick/.wine" wine "C:\Program Files\Steam\Steam.exe"
CellID: Fetching server list from CSDS. . .
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 169 servers.
CellID: Connecting to 150.101.120.97:27031. . .
CellID: Connect to 150.101.120.97:27031 took 264 MS
CellID: New Best!
CellID: Connecting to 87.248.208.117:27031. . .
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
CellID: Connect to 87.248.208.117:27031 took 143 MS
CellID: New Best!
fixme:shdocvw:ViewObject_SetAdvise (0x1f0e60)->(1 00000002 0x1132328)
fixme:shdocvw:PersistStreamInit_InitNew (0x1f0e60)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1f0e60)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1f0e60)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1f1b00)->(1 00000002 0x1132368)
fixme:shdocvw:PersistStreamInit_InitNew (0x1f1b00)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1f1b00)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1f1b00)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,0,2): stub!
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
CellID: Connecting to 213.202.254.141:27031. . .
CellID: Connect to 213.202.254.141:27031 took 220 MS
CellID: Connecting to 80.160.78.27:27031. . .
CellID: Connect to 80.160.78.27:27031 took 150 MS
CellID: Connecting to 83.141.55.2:27031. . .
CellID: Connect to 83.141.55.2:27031 took 149 MS
CellID: Connecting to 87.248.196.197:27031. . .
CellID: Connect to 87.248.196.197:27031 took 164 MS
CellID: Connecting to 69.28.151.29:27031. . .
CellID: Connect to 69.28.151.29:27031 took 95 MS
CellID: New Best!
CellID: Connecting to 68.142.119.11:27031. . .
CellID: Connect to 68.142.119.11:27031 took 80 MS
CellID: New Best!
CellID: Connecting to 195.13.60.2:27031. . .
CellID: Connect to 195.13.60.2:27031 took 165 MS
CellID: Connecting to 68.142.72.253:27031. . .
CellID: Connect to 68.142.72.253:27031 took 44 MS
CellID: New Best!
CellID: Connecting to 58.120.225.167:27031. . .
CellID: Connect to 58.120.225.167:27031 took 251 MS
CellID: Connecting to 79.141.167.4:27031. . .
CellID: Connect to 79.141.167.4:27031 took 179 MS
CellID: Connecting to 69.28.153.108:27031. . .
CellID: Connect to 69.28.153.108:27031 took 60 MS
CellID: Connecting to 116.193.88.76:27031. . .
CellID: timeout connecting to 116.193.88.76:27031
CellID: Connecting to 193.34.49.3:27031. . .
CellID: Connect to 193.34.49.3:27031 took 155 MS
CellID: Connecting to 79.141.162.2:27031. . .
CellID: Connect to 79.141.162.2:27031 took 141 MS
CellID: Connecting to 87.248.209.212:27031. . .
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
CellID: timeout connecting to 87.248.209.212:27031
CellID: Connecting to 72.165.61.151:27031. . .
CellID: Connect to 72.165.61.151:27031 took 110 MS
CellID: Connecting to 69.28.151.27:27031. . .
CellID: Connect to 69.28.151.27:27031 took 96 MS
CellID: Connecting to 87.248.196.114:27031. . .
CellID: Connect to 87.248.196.114:27031 took 139 MS
CellID: Connecting to 87.248.196.118:27031. . .
CellID: Connect to 87.248.196.118:27031 took 140 MS
CellID: Connecting to 195.56.146.154:27031. . .
CellID: Connect to 195.56.146.154:27031 took 156 MS
CellID: Connecting to 69.28.145.81:27031. . .
CellID: Connect to 69.28.145.81:27031 took 141 MS
CellID: Connecting to 69.28.151.28:27031. . .
CellID: Connect to 69.28.151.28:27031 took 134 MS
CellID: Connecting to 193.34.50.7:27031. . .
CellID: Connect to 193.34.50.7:27031 took 130 MS
CellID: Connecting to 213.246.38.252:27031. . .
CellID: Connect to 213.246.38.252:27031 took 130 MS
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
CellID: Connecting to 202.190.75.100:27031. . .
CellID: Connect to 202.190.75.100:27031 took 307 MS
CellID: Connecting to 203.77.185.3:27031. . .
CellID: Connect to 203.77.185.3:27031 took 224 MS
CellID: Connecting to 208.111.140.6:27031. . .
CellID: Connect to 208.111.140.6:27031 took 91 MS
CellID: Connecting to 68.142.72.251:27031. . .
CellID: Connect to 68.142.72.251:27031 took 44 MS
CellID: Connecting to 222.233.53.27:27031. . .
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:ntdll:RtlpWaitForCriticalSection section 0x302ad11c "?" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x302ad11c "?" wait timed out in thread 001e, blocked by 0009, retrying (60 sec)

```


...And that's as far as it got before I closed Steam. I'd really like to be killing headcrabs right about now!!

---

### Post by greyfox1 on 2008-06-25
Bah, accidental double post.

---

### Post by hydroxph on 2008-06-25
just download the tahoma font and put it into your font folder for wine!

---

### Post by cogadh on 2008-06-26
I think you have bigger problems than just the lack of a font. It looks like you are using a self-compiled version of Wine and you are missing some of the required dev libraries that are needed for a fully functional version of Wine (all those "fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time" errors). If you do have a bad compile, you either need to recompile it with all of the required libraries or just install the precompiled Ubuntu package from the WineHQ repository: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by greyfox1 on 2008-06-30
Yeah see, that's the weird thing: I didn't compile myself.  I used apt-get to install.  I even completely purged WINE and re-installed per your instructions in your original reply but still got the same result.

I did all of it again just now (purged WINE, deleted ~./wine/, reinstalled, ran winecfg, installed STEAM) and STILL get the same results as previously reported.  Why me, o gaming gods, WHY?!?!

---

### Post by greyfox1 on 2008-06-30
I did some clicking around in the interface and got to this screen.  Is the text in the EULA supposed to look this horrid?  WINE IE displays similarly poorly rendered text too.

---

### Post by YokoZar on 2008-07-01
> **greyfox1 said:**
> Yeah see, that's the weird thing: I didn't compile myself.  I used apt-get to install.  I even completely purged WINE and re-installed per your instructions in your original reply but still got the same result.

I did all of it again just now (purged WINE, deleted ~./wine/, reinstalled, ran winecfg, installed STEAM) and STILL get the same results as previously reported.  Why me, o gaming gods, WHY?!?!
None of those commands would have removed a self-compiled wine if you ran sudo make install

type `which wine` into a console to see where the Wine binary that's actually running is located.  I'll bet 5 dollars you have something in /usr/local

---

### Post by cogadh on 2008-07-01
> **YokoZar said:**
> None of those commands would have removed a self-compiled wine if you ran sudo make install

type `which wine` into a console to see where the Wine binary that's actually running is located.  I'll bet 5 dollars you have something in /usr/local
My thoughts exactly. You must have used a self-compiled version at some time and it is still installed somewhere. When you try running Wine, even though you have installed the packaged version, the old self-compiled version is running instead. You could try specifying which version to use when you install Steam and I'd bet $10 you would get very different results:
```
/usr/bin/wine msiexec /i SteamInstall.msi
```

---

### Post by greyfox1 on 2008-07-01
...why do I get the feeling you guys are acting standoffish?  No need to bet me ten bucks, because I'm not arguing with you.

After this problem originally came up but before I started this thread, I did compile from source after reading an old thread.  However I didn't know purging wouldn't remove it (yah so sue me, I goofed), so I didn't mention it because I thought I had trashed that installation already.  Ugh!

But again, I had this problem before I compiled (at least the way the Steam window appeared, not sure about the missing xrender headers part).  I have *always* used apt-get to install WINE in the past.

Anyway, I got rid of the related files in /usr/local/bin/ then ran Steam again and voila, eenie meenie miney moe, it worked.  So I guess I owe you guys a big fat THANKS (but no 5 or 10 bucks, I'm cheap!)  I'll be off shooting things in no time!

---

### Post by redradish on 2008-10-13
Hmm, glad that worked for you. For anyone else with this problem, it doesn't seem like much of a wine problem at all (at least not mine), because on my ubuntu laptop it all worked perfectly through wine, but when I installed it on a fresh windows xp I had exactly the same mentioned problem with not having any text displayed on the steam install window. Grr, no idea how that works!! Retarded

---

