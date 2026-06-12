---
title: "Microsoft Chat &quot;Comic Chat&quot; in WINE Installation &amp; Display Issues"
date: 2018-01-28
forum: Wine
---

### Post by oarion72 on 2018-01-28
Been trying to figure this out on sporadic occasions over the last ten+ years. As opposed to my previous attempts on older versions of wine, I can run the install executable mschat25.exe and click OK/yes to install, then the installation program appears to get interrupted. Nonetheless, the "Microsoft Chat" directory is successfully created under Program Files.

The newly generated "C:\Program Files\Microsoft Chat" directory contains two files which do not appear to exist in the equivalent installation folder on my virtual Windows XP system. These are "chatmig.dll" and "icchat.tlb."

I am able to successfully launch the installed "CChat.exe" from Program Files, and everything looks and works fine except that comic panes do not generate correctly at all: there are large black shapes in place of legible chat balloons and comic pane frames. 

What it looks like:
 [IMG]http://i35.tinypic.com/jku4pk.jpg[/IMG]

What it should look like:

[IMG]http://kurlander.net/DJ/Projects/ComicChat/FromVWG.jpg[/IMG]

When **[FONT=fixedsys]wine start "C:\Program Files\Microsoft Chat\CChat.exe[/FONT]** is executed from the Linux terminal, the following output is generated:

```
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Microsoft Chat\\icchat.tlb" failed with error 1006
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:imm:ImmReleaseContext (0x10110, 0x17eb78): stub
fixme:storage:create_storagefile Storage share mode not implemented.
```

It would seem to me that, perhaps, if I could get the installer to work correctly, then that may resolve these issues. I have riched20, MS .Net framework 2.0, and IE6 installed via winetricks.

When running the installation executable (mschat25.exe), which as I mentioned seems to get interrupted but does generate the Program Files directory, I get the following output in the terminal:

```
~/.wine/drive_c>wine start mschat25.exe 
fixme:exec:SHELL_execute flags ignored: 0x00000100
~/.wine/drive_c>fixme:advpack:set_ldids Need to support changing paths - default will be used
```

After that point, the installation hangs indefinitely without anything in the GUI and I have to run a ^C to regain control of the terminal.

Also, if I launch the working version Chat program in my virtual Windows XP box, and run "tasklist /m" while it's running, I get the following output:

```
CChat.exe                    748 ntdll.dll, kernel32.dll, ADVAPI32.dll,       
                                 RPCRT4.dll, Secur32.dll, GDI32.dll,          
                                 USER32.dll, COMCTL32.dll, ole32.dll,         
                                 msvcrt.dll, OLEAUT32.dll, WSOCK32.dll,       
                                 WS2_32.dll, WS2HELP.dll, SHELL32.dll,        
                                 SHLWAPI.dll, WINMM.dll, IMM32.dll,           
                                 WINSPOOL.DRV, comdlg32.dll, oledlg.dll,      
                                 comctl32.dll, MSCTF.dll, msctfime.ime,       
                                 RICHED32.DLL, RICHED20.dll, MSRATING.DLL,    
                                 WININET.dll, Normaliz.dll, urlmon.dll,       
                                 iertutil.dll, unidrvui.dll, VERSION.dll,     
                                 xpsp2res.dll  
```

If I cross check these files with a list of all system files in the equivalent wine installation, the following system files from the above list do not exist anywhere ~/.wine:

WS2HELP.dll
msctfime.ime
iertutil.dll
unidrvui.dll
xpsp2res.dll

Interesting that iertutil.dll does not exist in wine installation, as that is why I installed IE6 to begin with.

Any tips?

Old thread from 2008, didn't get much feedback:
[https://ubuntuforums.org/showthread.php?t=859463](https://ubuntuforums.org/showthread.php?t=859463)

I figure 9 years down the road is long enough I can revive the thread, as I still haven't found a solution and now have this "tlb" file error and dll list to compare. Sometime around Julian Assange's talk show on RT I maintained a blog for a while documenting how to imitate Microsoft Chat using a combination of shell scripts and weechat plugins, with the hopes that an actual developer might take up the project, but it was too time consuming for me to continue.

Thanks for any advice anyone may have :)

---

### Post by oarion72 on 2018-01-29
I upgraded to wine 3.0, removed ~/.wine, then created new win32 prefix. I installed riched20 and ie6 via winetricks. riched20 is necessary or the space bar won't work. I installed mschat25.exe. I tried "wine start CChat.exe" which failed, but "wine CChat.exe" worked as in the past. I'll admit my ignorance and look up the difference between wine and wine start. To my surprise, comic panes loaded correctly. I was able to connect no problem to the one server still dedicated to Comic Chat users. I believe if you try to use other servers, not only will you annoy other users by sending them comic data, but you might crash when joining a room. My version of wine was about 4 years old. Upgrading to wine 3.0 was a great success. After having been tinkering with this for 10 years, I guess I failed to seriously entertain that upgrading wine would resolve the issue. I'll be writing up some documentation soon and spreading it around, as every once in a great while there's a few nostalgic people who spring up curious about this program.

Screenshot: [http://i63.tinypic.com/2vajwok.jpg](http://i63.tinypic.com/2vajwok.jpg)

Marking solved. Cheers!

---

