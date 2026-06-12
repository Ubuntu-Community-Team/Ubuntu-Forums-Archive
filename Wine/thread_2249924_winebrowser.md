---
title: "winebrowser"
date: 2014-10-25
forum: Wine
---

### Post by jwfox on 2014-10-25
2I've done dozens of searches through google and on various forums, but  most of the results I've found are very old (2008-2010 or so), and none  of them seem to work. I suspect the reason I'm not turning up anything  newer is because there's such an easy way to do it that nobody's asking the  question anymore, and I'm just overlooking something obvious.

Anyhow,  here's my problem: Gecko opens wine's version of IE by default, and I'd  like to change this. Even if I have another browser open, popups open  in wine's IE. 

In my particular case, it's a proprietary  browser required for school; Respondus Lockdown. It's installed through  PlayOnLinux, and runs fine without detecting a virtualized environment  or compatibility mode, but when I try to take a quiz or exam, the popup  window is wine's IE, which of course tells me I must use the other  browser. 

Since it's in its own wine bottlethrough  PlayOnLinux, the default browser won't affect anything else. I just  can't figure it out.  

Thanks in advance for any help. 

Edited for line breaks.

Edited again to add:
I've got Win7 installed under VirtualBox, but the program detects the virtualized environment and won't run at all there.

---

### Post by jwfox on 2014-10-25
OK, it looks like I've finally got it working...

I've been chasing my tail on this for way too long. Here's what I did:

First off, DON'T install the stupid lockdown browser directly... I used POL's wizard to install IE6.

Once that's done, in POL's configration (Miscellaneous tab), "Run a .exe file in this virtual drive". Browse to Respondus' installer....

Hooray. Popups now open in the lockdown browser. Toolbar is uglier than sin, but no worries.

Edit: It all looked OK at the login screen, but after logging in the page didn't render correctly and had problems. Did the same thing with IE8, and all is joy. Going to try with Firefox, but I think the program actually uses IE's DLLs.

Edit again:Firedox is a bust. Program looks and behaves the same as with IE6. The IE8 install is working fine, with wine set as Win7. WinXP results in a "compatability mode" error from the program.

---

