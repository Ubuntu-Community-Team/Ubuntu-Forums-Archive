---
title: "wine: cannot find L&quot;C:\\windows\\system32\\program.exe&quot;"
date: 2019-05-04
forum: Wine
---

### Post by hillwalker801 on 2019-05-04
Hi,

I'm a relative newcomer to Ubuntu and have 18.04 installed alongside Windows 7. With Windows 7 approaching it's end of life support I'm looking for alternatives to my Windows programs, but not finding any that do as good a job as Winamp so I'm trying to get Winamp 5.666 to run under WINE and installed WINE today. It appeared to complete successfully however, if I open the terminal and enter:

"wine --version" returns "wine-3.0 (Ubuntu 3.0-1ubuntu1)"

"winecfg" opens the WINE config and shows
C:                    ../drive_c
Z:                    /

"wine program" returns "wine: cannot find L"C:\\windows\\system32\\program.exe"

Using the files utility I can navigate to Home .wine drive_c windows system32 and confirm that program.exe is not listed.

I've tried uninstalling and purging WINE and reinstalling WINE. Nothing changes and "wine program" continues to return the same message.

Can anyone give me a clue as to what has gone wrong, or what I'm doing wrong?

Thanks in advance

---

### Post by thenailedone on 2019-05-04
Hi,

You are receiving the error due to you telling wine to run the program called "program" when you run "wine program" which clearly does not exist.

What you can try is to download the winamp installation file and then in the terminal go to the folder you downloaded the file and run "wine <nameofthefileyoudownloaded.exe>". This should launch the installer. If it installs successfully you should see winamp in your menu. If it works congratulations. 

There are alternative methods that can be used with wine that often set-up things required for specific applications so that you are more likely to have them work, one is Play on Linux, another is Lutris. They might make your wine experience a better one.

---

### Post by hillwalker801 on 2019-05-06
Many thanks for your reply, which clearly explained my error. I downloaded the Winamp 5.8 (beta) program and used your advice but it failed to install. Downloaded the previous version 5.666 and that installed without a problem. Went into the preferences and set the watch folder to my existing music folder and started a scan which ran to completion. Tested with a few tracks successfully and am now very happy. Thanks again.

I&#8217;m now looking forward to switching over to other Linux programs before Windows 7 disappears.

---

### Post by mastablasta on 2019-05-08
otherwise there are so many alternatives that run natively including a couple of Winamp clones:

Audacious
Rhythmbox
Clementine
Amarok
Cantata
DeadBeef
gmusicbrowser
Guayadeque
Quod Libet
MUSIQUE




**winamp clones:**
qmmp
xmms

---

### Post by thenailedone on 2019-05-09
> **hillwalker801 said:**
> Many thanks for your reply, which clearly explained my error. I downloaded the Winamp 5.8 (beta) program and used your advice but it failed to install. Downloaded the previous version 5.666 and that installed without a problem. Went into the preferences and set the watch folder to my existing music folder and started a scan which ran to completion. Tested with a few tracks successfully and am now very happy. Thanks again.

I’m now looking forward to switching over to other Linux programs before Windows 7 disappears.

You can mark the thread as [solved]("https://ubuntuforums.org/showthread.php?t=726150&p=4527051#post4527051").

My prefered music player is Clementine, even on Windows.

---

