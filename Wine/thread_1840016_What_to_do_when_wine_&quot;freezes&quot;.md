---
title: "What to do when wine &quot;freezes&quot;"
date: 2011-09-06
forum: Wine
---

### Post by Melhisedek on 2011-09-06
Well it doesn't freeze the whole PC but most of it. Like I can move the mouse and see the cursor moving but not much more... CTR+ALT+left or right doesn't work neither CRTL+ALT+DELETE or ALT+F4.

CTRL+ALT+F1 does work but I can only reboot from there...
Is there anything else I can do to get back to desktop?

(tried with emulated desktop and without... still same thing)

P.S. this is happening while I try different options to get Civ V to work

---

### Post by disabledaccount on 2011-09-06
It depends on what really happened, but generally You can do 2 things:
1. from terminal (either terminal emulator or tty after pressing ctrl-alt-F[1-6]):
>wineserver -k
>killall <name_of_exe>
then go back to DE with ctrl-alt-F7

2. If DE is responsive "enough" You can use "Force Quit" panel applet.

---

