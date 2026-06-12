---
title: "Ubuntu 14.04, Wine and Sketchup - 'transparent' SU screen"
date: 2014-05-08
forum: Wine
---

### Post by RayArdia on 2014-05-08
Sketchup loads and opens ok, to the initial screen but as soon as I select 'Start using Sketchup' the sketchup framework appears but seems to be semi-transparent, you can see other applications (eg Thunderbird) 'through' the SU screen.
Of course both SU and the application 'behind' it are unuseable. Only recourse it to close SU.
Can I use Terminal in some way to find out what is going on?

---

### Post by a3277426 on 2014-05-08
Hello, 
found a workaround which works for me.
start sketchup with this command:
wine "C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"

source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063](http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063)

---

### Post by RayArdia on 2014-05-09
> **a3277426 said:**
> Hello, 
found a workaround which works for me.
start sketchup with this command:
wine "C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"

source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063](http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063)

Thanks, this didn't work for me 

ray@ray-Aspire-5735:/$ C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI
bash: syntax error near unexpected token `('


and can't access my C: directory in Terminal to check path. Also having problems getting to the source file.

---

### Post by Mark Phelps on 2014-05-09
The C:\Program Files has to be contained inside quote marks because there is a blank between Program and Files. Plus, it has to start with "wine".

You would really do better if you simply copied and pasted the command from the post instead of retyping it.

---

### Post by RayArdia on 2014-05-09
Did as you said, got this

 ray@ray-Aspire-5735:~$ wine "C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"
wine: cannot find 'C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe'

What am I doing wrong - now?

---

### Post by Mark Phelps on 2014-05-10
You can only run Windows executables that you install using Wine.  It looks like you are trying to run a Windows executable from your native Windows installation.  Wine can not do that.

---

### Post by RayArdia on 2014-05-11
> **Mark Phelps said:**
> You can only run Windows executables that you install using Wine.  It looks like you are trying to run a Windows executable from your native Windows installation.  Wine can not do that.
Thanks for comment Mark but I no longer have a native Win installation. I DID have a dual boot with windows but gave it up as far too annoying (lots of ads, spurious Microsoft messages warning of imminent disaster etc, etc.)  I formatted my HDD and took the opportunity to upgrade from 13.04 to 14.04 so there SHOULD be no trace of native windows.

Can I check the HDD to make quite sure - I have GPARTED live 0.12.0.5 if that might help?

ps. I don't recall actually installing Windows using Wine, I have an iso. of Win 7 I could use.

---

### Post by Mark Phelps on 2014-05-11
Sorry, but I haven't used Wine in a long time (found it to be all but useless for my needs) and the path you present is the directory of "Program Files" in 32-bit format on a PC running 64-bit Windows.  Have you tried the command without the "(x86)"?

---

### Post by RayArdia on 2014-05-11
Tried without the (x86) no difference; however something very strange occurred.
I quit SU from launcher, then forced to close it. Then, because Wine was still showing in launcher I right-clicked it, intending to quit, but as I clicked  - up came Sketchup apparently acting normally!
Haven't time now to pursue further.
Has anyone anything to offer?

---

### Post by RayArdia on 2014-05-13
I'm still completely stuck!
Should I try another version of Wine, an older version of Sketchup?  One thing I'm not about to do to get Sketchup running is install Windows in any shape or form as a dual-boot - tried that, got the T-shirt and have put it in the rags bin.

Can anyone offer any help please? Or is Wine only useful if I want to play games, I ask this because most of the current development seems to me to be heavily biased towards gaming.

---

### Post by dasBuero on 2014-05-17
> **a3277426 said:**
> Hello, 
found a workaround which works for me.
start sketchup with this command:
wine "C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"

source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063](http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063)

Thank you for your workaround! Any chance to get Ruby API to work? I use several plugins but they obviously doesn't work without Ruby.

---

### Post by xt-gr79 on 2014-05-17
> **a3277426 said:**
> Hello, 
found a workaround which works for me.
start sketchup with this command:
wine "C:\Program Files (x86)\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"

source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063](http://appdb.winehq.org/objectManager.php?sClass=version&iId=30063)

That did the work for me! Thanks!

---

### Post by visctrix on 2014-06-06
For me I needed to delete the (x86) and then it worked, thanks.

wine "C:\Program Files\SketchUp\SketchUp 2014\SketchUp.exe" "/DisableRubyAPI"

Is there any way I can get SketchUp to launch this way automatically through the Unity Launcher instead of going to a terminal?

Thanks

---

