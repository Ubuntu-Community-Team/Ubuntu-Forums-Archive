---
title: "Wine and Silkypix"
date: 2012-09-03
forum: Wine
---

### Post by tubunter on 2012-09-03
Hello,

I need to run Silkypix raw converter software on Linux; so I installed wine and then, installed Silkypix on it. The installation ran fine, but the software didn't work well (images didn't display correctly); so I uninstalled wine, to re-install it and remake the whole process, but now, I'm not able to install Silkypix anymore...

what's happen?

Thanks

---

### Post by temetvince on 2012-09-03
Are you getting an error message of any sort?

---

### Post by tubunter on 2012-09-03
nothing...

just, launching setup.exe it seems work for a while, then it stops...
I'm not able to install any software on wine actually...

---

### Post by temetvince on 2012-09-03
That's odd. Are any settings different between your old wine install and your new install? Also, have you tried rebooting your computer?

You could try running windows explorer in wine. If that doesn't work, then you've got serious issues. If it does work, then you really can run stuff in wine, and you'll just need to tweak everything a bit.

---

### Post by tubunter on 2012-09-03
settings are the same. Also I tried up different windows versions, but nothing changes...

...windows explorer...or internet explorer?
If you mean the explorer as the "folders navigator", it runs fine, but I don't understand what I should "tweak"...

also I noticed that trying to run any installation file, the terminal window comes up just the time of a flash then disappears...

---

### Post by temetvince on 2012-09-03
Yes, windows explorer as in the folder navigator. Since that runs okay, it means your wine installation is capable of running windows programs. By tweaking, I just meant that since your wine is capable of running a program, it should be capable of running other programs if the settings are correct.

I'm assuming you've played around some in wine config. How are you launching things? You might try using the terminal exclusively for a bit.

It is possible that your old wine folders were left behind when you uninstalled wine. Assuming you haven't installed anything in wine that you don't mind erasing, you might try removing ~/.wine and then running wine config again.

---

### Post by tubunter on 2012-09-04
Ok. Found. If I launch the installation process by terminal, all work fine.

But Silkypix doesn't work properly. Images are bad.
Here there are some errors occurred during the installation process:

> user@user-L51RI1:~$ wine instmenu.exe
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
err:rpc:I_RpcGetBuffer no binding
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:ole:CoInitializeSecurity (0x411318,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceA ((null),"IDriverT"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IDriverT"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x83e9b8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x12cc30,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


---

### Post by nothingspecial on 2012-09-04
*Thread moved to **Wine**.*

---

