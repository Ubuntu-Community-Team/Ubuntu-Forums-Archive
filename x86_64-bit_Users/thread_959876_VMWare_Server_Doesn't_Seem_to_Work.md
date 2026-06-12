---
title: "VMWare Server Doesn't Seem to Work"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by wetling on 2008-10-26
I downloaded VMware-server-1.0.6-91891.tar.gz so I could run an instance of Windows on this Linux machine.  I unpacked it and the install seemed to work (I took all the defaults except the virtual machine location).  I've got an entry for VMWare Server Console under Applications -> System Tools. 

When I try to run it though, I get an button on the task bar that says, "Starting VMWare Server" which stays there for a few minutes and then goes away.  Nothing else seems to happen and I don't see any VMWare process running when I check the System Monitor.

Any thoughts on what's going on here?  Thanks.

---

### Post by mperry on 2008-10-26
Try running vmware in a console or terminal and see what comes out. Open a terminal and type vmware. There are a few issues which can happen on AMD64 and often running the command in a terminal window will let you see where things are failing.

---

### Post by wetling on 2008-10-26
When I run vmware from the terminal, I get back the following:

```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

```

---

### Post by wetling on 2008-10-26
I found this [thread](http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/5c2b99a203559783) but I have no idea what they're talking about :)

---

### Post by wetling on 2008-10-26
Well, looks like I posted too early.  I looked through this thread: [http://ubuntuforums.org/showthread.php?t=826626]("http://ubuntuforums.org/showthread.php?t=826626") and ran the commands.  Now VMWare loads.

---

### Post by digital_sabine on 2008-11-03
For me, the error was resolved by renaming 

/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

to 

/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.old

...As this doc noted 2 posts above ([http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/5c2b99a203559783?pli=1](http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/5c2b99a203559783?pli=1)) seems to indicate is the workaround.

(Now I'm getting permissions errors on the virtual machine files, but at least now it's a different error... right?)

---

### Post by wetling on 2008-11-04
I ended up reinstalling Ubuntu (and upgrading to 8.10).  I've installed VMware erver 2.  It is okay, but I don't think I like the web interface.

I think VirtualBox will do what need so I'm going to give that a try.

---

