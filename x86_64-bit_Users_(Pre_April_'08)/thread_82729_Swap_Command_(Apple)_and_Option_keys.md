---
title: "Swap Command (Apple) and Option keys"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ascarter on 2005-10-27
I am using an Apple USB Keyboard with a Dell running Breezy.  I would like to swap the behavior of the Command (Apple) key and the Option key so that Command acts like Alt on a PC keyboard.  I also want to use Synergy with my powerbook so I need the Command + option keys to send the right codes to the Powerbook.

I've been searching the forums and google and I can't find the answer.  I believe it is a matter of creating the right xmodmap file but I'm not understanding it.

Thanks,
Andrew

---

### Post by fdiv_bug on 2006-09-28
I suppose a response is better late than never, so I'm adding how I did it here for future Googlers.  This was with an older Apple USB keyboard -- the kind with the translucent black keys -- but I think it should work with newer models of keyboard.

For X, in ~/.xmodmap (a file you may need to create) add the following:

```
clear mod1
keycode 115 = Alt_L
keycode 64 = Meta_L
keycode 116 = Alt_R
keycode 113 = Meta_R
add mod1 = Alt_L Alt_R
```

Then log out and back in again.  If you're asked to add keymaps to load, add .xmodmap to the list.

I haven't bothered figuring out how to do it on the console yet, but if I do I'll add information here.

Hope that helps!

---

### Post by trjonescp on 2007-07-11
One more useful line for me at the end of that .xmodmap config file was

```
add mod4 = Meta_L Meta_R
```

So the complete file looks like:

```
clear mod1
keycode 115 = Alt_L
keycode 64 = Meta_L
keycode 116 = Alt_R
keycode 113 = Meta_R
add mod1 = Alt_L Alt_R
add mod4 = Meta_L Meta_R
```

---

### Post by trjonescp on 2007-07-11
PS - This is so that you can use the Meta Key (aka windows key) to setup keyboard shortcuts just like in Windows (e.g. <Meta> + R  maps to "Run command")

---

### Post by nyinge on 2007-07-26
> **trjonescp said:**
> One more useful line for me at the end of that .xmodmap config file was

```
add mod4 = Meta_L Meta_R
```So the complete file looks like:

```
clear mod1
keycode 115 = Alt_L
keycode 64 = Meta_L
keycode 116 = Alt_R
keycode 113 = Meta_R
add mod1 = Alt_L Alt_R
add mod4 = Meta_L Meta_R
```

Awesome!  Now, what should I do to make it work on KDE?  Yes, GNOME would pop a question to load the file ".xmodmap" automatically, but KDE isn't asking anything like that.

P.S.  I realize this is not the right forum to be asking this multimedia related question, but this thread comes closest to my problem.

---

### Post by incubus on 2007-07-26
KDE looks for '.Xmodmap', so the uppercase 'X' makes a difference.

By the way, just as a suggestion, have you thought about using the Apple Key as Ctrl instead?  I know it sounds weird, but then you'll use your thumb for operations like copying, pasting, etc, which in my opinion is more ergonomic than using the pink finger.

I hope it works on KDE.

incubus

---

### Post by nyinge on 2007-07-26
> **incubus said:**
> KDE looks for '.Xmodmap', so the uppercase 'X' makes a difference.

By the way, just as a suggestion, have you thought about using the Apple Key as Ctrl instead?  I know it sounds weird, but then you'll use your thumb for operations like copying, pasting, etc, which in my opinion is more ergonomic than using the pink finger.

I hope it works on KDE.

incubus
Thanks, but it doesn't work for me.  Am I missing something.. like ..  I have to manually enter the file name '.Xmodmap' somewhere to make it run?  Thanks.

---

### Post by incubus on 2007-07-27
That's weird.  Are you on Feisty?  I think they added this feature in the last release.

As you probably know, '.Xmodmap' should be in your home directory.

Alternatively, here's what you can do:
1. Create a file 'xmodmap.sh' in ~/.kde/Autostart/
```

#!/bin/bash
xmodmap ~/.Xmodmap

```

2. Make it executable:
```

$ chmod +x ~/.kde/Autostart/xmodmap.sh

```

3. Test it.  Logout and login again.

Does it work?

incubus

---

### Post by nyinge on 2007-07-27
Ah..  It's working now.  Awesome.  Thank you.

hmm..  I think it wasn't working before, because I start KDE from the CLI rather than from the KDM.  KDM, perhaps, is the one that takes care of .Xmodmap file.  Anyway, thanks again.

---

