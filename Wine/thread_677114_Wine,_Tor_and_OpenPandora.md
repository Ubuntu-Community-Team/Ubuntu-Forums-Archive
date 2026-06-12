---
title: "Wine, Tor and OpenPandora"
date: 2008-01-24
forum: Wine
---

### Post by eMuNiX on 2008-01-24
I am trying to install [OpenPandora](http://openpandora.googlepages.com/) under linux using wine emulation.  I have the program installed in Windows at work and have been happily streaming Pandora radio all day.  I now fancy the challenge of getting it to run under wine.  Thusfar I have installed IE6, not wholly necessary but probably simplest.  Then I installed [Tor](http://openpandora.blogspot.com/2007/06/complete-guide-for-using-openpandora.html) and gave it the list of servers from the link and that runs okay.  I then installed mono to cover .NET and finally OpenPandora.  But when I run the .exe I get an error :- "fixme:win:EnumDisplayDevicesW ((null),0,0x61e3c4,0x00000000), stub!" and it fails.  Any thoughts or assistance?

---

### Post by chiefofthejojos on 2008-02-04
Hey dude.  I struggled to compile OpenPandora in MonoDevelop for a couple days.  But then I found something much better:
[http://www.screenlets.org/index.php/Pandora](http://www.screenlets.org/index.php/Pandora)
A pandora screenlet.  Coupled with compiz widgets, it's a dream.  I hope you enjoy it as much as I do.

---

### Post by DouglasAWh on 2008-02-04
> **eMuNiX said:**
> I am trying to install [OpenPandora](http://openpandora.googlepages.com/) under linux using wine emulation.  I have the program installed in Windows at work and have been happily streaming Pandora radio all day.  I now fancy the challenge of getting it to run under wine.  Thusfar I have installed IE6, not wholly necessary but probably simplest.  Then I installed [Tor](http://openpandora.blogspot.com/2007/06/complete-guide-for-using-openpandora.html) and gave it the list of servers from the link and that runs okay.  I then installed mono to cover .NET and finally OpenPandora.  But when I run the .exe I get an error :- "fixme:win:EnumDisplayDevicesW ((null),0,0x61e3c4,0x00000000), stub!" and it fails.  Any thoughts or assistance?

This is the greatest thing to come to Windoze since Evolution!...oh, wait, I can't get Evolution to work...

---

### Post by DouglasAWh on 2008-02-04
> **chiefofthejojos said:**
> Hey dude.  I struggled to compile OpenPandora in MonoDevelop for a couple days.  But then I found something much better:
[http://www.screenlets.org/index.php/Pandora](http://www.screenlets.org/index.php/Pandora)
A pandora screenlet.  Coupled with compiz widgets, it's a dream.  I hope you enjoy it as much as I do.

The screenlet doesn't submit to Last.fm though, does it?  OpenPandora does...or is supposed to.  I haven't gotten it to work yet.

EDIT: Nor does it work with the media keys, like OpenPandora does.

---

### Post by chiefofthejojos on 2008-02-04
Well then, I will share what I discovered in my struggles with MonoDevelop.  I do believe OpenPandora is portable to Mono, although it may be a lot of work.  OpenPandora in an embedded IE window in the Form, which is not available to Mono.  There is some recent development in Mono, however which may be used instead.  Mono.Mozilla is in Mono subversion and it can be used to not only embed Mozilla like gtkmozembed, but also access and make changes to the DOM like OpenPandora does.  The OpenPandora Visual Studio solution opens fine with MonoDevelop, so it's just a matter of getting rid of compile errors by replacing Windows specific code with code which will work with Linux.  I started doing so, but I got stuck when I didn't know how to setup event callbacks for Mono.Browser.  Being so new, the documentation is still sort of lacking.  Anyway, if someone wants to try this, I will provide as much support as I can.

---

