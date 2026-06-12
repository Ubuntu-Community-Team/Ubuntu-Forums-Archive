---
title: "Error in Ubuntu 14.04 MS Office"
date: 2017-03-26
forum: Wine
---

### Post by Jayanth_Krishnamoo on 2017-03-26
Ubuntu 14.04:-
Hi everyone,
I am facing a problem with the following:
I had installed wine and POL (Play-on-linux) using the below commands-
1. sudo apt-get install wine
2. sudo apt-get install playonlinux
3. sudo apt-get upgrade
After installing the above, I installed MS Office 2007 from my USB drive. On my USB drive, I had selected the "exe" file and installed. Yet, whenever I launched the office program, I had trouble opening and saving word documents. So, I thought I will install Q4Wine and go with it. Hence, I decided to uninstall wine and POL. I went to 'system' and uninstalled wine. Yet, the MS-Office is there in the system and when I type word, in the 'search' files option, 'Microsoft Word' shows up. The problem is when it opens, it gives an error.
I would like to uninstall MS Office and download Q4Wine & install MS Office.
P.S.:- Kindly note, I am new to ubuntu and please provide me a step by step guidance of how to go about rectifying this condition. Any help will be sincerely appreciated.

K.N.Jayanth Krishnamoorthy.

---

### Post by Geoffrey_Arndt on 2017-03-26
I am not an expert on Wine/Play-on-Linux etc. although I did help someone install it so they could use a Windows only genealogy program.   It worked, but it was awkard . . . so . . . have you tried to open those MS Office documnets using the latest LibreOffice?    There is a good possibility it will open the files perfectly or with only very minor adjustments needed.    Then the completed file can be saved again in a MS Office format . . . or PDF . . . or native LibreOffice.   Unless the Office documents are EXTREMELY complex, the conversion process works very well . . . .

---

### Post by deadflowr on 2017-03-26
Thread moved to ***Wine **sub-forum*

In order to remove the entries produced by wine programs from the menu delete the desktop file, which should be located in ~/.local/share/applications.
Also to fully remove wine programs and settings after you have removed wine, delete the wine folder at ~/.wine.

(Both the .local and .wine folders are hidden, so to see them in the Files program you need to press *ctrl +h *to enable the view hidden folders and files setting.)

---

