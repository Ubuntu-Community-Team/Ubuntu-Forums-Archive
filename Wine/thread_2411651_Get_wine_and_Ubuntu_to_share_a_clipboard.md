---
title: "Get wine and Ubuntu to share a clipboard?"
date: 2019-02-01
forum: Wine
---

### Post by gardengxc2 on 2019-02-01
I have a stable copy of Kindle for PC running under Playonlinux and Espeak is configured and running well.

I want push a button and have it play the highlighted text in my kindle book. I'm trying to use the script 
#!/bin/bash


xclip -o | xclip -selection clipboard -i
xclip -o | espeak


but it never picks up highlights in wine. So how do I link the clipboards/ grab highlighted text in wine?

---

### Post by dacha on 2019-03-29
Firstly what are you doing there? Why is xclip being called 3 times?

X11 has several clipboards.
When you copy with Ctrl+C, it goes into "CLIPBOARD", and Ctrl+V pastes from "CLIPBOARD".
Mere text selection goes into "PRIMARY", and middle-click pastes from "PRIMARY".

xclip's default clipboard is PRIMARY.

```
xclip -o | xclip -selection clipboard -i
```
outputs from PRIMARY, then inputs into CLIPBOARD.

```
xclip -o | espeak
```
outputs from PRIMARY, pipes it to espeak's stdin.

You should only need the second line. The first line is only there to copy PRIMARY to CLIPBOARD so Ctrl+V can paste, it should not affect the second line at all.

Now onto why it isn't working.

Does Wine even populate PRIMARY when text is selected? Let me investigate.

---

### Post by dacha on 2019-03-29
I've looked at the source code and run a few tests, and apparently Wine doesn't update the PRIMARY selection when text in a Windows application is selected. It only updates CLIPBOARD, and only when Ctrl+C is pressed.

To get your application working, you have to select text in the Windows application running under Wine, copy it into the CLIPBOARD selection with Edit->Copy or Ctrl+C or the like, and then get xclip to paste from the CLIPBOARD selection and pipe it to espeak:

```
xclip -selection clipboard -o | espeak
```

If you really want it to automatically copy selected text into the PRIMARY selection without Ctrl+C, please consider filing a bug report with the Wine project.

---

