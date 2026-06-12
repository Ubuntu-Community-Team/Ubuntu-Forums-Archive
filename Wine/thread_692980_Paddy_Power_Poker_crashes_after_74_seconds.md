---
title: "Paddy Power Poker crashes after 74 seconds"
date: 2008-02-10
forum: Wine
---

### Post by con on 2008-02-10
Hey there
I just installed the 0.9.54 version of wine from the 7.10 winehq repository to see if I can get Paddy Power Poker working.

The install went fine with everything seems to work, however the program crashes 74s after the program is executed regardless of what is being done with it, funnily enough its exactly 74s each time.

I've dual graphics on an Asus laptop and it crashes the same way with Nvidia 8400 and intel x3100 graphics.

I've attached the ouput from the terminal (running Nvidia graphics). 

I'm new to wine so none of it makes any sense to me but the first line is

err:advapi:service_control_dispatcher pipe connect failed

and the last lines are;

  29 0x03c3243f in gkparser (+0x1243f) (0x00000000)
fixme:shdocvw:WebBrowser_Stop (0x14d8e8)
err:ole:CoUninitialize Mismatched CoUninitialize
wine client error:9: write: Bad file descriptor

Thanks for any help.

---

