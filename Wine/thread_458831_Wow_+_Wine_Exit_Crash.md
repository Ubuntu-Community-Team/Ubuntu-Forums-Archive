---
title: "Wow + Wine Exit Crash"
date: 2007-05-30
forum: Wine
---

### Post by malura on 2007-05-30
Okay, so I've successfully managed to get World of Warcraft running on Ubuntu.....with just one problem. Whenever I click exit game, or leave game, or try to quit at all, the game completely freezes, forcing me to use System Monitor to forcibly kill the program. Is there any solution for this problem?

My Config.wtf reads as follows:

SET gxResolution "1024x768"
SET hwDetect "0"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET readScanning "-1"
SET realmName "Tanaris"
SET gameTip "55"
SET gxCursor "0"
SET SmallCull "0.040000"
SET frillDensity "32"
SET farclip "357"
SET Gamma "1.000000"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET gxColorBits "24"
SET gxApi "opengl"
SET statusBarText "1"
SET ffxDeath "0"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET readContest "-1"
SET minimapInsideZoom "5"
SET gxDepthBits "24"
SET accountName "Weeeeee!"
SET locale "enUS"
SET lastCharacterIndex "3"
SET patchlist "us.version.worldofwarcraft.com"

---

### Post by Dev0205 on 2007-05-30
Malura,

I ran into the same issue tonight as well "I just installed WoW via Wine". Here is some useful information I found at WoW Wiki [http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine") 

> WoW hangs on exit

As of the 2.1.0 patch, some users, mostly ATI and Intel, experience their WoW program hanging (being unable to do anything) when they exit the game. It seems that changing the sound driver from OSS to ALSA fixes this for most people. Simply type winecfg in a terminal, select the Audio tab, then select ALSA as your driver instead of OSS.

If it locks up on you just alt-tab out of the game and kill it with the process manager. Or if you launch WoW in a terminal you can kill it with ctrl-c. For those who don't like to end WoW process so brutally, you may follow these steps:

   1. /reloadui
   2. /logout
   3. click "Back" on characters page
   4. click "Quit" on logon page. 

[edit] 

Does any of this apply? I got stuck at an Error #121 and need to reload WoW before I can try it myself.

Cheers,
Dev :D

---

### Post by marcozs on 2007-05-30
I had the same problem since I installed the patch 2.1.0... I solved it erasing my addons directory and using only addons compatible with 2.1.0 and as well I made a fresh Config.wtf

---

### Post by malura on 2007-05-30
Same issue still occurring. I'm not sure really what I'm supposed to do with
1. /reloadui
2. /logout
3. click "Back" on characters page
4. click "Quit" on logon page. 

Also, Marco, how did you go about deleting your addons folder? How did you determine which addons were actually used by patch 2.1.0?

<UPDATE>
I've gone back into wine, and changed my windows version to 2000. This resolved the issue. Thanks all :)

---

### Post by Dev0205 on 2007-05-30
Good to hear! How's WoW running? I'm reinstalling as we speak.

---

### Post by HieroPosche on 2007-05-30
How did you change your windows version? I can't find where to do it.

---

### Post by Sammi on 2007-05-31
@[HieroPosche]("http://ubuntuforums.org/member.php?u=303573")
Write this in a terminal "winecfg" and press enter. It will launch a little Wine configuration application, that you'll probably figure out by yourself.

---

### Post by ShadowFlar3 on 2007-05-31
This was a server-side issue just after launch of patch 2.1.0 and everyone that had this problem reported that they no longer experienced it regarless on if they applied some fix or not. But you say you still get this?

---

### Post by Spinalcracker on 2007-06-01
*** FIXED ***

Navigate to the following file

internet.c

In the following directory

/home/YOUR_LOGIN_NAME_GOES_HERE/CVS/winex/dlls/wininet

Make a backup of the file, (just in case), and then open it with a text editor.

Go to the end and copy and paste everything below this line into it and save... Ta da!!! :)
---------------------------------------------------------------------------------------------------------------------------

Index: internet.c
===================================================================
RCS file: /var/lib/cvsd/cvsroot/winex/dlls/wininet/internet.c,v
retrieving revision 1.21
retrieving revision 1.22
diff -u -d -r1.21 -r1.22
--- internet.c 25 May 2007 21:47:16 -0000 1.21
+++ internet.c 25 May 2007 21:47:23 -0000 1.22
@@ -1383,12 +1383,15 @@
BOOL retval = FALSE;
int nSocket = -1;
LPWININETHANDLEHEADER lpwh = (LPWININETHANDLEHEADER) hFile;
+ LPWININETAPPINFOA hIC = NULL;

TRACE("%p %p %ld %ld\n", hFile, lpBuffersOut, dwFlags, dwContext);

if (NULL == lpwh)
return FALSE;

+ hIC = (LPWININETAPPINFOA) lpwh->lpwhparent;
+
/* FIXME: this should use NETCON functions! */
switch (lpwh->htype)
{
@@ -1422,6 +1425,15 @@
break;
}

+ /* hack for WoW; whenever we do a partial read, it waits for another RESPONSE_RECEIVED.
+ * We should probably send one when we actually receive data on the socket, but
+ * that's not possible right now without a major rewrite of the netcon stuff. */
+ if (retval && lpBuffersOut->dwBufferLength) {
+ DWORD len = 0;
+ TRACE("firing callback\n");
+ SendAsyncCallback(lpwh, hIC, lpwh, dwContext, INTERNET_STATUS_RESPONSE_RECEIVED, &len, sizeof(len));
+ }
+
TRACE("-- %s (bytes read: %ld)\n", retval ? "TRUE": "FALSE", lpBuffersOut->dwBufferLength);
return retval;
}
@@ -1442,12 +1454,15 @@
BOOL retval = FALSE;
int nSocket = -1;
LPWININETHANDLEHEADER lpwh = (LPWININETHANDLEHEADER) hFile;
+ LPWININETAPPINFOA hIC = NULL;

TRACE("%p %p %ld %ld\n", hFile, lpBuffersOut, dwFlags, dwContext);

if (NULL == lpwh)
return FALSE;

+ hIC = (LPWININETAPPINFOA) lpwh->lpwhparent;
+
/* FIXME: this should use NETCON functions! */
switch (lpwh->htype)
{
@@ -1482,6 +1497,15 @@
break;
}

+ /* hack for WoW; whenever we do a partial read, it waits for another RESPONSE_RECEIVED.
+ * We should probably send one when we actually receive data on the socket, but
+ * that's not possible right now without a major rewrite of the netcon stuff. */
+ if (retval && lpBuffersOut->dwBufferLength) {
+ DWORD len = 0;
+ TRACE("firing callback\n");
+ SendAsyncCallback(lpwh, hIC, lpwh, dwContext, INTERNET_STATUS_RESPONSE_RECEIVED, &len, sizeof(len));
+ }
+
TRACE("-- %s (bytes read: %ld)\n", retval ? "TRUE": "FALSE", lpBuffersOut->dwBufferLength);
return retval;
}

---

### Post by Hayabusarider on 2007-09-16
Can anyone confirm this works?

---

### Post by Spinalcracker on 2007-09-17
This was working up till the last mini patch.  Since then a patched version of Wine is necessary.

So.... Here is how to fix wine so it no longer hangs on quit.

Open a terminal and past in the following code and hit enter

```
sudo dpkg --purge wine
```

Enter your password and hit enter.  Wait for all the crap to go.  If it asks yes or no say Yes, but it shouldn't even ask.  Once the uninstall is done and you are back to a command prompt, close the terminal.

Download the following file.  

[**Click here --> Patched Wine Installation File <-- Click here**](http://files.filefront.com/wine+0944winehq0ubuntu76deb/;8575938;/fileinfo.html)

Once downloaded double-click the file to begin the installer.  Once finished, start the game and you are good to go.  No more hanging on quit  :lol:

NOTE:  Ubuntu may want to auto update to the unpatched version of wine.  You will have to ignore this until wine releases an official patched version that has populated the repositories.

NOTE:  This patch also for me fixed the hanging when changing in game video settings under openGL.  Please check this out as well, but  the hang on quit is confirmed by multiple people.

---

### Post by gurkburk on 2007-09-25
I cannot get the above file to work, and im having this EXACT problem myself, very annoying since I cant save any information and thus not setup my UI or keybinds..

I cannot use regular GDebi Package Installer, I get an errormessage complaining about either corrupt package or permissions settings, and I have set read/write & execute permissions on this file.

Also tried using terminal with
> sudo dpkg -i wine_0.9.44winehq0ubuntu76.deb
Which gave these error-messages:
> Selecting previously deselected package wine.
(Reading database ... 108729 files and directories currently installed.)
Unpacking wine (from wine_0.9.44winehq0ubuntu76.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.44winehq0ubuntu76.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/dsound.dll.so')
Errors were encountered while processing:
 wine_0.9.44winehq0ubuntu76.deb


I have no idea what it all means.. but I cant get this "version" of wine installed, the one I had before which is the regular auto-updated one, works fine though, appart from the wow-error ofcourse.

---

### Post by Seraed on 2007-09-25
> **gurkburk said:**
> I cannot get the above file to work, and im having this EXACT problem myself, very annoying since I cant save any information and thus not setup my UI or keybinds..

I cannot use regular GDebi Package Installer, I get an errormessage complaining about either corrupt package or permissions settings, and I have set read/write & execute permissions on this file.

Also tried using terminal with

Which gave these error-messages:


I have no idea what it all means.. but I cant get this "version" of wine installed, the one I had before which is the regular auto-updated one, works fine though, appart from the wow-error ofcourse.

I actually rolled back to 0.9.43 from 0.9.45 because of this problem. Works fine for me... though we will see after today's patch.

---

### Post by sk8dork on 2007-09-25
downgrading to 9.43 fixed the hang on exit bug for me. also, i don't know when it happened, but hardware cursor in d3d mode works beautifully (in both 9.43 and 9.45)

---

### Post by Nussi on 2010-01-11
This thread is almost three years old. Still. I have found it by google employing pretty straight foward search terms when I was trying to figure out why World of Warcraft crashed for me every time I shut down the client. Thus, I deem my reply justified.

A possible reason nowadays why one's client might crash on exit is using the D3D-engine instead of the OpenGL one. Add "-opengl" to the end of your wine-line, like this:
```
wine "D:\Games\World of warcraft\Wow.exe" -opengl
```
Most people do this for various reasons, and I did it before, too. I just didn't realize immediately what was going on and started to hunt for solutions at the wrong spots.

---

