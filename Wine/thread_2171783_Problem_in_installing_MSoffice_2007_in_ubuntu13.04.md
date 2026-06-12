---
title: "Problem in installing MSoffice 2007 in ubuntu13.04 through wine"
date: 2013-09-01
forum: Wine
---

### Post by nns2006 on 2013-09-01
Hello,
I am trying to install msoffice 2007 on ubuntu 13.04 with wine version 1.6(added by ppa). Everytime following all the advice written in how-to's I reach at only one outcome-"Runtime error." and when I try to get more information from wine it doesn't respond-just empty window. 
Here is the terminal output for error (I pressume so).```
wine setup.exe 
wine: Unhandled exception 0x40000015 in thread 9 at address 0x7bc30073:0x30029af7 (thread 0009), starting debugger...
nityanand@Vostro-1500:/media/nityanand/OFFICE12$ Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001d    0
	0000001c    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001b    0
	00000018    0
	00000017    0
	00000013    0
00000019 plugplay.exe
	0000001f    0
	0000001e    0
	0000001a    0
00000020 explorer.exe
	00000022    0
	00000021    0
winedbg: Internal crash at 0x7ecfc5ea
```

Any advice/suggestions/guidance in installing is highly welcome.

thanks and regards

---

### Post by TheFu on 2013-09-01
The best advice I can give is to review the how-to over at **winehq.org**.  If that doesn't work, as the maintainer for help there.
Also, between attempts, be certain to mv or wipe the ~/.wine/ directory.

---

### Post by protoss96 on 2013-09-03
Why you dont install open office or just use already builded Libre Office? It supports MS office commands.  :/

---

### Post by TheFu on 2013-09-03
[http://www.howtogeek.com/171565/how-to-install-microsoft-office-on-linux/](http://www.howtogeek.com/171565/how-to-install-microsoft-office-on-linux/) was just published today. Might help.

80% of the time, there is no way to use LO or OO instead of MSO. Examples:
* working in a team with other companies using MSO (edits, notes, comparisons fail, fonts are different pagination is different - re-re-re-reformatting will kill everyone's productivity)
* when the output doc format is contractually required to be 100%, MSO files
* when there are OCX or other addons that are required for use, but only work in MSO
* when you need to embed Microsoft-only objects, files, into documents.  I've never gotten MS-Visio diagrams to embed into anything except MSO.

If you work alone - use whatever you like.
If you work in groups of people from small companies, use whatever the team decides.
If you work with a Fortune 50 company as the client, get over it, use MSO.

BTW, I use LO for everything that I can. I prefer the old-style menus - hate the ribbon bar.  When working with a team, the reasons able are why I suck it up and use MSO. Sometimes there is NO choice.

---

### Post by nns2006 on 2013-09-03
> protoss96
    Why you dont install open office or just use already builded Libre Office? It supports MS office commands. :/ 

I need it for MS presentaion which OO/LO lacks terribly.

> TheFu

   80% of the time, there is no way to use LO or OO instead of MSO. Examples:
* working in a team with other companies using MSO (edits, notes, comparisons fail, fonts are different pagination is different - re-re-re-reformatting will kill everyone's productivity)
* when the output doc format is contractually required to be 100%, MSO files
* when there are OCX or other addons that are required for use, but only work in MSO
* when you need to embed Microsoft-only objects, files, into documents. I've never gotten MS-Visio diagrams to embed into anything except MSO.


That is precisely the reasons why I want it running in wine. While I have also started to think of installing it in VMplayer with xp installed as I didn't see it runing well in wine for many.

---

