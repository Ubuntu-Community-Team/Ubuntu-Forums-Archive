---
title: "Open Office Locking Up"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by llanitedave on 2006-07-11
I've been getting several bugs in Open Office lately:  specifically documents in the Draw and Word Processor modules.

I have Kubuntu installed on both my AMD64 desktop, and on a PPC iBook -- and ONLY the AMD64 version is giving me problems.  I've been able to move documents to the iBook for now, but that's not always going to be a solution.

My first clue was when Open Office failed to load at all.  For a few days, I could get it to open from the document icon, but not from the KDE menu or the panel.  As of yesterday, even the document wasn't working.

I used Adept to delete all of the Open Office modules, and then re-downloaded and installed.  After that, it would load and open, and I could work on documents, but as soon as I tried to save them, the application would lock up.  It didn't matter whether I used the "Save" icon, the menu choice, or the "Save As" option.  Locking up means I couldn't do anything else to the window, not move it, edit it, or close it.  It seemed to be dragging the rest of the system down a certain extent as well.

After forcing it to quit through logging out, on logging back in again it immediately reopened and went to "restore" the applications that hadn't saved.  After restoring them, the same thing happened.  I couldn't save them.  The only way to get Open Office itself to quit was to close the open document without saving it.  At that point, I was back to the original problem, where it wouldn't open at all -- the hourglass icon and the label and the jumping OOo icon would appear, bob for a while, and then disappear.

I've since gotten it to work if I only install three modules:  the write, draw, and spreadsheet modules.  Once I installed the formula module, it all started locking up again.  So I THINK it might be in that section of the program.  However, it might have been just a matter of the number of uses I put it to before it crashed.  I plan to experiment more with it when I have time.

Should I put in a bug report with OOo?  Is this something anyone else has encountered?  Could there be a corrupted file remaining even after I removed Open Office from my local installation?

Any ideas are welcome!

---

### Post by Kilz on 2006-07-11
> **llanitedave said:**
> I've been getting several bugs in Open Office lately:  specifically documents in the Draw and Word Processor modules.

I have Kubuntu installed on both my AMD64 desktop, and on a PPC iBook -- and ONLY the AMD64 version is giving me problems.  I've been able to move documents to the iBook for now, but that's not always going to be a solution.

My first clue was when Open Office failed to load at all.  For a few days, I could get it to open from the document icon, but not from the KDE menu or the panel.  As of yesterday, even the document wasn't working.

I used Adept to delete all of the Open Office modules, and then re-downloaded and installed.  After that, it would load and open, and I could work on documents, but as soon as I tried to save them, the application would lock up.  It didn't matter whether I used the "Save" icon, the menu choice, or the "Save As" option.  Locking up means I couldn't do anything else to the window, not move it, edit it, or close it.  It seemed to be dragging the rest of the system down a certain extent as well.

After forcing it to quit through logging out, on logging back in again it immediately reopened and went to "restore" the applications that hadn't saved.  After restoring them, the same thing happened.  I couldn't save them.  The only way to get Open Office itself to quit was to close the open document without saving it.  At that point, I was back to the original problem, where it wouldn't open at all -- the hourglass icon and the label and the jumping OOo icon would appear, bob for a while, and then disappear.

I've since gotten it to work if I only install three modules:  the write, draw, and spreadsheet modules.  Once I installed the formula module, it all started locking up again.  So I THINK it might be in that section of the program.  However, it might have been just a matter of the number of uses I put it to before it crashed.  I plan to experiment more with it when I have time.

Should I put in a bug report with OOo?  Is this something anyone else has encountered?  Could there be a corrupted file remaining even after I removed Open Office from my local installation?

Any ideas are welcome!

You could try and remove them again, then use this command to remove the settings directory in your home folder. Replace <username> with your username.
```
sudo rm -rfd /home/<username>/.openoffice.org2
```
Then reinstall.
You could also try KOffice since you use Kubuntu it would probably be a better fit for the os.

---

### Post by llanitedave on 2006-07-11
Thanks for the idea, Kilz.  I'll try that this evening.  KOffice, unfortunately, is not an alternative because it can't read .odg files.  I tried that trick last night, using both kwrite and karbon14, and my documents simply didn't parse.

---

### Post by llanitedave on 2006-07-11
Well, I went beyond the advice.  I searched my system and deleted every reference to openoffice I could find, some 330 of them.  Then I re-installed the whole thing from scratch.

Still doesn't work.  The icon appears in my system menu, but the application simply won't load.  I get the bouncing cursor for about 30 seconds, but the splash box never appears, and then the application simply quits.

---

### Post by Kilz on 2006-07-12
> **llanitedave said:**
> Well, I went beyond the advice.  I searched my system and deleted every reference to openoffice I could find, some 330 of them.  Then I re-installed the whole thing from scratch.

Still doesn't work.  The icon appears in my system menu, but the application simply won't load.  I get the bouncing cursor for about 30 seconds, but the splash box never appears, and then the application simply quits.
That may have been to much. There are some things that were added to make OO run on the 64bit os, its a 32bit application.

---

### Post by llanitedave on 2006-07-12
Shouldn't those things have been re-downloaded when I reinstalled from scratch?

---

### Post by thebasti on 2006-07-12
> **llanitedave said:**
> I could work on documents, but as soon as I tried to save them, the application would lock up.  It didn't matter whether I used the "Save" icon, the menu choice, or the "Save As" option.  Locking up means I couldn't do anything else to the window, not move it, edit it, or close it.  It seemed to be dragging the rest of the system down a certain extent as well.

I have the similar problem with OO, but on Ubuntu (i.e. I am using gnome). I have random freezes when I try to save files in all OO applications. Sometimes it saves the file without problem, but sometimes it freezes.

That it self wouldn't be such a problem, but it also freezes keyboard and mouse, so there's nothing I can do except hit the reset button.

Does the same happens to you?

---

### Post by llanitedave on 2006-07-12
That hasn't quite happened, although it seems that way as long as the OpenOffice document has focus.  I can use the mouse, but no keyboard commands seem to respond.  However, I can use the panel to select another application, and that one will work fine.  If I close it, the part that's covered by the OOo window won't refresh, and I'll see the data from the closed application outlined by the OpenOffice document window!

---

### Post by Jonnycat26 on 2006-07-12
When openoffice freezes, is it using a lot of CPU?  Next time it happens, check in Top and see if it's frozen, or sucking down a lot of CPU.  If it's using a lot of CPU, it's a problem I've seen before and there is a fix.

---

### Post by sarolite on 2006-07-15
I get the same problem, splash screen, then nothing. If I try to open it from command line rather than icon, it tells me this:

> Gtk-Message: Failed to load module "gail": libgail.so: cannot open shared object  file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libspi.so.0: cannot open shared  object file: No such file or directory


Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c51f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c83f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8dd]
[0xffffe500]
/lib32/libc.so.6(vsscanf+0x6d)[0x564f507d]
/lib32/libc.so.6(sscanf+0x2b)[0x564efe7b]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(_Z13InitAtkBridgev+0x35)[0x59 301fdd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(create_SalInstance+0x19d)[0x5 9300341]
/usr/lib/openoffice/program/libvcl680li.so[0x55791369]
/usr/lib/openoffice/program/libvcl680li.so[0x5579146a]
/usr/lib/openoffice/program/libvcl680li.so(_Z7InitVCLRKN3com3sun4star3uno9Refere nceINS1_4lang20XMultiServiceFactoryEEE+0xb7)[0x555f4ad3]
/usr/lib/openoffice/program/libvcl680li.so[0x555f4c31]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0x555f4cf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib32/libc.so.6(__libc_start_main+0xd2)[0x564b2ea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x3 1)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233:  5661 Aborted                 "$s d_prog/$sd_binary" "$@"

** (process:5648): WARNING **: Unknown error forking main binary / abnormal earl y exit ...


---

### Post by llanitedave on 2006-07-19
I'm going to have to try that tonight -- been away from home for a few days and couldn't follow up on it.

Might there be libraries that I need to find and install?

---

### Post by llanitedave on 2006-07-20
Seems to be working fine now.  I went to the package manager, and it showed a number of updates needed for my OpenOffice installation -- seems pretty much every file needed to be updated.  I downloaded and installed the updates, and suddenly an error message that I thought I'd taken care of weeks ago popped up.  It claimed that there were changes it couldn't commit.  I'll have to chase that one down again.

Anyway, when I went to open OpenOffice, it all locked up again.  After I rebooted, however, it seems to be working.  

We'll see how well and how long:  I'm not ready to declare victory yet!

---

