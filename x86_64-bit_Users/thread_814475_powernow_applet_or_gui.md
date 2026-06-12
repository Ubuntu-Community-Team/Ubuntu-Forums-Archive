---
title: "powernow applet or gui?"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by khosra on 2008-05-31
Hello.

Is there a gui to control the driver for the cpu frequency management? I have a dual opteron machine with powernow. Seems like the frequency governor is ondemand. It would be nice if there was a gnome applet to change that to performance, for example.

I vaguely remember there was such a thing when I had gentoo running on this machine, but I haven't been able to find the applet in ubuntu.

Was wondering if anyone can point me to it or suggest some other way of doing this than cat'ing to files in /sys/devices/system/cpu.

Thanks.

---

### Post by khosra on 2008-05-31
Sorry. Should have searched forums.

I was able to do it using the applet after:

sudo dpkg-reconfigure gnome-applets

and answering 'y' to the one option

It's very useful.

---

