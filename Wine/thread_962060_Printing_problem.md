---
title: "Printing problem"
date: 2008-10-28
forum: Wine
---

### Post by mike_mango on 2008-10-28
Hi,

First of all, I'm completely new to Ubuntu (Linux in general).  In fact I have only been using it for a few days.

I have installed Wine with the intent to use a program called "Cashflow Manager GST".  Within the AppDB it indicates that support is unknown, however I have it all completely working except for one part - printing.

I can print from any other application in Ubuntu and I can print from Notepad using Wine, however whenever I try and print with Cashflow I get this message:

"Operation not supported on selected printer"

I have tried both the built-in PDF printer and also the printer that I have setup (a Samsung SCX-4216F).  As I said above, this printer prints perfectly with everything else.

I did a search and someone else came across this problem but it doesn't indicate whether or not it had been solved and now.  Besides, being a total newbie from the Windows world, most of what was being discussed was over my head.

This started as a project to move my mother over and this is the last hurdle.  Everything else she uses either works perfectly or I found an alternative for her.

I installed the latest version of Wine - didn't help.

Any help would be greatly appreciated.

Oh, system details: Ubuntu 8.04 x86, Samsung SCX-4216F, umm... I don't know what other specs to give you.

Cheers,
Mike

---

### Post by asdfoo on 2008-10-28
> **mike_mango said:**
> Hi,

First of all, I'm completely new to Ubuntu (Linux in general).  In fact I have only been using it for a few days.

I have installed Wine with the intent to use a program called "Cashflow Manager GST".  Within the AppDB it indicates that support is unknown, however I have it all completely working except for one part - printing.

I can print from any other application in Ubuntu and I can print from Notepad using Wine, however whenever I try and print with Cashflow I get this message:

"Operation not supported on selected printer"

I have tried both the built-in PDF printer and also the printer that I have setup (a Samsung SCX-4216F).  As I said above, this printer prints perfectly with everything else.

I did a search and someone else came across this problem but it doesn't indicate whether or not it had been solved and now.  Besides, being a total newbie from the Windows world, most of what was being discussed was over my head.

This started as a project to move my mother over and this is the last hurdle.  Everything else she uses either works perfectly or I found an alternative for her.

I installed the latest version of Wine - didn't help.

Any help would be greatly appreciated.

Oh, system details: Ubuntu 8.04 x86, Samsung SCX-4216F, umm... I don't know what other specs to give you.

Cheers,
Mike

can you try running the program from the terminal to see if there is any informational messages?

eg. 

cd .wine/drive_c/cash_flow/
wine cashflow.exe

then paste the output here?

---

### Post by mike_mango on 2008-10-28
> **asdfoo said:**
> can you try running the program from the terminal to see if there is any informational messages?

eg. 

cd .wine/drive_c/cash_flow/
wine cashflow.exe

then paste the output here?

After doing the above, I got the following messages from terminal:

ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
fixme:toolhelp:InterruptRegister16 (0000, 0x11df00ba), stub.

Does this help?

---

### Post by asdfoo on 2008-10-29
> **mike_mango said:**
> After doing the above, I got the following messages from terminal:

ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
fixme:toolhelp:InterruptRegister16 (0000, 0x11df00ba), stub.

Does this help?

Searching the winehq bugzilla for your exact error message yields this bug [http://bugs.winehq.org/show_bug.cgi?id=12231](http://bugs.winehq.org/show_bug.cgi?id=12231)

I would register an account there and add a comment saying that you receive the same message when attempting to print with Cashflow Manager GST, preventing you from printing anything.

---

### Post by mike_mango on 2008-10-29
> **asdfoo said:**
> Searching the winehq bugzilla for your exact error message yields this bug [http://bugs.winehq.org/show_bug.cgi?id=12231](http://bugs.winehq.org/show_bug.cgi?id=12231)

I would register an account there and add a comment saying that you receive the same message when attempting to print with Cashflow Manager GST, preventing you from printing anything.

Thanks for the advice.  Will do so now.

---

