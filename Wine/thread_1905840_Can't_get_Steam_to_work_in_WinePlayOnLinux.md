---
title: "Can't get Steam to work in Wine/PlayOnLinux"
date: 2012-01-07
forum: Wine
---

### Post by djbon2112 on 2012-01-07
I've got a fresh Kubuntu 11.10, and I've installed PlayOnLinux to get Steam. However I get the following errors:

When I start Steam, it's:

>  fixme: process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  9308
  Current serial number in output stream:  9308



And if I try to use winetricks to install allfonts (a possible solution acording to the WineHQ), I get:

> 
winetricks corefonts allfonts tahoma gecko gecko-dbg 
Executing w_do_call corefonts
corefonts already installed, skipping
Executing w_do_call allfonts
Executing load_allfonts
Executing w_do_call baekmuk
baekmuk already installed, skipping
Executing w_do_call corefonts
corefonts already installed, skipping
Executing w_do_call droid
Executing load_droid
Executing mkdir -p /home/joshua/.cache/winetricks/droid

...

------------------------------------------------------
sha1sum mismatch!  Rename /home/joshua/.cache/winetricks/droid/DroidSans-Bold.ttf and try again.
------------------------------------------------------


I'm getting frustrated with this, and I can't seem to find anything on the internet that works.

---

### Post by oldos2er on 2012-01-08
Moved to Wine.

---

### Post by djbon2112 on 2012-01-11
This issue seems to have spontaniously resolved itself; I don't know what I did but Steam now works. Marked as solved.

---

