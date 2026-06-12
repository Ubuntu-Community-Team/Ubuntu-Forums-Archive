---
title: "can't reinstall WoW with Wine (Gutsy)"
date: 2008-04-03
forum: Wine
---

### Post by Mousekavich on 2008-04-03
So I recently began using Ubuntu.  I installed Wine, WoW, Guildwars, and began playing the aforementioned games.  All of a sudden, one day my WoW is corrupt (apparently).  So I tried repairing and it didn't work.  I figured I'd reinstall.

I couldn't figure out how to uninstall with Ubuntu or Wine so I just deleted /.wine/Program\ Files/World\ of\ Warcraft/ entirely.  Big mistake.

Now I cannot install WoW at all.  I've got two different sets of disks, both of which worked just fine about 2 weeks ago when I initially installed.  Please help!


I am working with wine v.0.9.58 which should be the most updated version.  Every time I try to install, no matter what I do, it gives me the following error message in the installer screen:

```
 The installer was unable to read the file "<unknown>". This error may be caused by problems with the media or drive at --for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the installer. (The data being read was "InstallCD\ExternalLinks\Support\Manual.pdf", and the error code was 38.) If this problem persists, please contact Blizzard Technical Support. (MPQFile::Read)
 The file "C:\Program Files\World of Warcraft\Data\base.MPQ" could not be found.
```

and then it cuts off - and I can't scroll to the side or copy and paste it to find out what it could be caused by.

Please help - I've been trying to fix this all day and part of yesterday.  If you need any info I'll probably be checking this post hourly for the next few days.

I get this error in the terminal:
```
anbailey@Zeus:~/Desktop/wow_install$ wine Installer.exe
anbailey@Zeus:~/Desktop/wow_install$ fixme:font:CreateScalableFontResourceW (1,L"C:\\windows\\temp\\Blizzard Installer Temp - 00000453\\FrizQuadrata.fot",L"C:\\windows\\temp\\Blizzard Installer Temp - 00000453\\FrizQuadrata.ttf",(null)): stub
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:richedit:IRichEditOle_fnGetClientSite stub 0x843290
fixme:ole:OleCreateStaticFromData (not shown), stub!
fixme:richedit:IRichEditOle_fnGetClientSite stub 0x843290
fixme:ole:OleCreateStaticFromData (not shown), stub!
```

---

### Post by YokoZar on 2008-04-04
Yeah, uninstalling by just deleting the folder will lead to problems, even on Windows.  I would have expected WoW to have a more robust installer that didn't crap out in that case, but oh well.

If you want to uninstall Windows applications in the future, go to Applications->Wine->Uninstall Wine Software

The easiest thing for you to do at this point is to just move (or delete) your ~/.wine folder and install WoW from scratch.  If you have other windows applications installed into Wine, though, you'd have to reinstall them.

---

### Post by Mousekavich on 2008-04-04
Thanks for the input, I really appreciate the quick response.  I didn't realize how simple it was to remove programs *sigh* oh well I guess.

Unfortunately, I've already tried deleting the /.wine folder.  Additionally I've also tried deleting anything related to wine in my /.local folder.  I've looked for every place I could find anything to do with WoW or Wine and removed it, this all after uninstalling.  None of this seemed to fix it.

Additionally I tried installing an older version of wine (0.9.57) at the recommendation of other posts on these forums.  Nothing seems to work.

I've got another hard drive that's mostly empty sitting around.  I'm going to do a clean install of Ubuntu on that with Wine and see if it fixes my problem :(  didn't wanna resort to that, but oh well.

---

### Post by YokoZar on 2008-04-04
> **Mousekavich said:**
> Thanks for the input, I really appreciate the quick response.  I didn't realize how simple it was to remove programs *sigh* oh well I guess.

Unfortunately, I've already tried deleting the /.wine folder.  Additionally I've also tried deleting anything related to wine in my /.local folder.  I've looked for every place I could find anything to do with WoW or Wine and removed it, this all after uninstalling.  None of this seemed to fix it.It's giving you the exact same error about base.MPQ not being found even after clearing ~/.wine?

---

### Post by Mousekavich on 2008-04-04
Yep, that seems to be the case.  I can't quite tell though because the error message has a tendency to run off in one line and not do word-wrap for me so I can't read more than a little bit. :(

---

### Post by Mousekavich on 2008-04-09
Okay, so I think I found the problem...After trying to reintall Ubuntu on 2 HDDs with 2 cd roms using 2 disk drives in various combinations and such, I began to get a little concerned.  What was going on?

I decided to run memtest86.  32,000 errors later I decided I have bad RAM.  New RAM should be arriving today.  Let's hope for the best.


Thanks for your help anyway.

---

