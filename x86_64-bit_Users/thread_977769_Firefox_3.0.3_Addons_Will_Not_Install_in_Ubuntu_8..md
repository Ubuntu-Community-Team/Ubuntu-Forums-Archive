---
title: "Firefox 3.0.3 Addons Will Not Install in Ubuntu 8.10 x64 on Dell XPS M1710"
date: 2008-11-10
forum: x86 64-bit Users
---

### Post by Cbcom0 on 2008-11-10
I am unable to install any addons for Mozilla Firefox 3.0.3. When I click add to firefox, it just sits there trying to connect, for which it never connects. I was able to install addons on Firefox 3.0.3 in Ubuntu 8.04, but not 8.10. Could somebody please tell me what I need to do to get the addons to install properly on 8.10?

Thanks

---

### Post by fooman on 2008-11-10
i remember a similar problem when i went from feisty to hardy.

what i had to do then was delet the extensions.rdf file in the .mozilla directory.

first close any firefox that may be running.  then open your home folder (places > home folder),  and in the toolbar click "view" and put a check next to "show hidden files".  then browse to /.mozilla/firefox/****

where **** will be a random series of letters and numbers

find the extensions.rdf file in there,  right click on it and choose "move to trash".

now open firefox and try again.

---

### Post by Cbcom0 on 2008-11-10
It works unfortunately it takes about 10 minutes for one addon to install. An addon should not take that long to install. What am I missing here?

---

### Post by fooman on 2008-11-10
edit: nevermind...i see it did work for you?

---

### Post by Cbcom0 on 2008-11-10
Yeah it worked, but like I said it should not take 10 minutes for an addon to install.

Does anybody know how to fix this problem?

---

