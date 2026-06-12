---
title: "Harmony 650 Remote will not communicate with Ubuntu"
date: 2013-11-21
forum: Wine
---

### Post by jlh68 on 2013-11-21
I have a Logitech Harmony 650 remote (TV,Audio,Cable box,etc) and I use the Harmony 7.7.0 software using WINE on my Ubuntu unit.  I get the software to work just perfectly with the following exception:  the remote and computer will not communticate.  I suspect that the software is "looking" for a COM port and the Linux ports are /dev/ttyS0 and so on.  The Harmony software even communicates via the Internet with the Logitech web site and saves my selections.  My current work around is to make selecions using Ubunu, then shut down, open Win7 and communicate from computer to remote.  Because of the compatability of every thing before the final step of haveing the computer and remote communicate, I believe there is a solution to making the whole process compatbe on Ubuntu.

My thoughts are, if I knew the software  programed COM port then I could assign COMx to one of my Linux ports (/dev/ttySx).  I do not know how to find out what the COM port number is, and I am not sure on how to assign a Linux port number once the COM port number is found.

Any solutions, comment?

---

