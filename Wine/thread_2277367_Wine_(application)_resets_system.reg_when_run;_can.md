---
title: "Wine (application?) resets system.reg when run; can't edit registry"
date: 2015-05-08
forum: Wine
---

### Post by sam-korson on 2015-05-08
Hello.  For the last several months or so, I've been working on trying to accomplish something that I thought would be rather simple to do:  change the command that Wine uses to open a certain file extension (.skp) with the associated program (Trimble SketchUp).  I couldn't find much or any info online about this, unfortunately, so I've been trying to figure things out myself for the past few hours today, and I might actually be getting somewhere at last.  This morning I found a thread that mentioned the program Alacarte, which I installed and tried to use to modify the command that opens .skp files.  It didn't work; apparently the command can't have any arguments added before or after the %f for the file to open.  I just need to add the /DisableRubyAPI argument so that the program doesn't freeze when I open a file with it.  I think I might need to change the command that the ProgIDOpen part runs for the SketchUp.Document ProgID.

I finally was able to find a registry entry that controls what command is used to open the .skp file extension with SketchUp.  The problem, apparently, was that the "SketchUp.Document" key is hidden in RegEdit, although it's visible in ~/.wine/system.reg when I open that with Gedit.  I was able to change that file in Gedit to have the following entry:

```
[HKEY_LOCAL_MACHINE\Software\Classes\SketchUp.Document\shell\open\command] 1431097523
@="C:\\PROG~FBU\\SketchUp\\SKET~1VA\\SketchUp.exe \"%1\" /DisableRubyAPI"

```

Unfortunately, while it was able to accomplish the desired result when I double-clicked a .skp file in the file manager, this only lasts for one use, and it seems that something (Wine or SketchUp) is resetting/reverting the modification I made after I exit SketchUp.  The same result occurs if I save the text above as a .reg file and use the command "wine regedit SketchUp.reg" to import it; it's back to the previous value once I exit SketchUp.

Can anyone help me by explaining why the registry change I'm trying to make keeps getting reverted, or provide a simpler way to add an argument to the command I use to open .skp files or any other type of file in Wine?  Thanks in advance.

---

