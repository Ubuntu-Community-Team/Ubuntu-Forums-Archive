---
title: "Check if wine program freezes, crashes"
date: 2008-11-14
forum: Wine
---

### Post by iljabrander on 2008-11-14
Goodevening all readers, 

I use Ubuntu 8.10 Server. I use vnc4server to connect remote to a GUI. I am using this GUI to start a wine program (wich is not availible as Linux software) this is used to be a dedicated server. This program is called Battlefield 1942 multiplayer demo. 
Everything works fine. But after some time the game crashes or the game server freezes. Everytime with different errors. And different time.

Now my question is, is there a way to check that wine is crashing or freezing? If, then kill the process and restart it?

Thanks in advance

Ilja

---

### Post by cogadh on 2008-11-14
You can't kill and re-start Wine without also killing whatever Wine is running. The Windows app you are running is dependent on the wineserver process, so if you were expecting to be able to "refresh" Wine and keep on playing wherever you left off, that won't work.

As for checking to see what Wine is doing at the time of the crash, if you run the game through the terminal, Wine will output its error messages to the terminal and you should be able to see what happened (from Wine's perspective).

---

### Post by iljabrander on 2008-11-14
I am only running one wine app at the same time and it is no problem that the server will be offline for a few seconds but i will check the output of the command line as soon as it crashes again.

tnx

---

### Post by cogadh on 2008-11-14
I think you might have misunderstood. The "wineserver" is the name of the process that Wine runs a windows app within. Without it, whatever app Wine is running will simply cease to exist, so it cannot possibly be stopped and restarted without also killing whatever Windows app you are running, even if it is only one app.

---

### Post by iljabrander on 2008-11-14
i dont mind that it will terminate all wine apps it does not make my system instable or?

---

### Post by cogadh on 2008-11-14
No, it won't make your system unstable at all. I just didn't want you to think you could "wake up" Wine by restarting the process. Maybe I misunderstood.

Anyway, to kill the running Wine process, you just need to open a terminal and run "wineserver -k".

---

### Post by iljabrander on 2008-11-14
Ok thanks but i have to trigger a script when it freezs/crashs how to to that

---

### Post by iljabrander on 2008-11-15
Oke it was freezing again with this output:

```

found key:Joystick_IDButton29
found key:Joystick_IDButton30
found key:Joystick_IDButton31
found key:Demo_Wake
found key:Demo_Wake
found key:IDKey_OEM_102
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
err:seh:setup_exception_record stack overflow 1172 bytes in thread 001a eip 7bc78bc86 esp 00240e9c stack 0x240000-0x241000-0x340000
^C
root@server:/home/root# fixme:event:wait_for_withdrawn_state window 0x10022/a00009 wait timed out

```

---

### Post by iljabrander on 2008-11-16
someone?

---

### Post by iljabrander on 2008-11-22
I think noone can help me...

---

### Post by jhenager on 2008-12-04
I can say that 'wineserver -k' had no effect on my runaway wine process. It is taking up 100% of one of my processors, and I can't run IES4Linux until I restart.

---

### Post by jhenager on 2008-12-04
If this helps, I was able to stop the runaway process with kill -9 6451 (which was the current PID of the process).
Type "top" in a terminal to get the PID of your processor hogging wineserver process. Substitute that PID number for 6451 and you should see your CPU heave a big sigh of relief, and lay down for a quick rest.

---

### Post by chiques on 2009-01-24
<System><Administration><System Monitor>

---

