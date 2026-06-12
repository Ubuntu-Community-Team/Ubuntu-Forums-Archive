---
title: "Program starts - and disappears"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yumi on 2006-09-22
I just experiencing that Thunderbird starts up, starts loading new mails and disappears without Error or trace. Now the same happens to Openoffice, the splash-screen shows and disappears as well.

Any hints where to look?

Michael

---

### Post by wieman01 on 2006-09-22
Fire them up from a terminal. The output should reveal all error messages:
> thunderbird
Then we'll see.

---

### Post by acefreely on 2006-09-22
Try launching from a shell, when it errors out it should give you some specific type of error...

---

### Post by Yumi on 2006-09-22
Here is the output after starting in terminal

$ mozilla-thunderbird
GTK Accessibility Module initialized
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1
(Gecko:11976): GLib-GObject-WARNING **: gsignal.c:1017: unable to lookup signal "activate" of unloaded type 'MaiAtkObject'

(Gecko:11946): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion 'signal_id >0' failed
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 11976 Segmentation fault
    "$prog" ${1+'$@"}


I heard about the Segmentation fault being something nasty to take care off.

Michael

---

### Post by wieman01 on 2006-09-22
Beats me, buddy. Sorry for this.

---

### Post by Yumi on 2006-09-22
Thanks for trying. You got me to find the error message. Thats the first part for solving the problem.

---

### Post by acefreely on 2006-09-22
Try rebuilding your thunderbird profile...

```
mkdir ~/oldTbird
cp -r ~/.mozilla-thunderbird/* ~/oldTbird/

```

Fire up a file manager window and make sure that all of the files from your old profile copied to the oldTbird directory, also make sure they are the same size.  
```

rm -dfr ~/.mozilla-thunderbird
```

Now start thunderbird from shell and see what happens.  Keep in mind that you will have to reconfigure your email accounts, or if you like you can go into your oldTbird directory and copy your email data back into your new profile.  You will not lose any emails, just a matter of getting them back into your new profile.

---

### Post by Yumi on 2006-10-03
Thanks ACEfree! A new profile did the trick.

---

