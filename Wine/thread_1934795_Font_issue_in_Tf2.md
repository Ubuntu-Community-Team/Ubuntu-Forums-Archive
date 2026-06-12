---
title: "Font issue in Tf2"
date: 2012-03-02
forum: Wine
---

### Post by ChasKi on 2012-03-02
Hi there, 

Firstly, thanks to the many contributors who've posted fixes previously for running Tf2 in Wine. 

I've read a -lot- of forum posts, blogs, guides and articles about running Tf2 in Wine and happily I can say that it does just that! I get reasonably good fps and not too much slow down even at max settings, 1680 * 1050 all features set to as high as the in game video menu will let me. I'm very new to linux having binned off Winblows and wiped my SSD clean with Ubuntu, so all of the guides etc have been very helpful!

_The rig:_ 

Ubuntu 11.10 Oneiric
Wine 1.4-Rc5
NVIDIA x86_64 280.13

Running a Core i5 2500k
Msi TwinFrozr 560Ti 1024mb
Asus Maximus Gene-Z IV ROG
OCZ Solid 3 SSD

tahoma font installed.

Wine registry has the following saved as string values under a Direct3D key in HKCU/Software/Wine/Direct3D a suggested by many a guide (With video memory changed to match my card): 

OffscreenRenderingMode fbo
UseGLSL Enabled
PixelShaderMode Enabled
VideoMemorySize 1024

_The problem:_ 

Fonts don't seem to display correctly. My launch settings are: -novid -h 1680 -w 1050 -win -noborder and I've tried removing each of them one at a time and tried -dxlevel's 81, 85 and 90 and it occurs on the autoconfig settings for each dxlevel and still occurs after changing the video settings through the in game menu. 

I noticed that if I bring up a chat window to speak in game, specific characters repeatedly throw up a blank box where the character should be - this seems consistent with the strange errors I'm seeing, as it's not so much a graphical glitch as there are no half-characters, only full characters with correct spacing for the rest of the letters in a word are missing. The characters k / and ; all cause a blank 'box' to appear where the letter or symbol should when in game. The same characters seem to be consistently throwing up this issue having just tested it out. Along with the letters h and y. I don't think it's a letter specific problem rather than a problem with the font itself entirely.

Whilst the game plays well, it's a very annoying bug as you can't see how many people are on the cart, you can't see the amount of health or ammo you have left in a number form. You can't see scores, or who's healing you or who you're healing. Big pain in the ****!

Tried everything I can think of, except the extracting something from a team fortress 2.res file as I couldn't find an app that would open the .res file (couldn't find a reliable download source for GCFExplorer) which I think may be a workaround for me to get this fixed by replacing the font used with another one - it would at least help to identify and isolate the issue to a specific font if nothing else! Does anyone know how I can get this done?

Thanks in advance if you made it this far and didn't just think tl;dr!

---

### Post by voidmage on 2012-04-04
I found this thread on google and you were the only other person I could find that had this issue. I'm not running Ubuntu but since this is the only other place I could find this, maybe if I post here it could help.

For me the fonts start out as missing, but the longer I play, the more letters start to show up correctly.

My setup:
Arch Linux
Kernel 3.2.13
Wine 1.5.1
Nvidia drivers 295.33

Intel 2500k
Nvidia GTX 570

Have you filed a bug with Wine?

---

### Post by fbis251 on 2012-06-08
3rd person who's reported having this issue. :/ It gets progressively better as the game continues but it's annoying trying to read any text at all.

---

