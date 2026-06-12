---
title: "Gnome not booting"
date: 2006-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by TimeForBears on 2006-07-02
Hello,

On a fresh install of 64 bit 6.06, I get this problem:

I am able to enter username and password on the login screen, then the background changes (this is a fresh install, so it's a marroon colour), and the mouse pointer appears, but nothing else.

I have no errors in the logs, and I get the same problem when I boot from live CD - it 'stops' in the same place - but the mouse pointer appears, and I can move it around - ie the system has not hung.

Failsafe mode does not work, and failsafe terminal works, (ie I  get the terminal, but the desktop still doesnt load.)

I am installing this on a Tyan K8WE board with two C0 stepping 248 opterons. I want to take advantage of NUMA if possible, but this is just an installation thing - the only things I've added to the install, are nvidia-glx (to see if nvidia drivers fix the problem) and changed xorg.conf accordingly.

The problem exists whether the nvidia-glx module is installed or not.

If anyone could tell me what I need to do, I'd be very obliged. I've spent a whole day on this.... with no luck.

I don't want to revert to 5.10, but if I can't get dapper working, it's either that or XP....

Thanks very much

TimeForBears

---

### Post by simonn on 2006-07-02
I suspect this is something to do with permissions on the users home directory or /tmp.

Make sure that the user has write permissions to these directories.

---

### Post by TimeForBears on 2006-07-03
Simonn,

You sir, are a complete star.

It was indeed write perms on the home directory.

I'm wondering why I got this problem on a fresh install though, and if it is a problem which needs addressing?

I don't much care though, since I've got dapper back... cheers!

TimeForBears

---

