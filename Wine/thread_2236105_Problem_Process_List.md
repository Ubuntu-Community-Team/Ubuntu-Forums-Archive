---
title: "Problem Process List"
date: 2014-07-24
forum: Wine
---

### Post by M1k4 on 2014-07-24
Does somebody know why my programm is not in my process list please?

My programm is Diablo II expansion.
It should be "Game.exe" but I don't find it in my process list, why?

PS : I am not a very big player.
I just want like to understand and to train myself.

---

### Post by M1k4 on 2014-07-24
Hi Everybody
I am using Wine to play Diablo II

I found a software usefull called ISpy (used on close Battle.net), legit

I found this software there
[http://www.blizzhackers.cc/viewtopic.php?f=171&t=480193](http://www.blizzhackers.cc/viewtopic.php?f=171&t=480193)

I have a problem. 
I need to indicate to my software where is my Diablo II process named "Game.exe"
There is a list of process but my Game.exe process isn't in that list.
Impossible to write it manually, it doesn't work.

My process really exist.
I verified typing "sudo top"
I got this :

[[IMG]http://img11.hostingpics.net/thumbs/mini_683131Capturedu20140724225340.png[/IMG]](http://www.hostingpics.net/viewer.php?id=683131Capturedu20140724225340.png)

My process is really present.
I just cant find it using this process list from ISpy
My aim is to modify ISpy to make it able to find Game.exe process.


Using "resource hacker" I can read this in the file ISpy.dll

<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
    <security>
      <requestedPrivileges>
        <requestedExecutionLevel level="asInvoker" uiAccess="false"></requestedExecutionLevel>
      </requestedPrivileges>
    </security>
  </trustInfo>
</assembly>

I will now try to read ISpy.exe

I will update this topic.

Please help me if u can.

---

### Post by TheFu on 2014-07-24
Look for "wine", not game.exe.

Use 'ps -eaf|grep -i game' if that is what you want to search including the beginning of the argument list.

---

### Post by M1k4 on 2014-07-24
[[IMG]http://img4.hostingpics.net/thumbs/mini_435843processlist.png[/IMG]](http://www.hostingpics.net/viewer.php?id=435843processlist.png)

I tried all processes and it didnt work.

Still trying to disassemble this software.
objdump -D ISpy.exe

But all is in my terminal
How to get it on a file? :s

---

### Post by TheFu on 2014-07-24
Open a terminal - run the commands provided above.  That solves the first question - see the program in the process table, correct?

I cannot help disassemble commercial software or non-Linux software.

---

### Post by M1k4 on 2014-07-24
[[IMG]http://img4.hostingpics.net/thumbs/mini_478987commandrunned.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=478987commandrunned.png")

I don't find Game.exe in my process list.

---

