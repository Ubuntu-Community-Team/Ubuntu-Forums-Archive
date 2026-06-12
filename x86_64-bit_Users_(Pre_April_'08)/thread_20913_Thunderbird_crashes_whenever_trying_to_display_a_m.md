---
title: "Thunderbird crashes whenever trying to display a mail"
date: 2005-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by beppo on 2005-03-19
Thunderbird starts up fine, connects to the mail account and receives new messages.
Whenever I try to view one of the messages (be it by clicking on them in the list in the upper part of the window or using the keyboard) thunderbird crashes without any error messages. I did not find any error message in /var/log/... either.
Unfortunately, the default of thunderbird seems to remove messages from the server, so that currently I cannot view any of my old messages. (I changed the setting NOW.)

Searching the internet has not revealed my clue; therefore any hint/help is very welcome.

Update: By running mozilla-thunderbird from a terminal with --debug option
that the problem seems to be in libenigmime.so

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 16384 (LWP 9071)]
0x0000002a9e4be62e in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libenigmime.so

Deinstalling the corresponding package 
  mozilla-thinderbird-enigmail
solved the orignal problem, however it seems then to be a bug in the package??
Sould I file a bug report??

---

