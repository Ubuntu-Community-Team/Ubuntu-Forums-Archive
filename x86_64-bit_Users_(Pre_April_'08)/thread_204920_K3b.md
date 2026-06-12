---
title: "K3b"
date: 2006-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by vincentb on 2006-06-27
All,

I have installed Linux ubuntu.borreux.be 2.6.15-25-amd64-generic #1 SMP PREEMPT Wed Jun 14 11:28:03 UTC 2006 x86_64 GNU/Linux on my PC.

Then I have installed K3B 0.12.14

My CD / DVD drive is a Plextor DVD R PX 750 A. 

When I try to duplicate an audio CD, it first read the source one, then asked to put a empty CD in the burner. I receive a message 'no media found' in a pop-up window. In this window, I have several options : 1 button for 'Load', 'Eject', 'Force' and 'Cancel'. But once I put the empty CD in the burner, it seems the system never detects this new CD. It waits and waits and ... ends with an error message (trumpet ...)

Any idea to help me?

Thanks in advance,

Vincent

---

### Post by Lil_Eagle on 2006-06-28
Are you putting the CD in the driver before you choose Load?

---

### Post by Kilz on 2006-06-28
[QUOTE=vincentb]All,

I have installed Linux ubuntu.borreux.be 2.6.15-25-amd64-generic #1 SMP PREEMPT Wed Jun 14 11:28:03 UTC 2006 x86_64 GNU/Linux on my PC.

Then I have installed K3B 0.12.14

My CD / DVD drive is a Plextor DVD R PX 750 A. 

When I try to duplicate an audio CD, it first read the source one, then asked to put a empty CD in the burner. I receive a message 'no media found' in a pop-up window. In this window, I have several options : 1 button for 'Load', 'Eject', 'Force' and 'Cancel'. But once I put the empty CD in the burner, it seems the system never detects this new CD. It waits and waits and ... ends with an error message (trumpet ...)

Any idea to help me?

Thanks in advance,

Vincent[/QUOTE]

Do you have one or 2 cd/dvd drives?

---

### Post by vincentb on 2006-06-29
All,

I have only one CD- DVD reader/writer.
When I try to duplicate the CD, it first reads the whole CD, then ejects it asking to put an empty CD. 

It looks like it is not able to write on it (does not find it or does not detect it).
I have a similar problem when trying to burn an audio CD from OGG file. When trying to start the burning, it 'hangs' apparently.

Thanks in advance for your help.

Vincent

---

### Post by Lil_Eagle on 2006-06-29
In my experience K3B detects the CD/DVD drive flawlessly, but perhaps there is something wrong in the configuration.

It could be related to permissions.  If your account doesn't have write access to the cdrom, and k3b is using cdrao, then cdrao needs to have write permission to /dev/cdrom0.  Normally things are already configured this way, so you don't have a problem, but you could check.

It could also be a hardware problem, it could be specific to K3B.  Can you burn CD's with other operating systems on the same compuer?  Have you tried another program such as gnomebaker?

I'm afraid you'll just have to keep testing.  Trial and error is the best method of learning. ;)

---

### Post by vincentb on 2006-07-06
I have installed Ubuntu 6.06 (32 bits) and everything seems ok now. I also burn CD by activating the 'TOA' option (not sure I really understand what it means) and have experienced no more problems since then ...

---

### Post by Kilz on 2006-07-06
[QUOTE=vincentb]I have installed Ubuntu 6.06 (32 bits) and everything seems ok now. I also burn CD by activating the 'TOA' option (not sure I really understand what it means) and have experienced no more problems since then ...[/QUOTE]
I think you should file a bug report. that way it will get fixed.

---

