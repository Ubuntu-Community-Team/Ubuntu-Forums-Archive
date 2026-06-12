---
title: "How to disable usplash?"
date: 2007-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Freddy on 2007-10-14
How can I disable usplash? I want to try out the 64bit version of Gutsy but had some (major) problems when trying to boot Ubuntu, usplash doesn't shot itself and the boot up stops.

I know that this is a known and reported bug since I have reported it myself but how do I disable usplash without having access to a editor?

/Thanks

---

### Post by John.Michael.Kane on 2007-10-14
> **Freddy said:**
> How can I disable usplash? I want to try out the 64bit version of Gutsy but had some (major) problems when trying to boot Ubuntu, usplash doesn't shot itself and the boot up stops.

I know that this is a known and reported bug since I have reported it myself but how do I disable usplash without having access to a editor?

/Thanks

Try this.
When the PC boots up, you will see Grub counting down,Press "Esc" to bypass this countdown and enter a Grub menu. Then

1)Press 'e' to start editing.
2)scroll down to until you find the section below, and Change the part in bold:
```
  ## additional options to use with the default boot option, but not with the
  ## alternatives
  ## e.g. defoptions=vga=791 resume=/dev/hda5
  **# defoptions=quiet splash**
```
3) select the line you want to edit with the <Up> and <Dn>Keys (The up and down arrow keys)

4)press 'e' once more to edit the selected line.

5)delete the options 'quiet' and / or 'splash' with the delete keys

6)press <Esc> to leave the edit mode and press <b> to boot

Note: depending on your setup there might be more options not only quiet and splash. Don't delete the other options, only delete quiet and splash.

Hope this helps.

---

### Post by Freddy on 2007-10-14
Thanks Plissken, I will try this tomorrow when I reinstall.

---

