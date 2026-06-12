---
title: "[SOLVED] Another 64-bit libgtk-1.2.so.0 problem"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by Mystere on 2008-11-18
I've searched fairly extensively through the forums and found several people with the same problem, but not a solution that worked for me (There were several dead links where solutions looked to be found, also) I'm trying to run Epsxe after installing it, and it consistently gives me the output
```
/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
I'm running 64-bit Kubuntu (Studio) 8.04 and have libgtk1.2 and libgtk1.2-common installed. I can find libgtk-1.2.so.0 in usr/lib64 but I don't know how to copy/paste it to lib32 or to make epsxe realize it's there. I've tried copying it, but it copies some sort of dead link (it claimed to be 3.4 mbs in lib64, and becomes 0 bytes in lib32) I'm a gui enthusiast, so the simpler the explanation the better. Thanks in advance!

---

### Post by Kilz on 2008-11-18
> **Mystere said:**
> I've searched fairly extensively through the forums and found several people with the same problem, but not a solution that worked for me (There were several dead links where solutions looked to be found, also) I'm trying to run Epsxe after installing it, and it consistently gives me the output
```
/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
I'm running 64-bit Kubuntu (Studio) 8.04 and have libgtk1.2 and libgtk1.2-common installed. I can find libgtk-1.2.so.0 in usr/lib64 but I don't know how to copy/paste it to lib32 or to make epsxe realize it's there. I've tried copying it, but it copies some sort of dead link (it claimed to be 3.4 mbs in lib64, and becomes 0 bytes in lib32) I'm a gui enthusiast, so the simpler the explanation the better. Thanks in advance!

Ok, here's what I think has gone on. You installed an application from someplace on the internet. Thats ok, but what you have to know when you do that is if its 32 or 64bit. Both will install.
32bit applications will even run , if you have the correct 32bit libraries installed. The first clue you gave that this may be the case is thinking and seeing the library in place, even trying to copy it to /lib32. But you cant. Its still a 64bit library, you need a 32bit library.
Thats where [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") comes into play, its the solution. It will get and install 32bit libraries with a few simple commands.

---

### Post by Mystere on 2008-11-18
Ah, thank you very much for the prompt response. I feel really dumb for glossing over that program when I was looking for solutions since I didn't understand exactly what it was. I got that set up and installed the two libraries I needed and it works fine, thanks!:popcorn:

---

