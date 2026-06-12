---
title: "Installing MS Office 2000 in Wine"
date: 2008-07-17
forum: Wine
---

### Post by oserdavid on 2008-07-17
I did search - but I cannot find an answer suitable for my level of newbieness... so apologies. I have good reasons for needing to run MS Office 2000 in Ubuntu 8.04 (believe me - and I know all about Openoffice).

But I couldn't get far with [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)

I've got to the point of having (partially) installed Office 2000 under the latest Wine. But I understand I need to copy riched20.dll and ole32.dll from my Windows/System32 directory (dual boot with Vista) into /home/david/.wine/drive_c/windows/system32

OK - I've now got them (pasted) onto my desktop. How, using terminal, do I get them into the directory named above? (Sorry - I did say I was a newbie!)

Maybe that is all that is needed - but I think, secondly, I need to "Change preferred owner in ~/.wine/system.reg" Likewise with "Organization".. doh... I can't find that directory - and I wouldn't know how to "Change preferred owner" in it (I suspect), even if I could - or maybe it'll be obvious, dunno.

And, finally, how do I get my license key for MS Office to 'stick'?

If I actually manage to install it properly (I understand it does work superbly with Ubuntu under Wine) - I suspect I will then come back in another thread and ask about installing the MS Office updates!! Grrr..

If all else fails, I may pay USD $29 and buy the Codeweavers solution - but it'd be nice to be able to avoid that - especially as I don't know that it won't still leave me with the same problems!

David

---

### Post by DGortze380 on 2008-07-17
> **oserdavid said:**
> I did search - but I cannot find an answer suitable for my level of newbieness... so apologies. I have good reasons for needing to run MS Office 2000 in Ubuntu 8.04 (believe me - and I know all about Openoffice).

But I couldn't get far with [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)

I've got to the point of having (partially) installed Office 2000 under the latest Wine. But I understand I need to copy riched20.dll and ole32.dll from my Windows/System32 directory (dual boot with Vista) into /home/david/.wine/drive_c/windows/system32

OK - I've now got them (pasted) onto my desktop. How, using terminal, do I get them into the directory named above? (Sorry - I did say I was a newbie!)

Maybe that is all that is needed - but I think, secondly, I need to "Change preferred owner in ~/.wine/system.reg" Likewise with "Organization".. doh... I can't find that directory - and I wouldn't know how to "Change preferred owner" in it (I suspect), even if I could - or maybe it'll be obvious, dunno.

And, finally, how do I get my license key for MS Office to 'stick'?

If I actually manage to install it properly (I understand it does work superbly with Ubuntu under Wine) - I suspect I will then come back in another thread and ask about installing the MS Office updates!! Grrr..

If all else fails, I may pay USD $29 and buy the Codeweavers solution - but it'd be nice to be able to avoid that - especially as I don't know that it won't still leave me with the same problems!

David

I gave up on wine, didn't seem worth the effort to me, I'll just dual boot... but to answer JUST your question.

To move file via command line use the mv command.
NOTE: Anything in <> needs to be replaced with specific information from your system.

```

mv /home/<username>/Desktop/<nameOfFile> /home/david/.wine/drive_c/windows/system32

```

---

### Post by oserdavid on 2008-07-18
Well - at least thanks for that DGortze380...

---

### Post by a1z on 2008-10-14
PART 1/3:

Installing Office 2K in Hardy is done with Wine v1.1.2.

1) install wine 1.1.2
2) extract office 2000 ISO (or zip or rar file)
3) install using setup.exe

====================
PART 2/3:

My question:

MS Word 2000 uses CPU all the time. My CPU meter on the task applet bar shows full usage of CPU when MS Word 2000 is opened and being used. The performance is smooth, nonetheless. When I minimize the window, the CPU relaxes.

What is going on? Is there a way to control the workload of CPU by MS Word 2000? Will this affect the performance of the word processor?

====================
PART 3/3:

SUMMARY:

I see this heavy usage of CPU under these conditions:

1) Hardy + Wine1.1.2 + Office 2000
2) Hardy + Wine1.1.2 + Office 2003
3) XP + Office 2000 (mentioned above)

But it is okay when I open and edit a document under these conditions:

1) XP + Office 2003
2) Hardy + Wine0.9.59 + Office 2003

Thanks in advance!

-a1z

---

