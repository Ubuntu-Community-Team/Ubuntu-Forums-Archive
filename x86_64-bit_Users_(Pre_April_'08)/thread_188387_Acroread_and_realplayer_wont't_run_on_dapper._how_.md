---
title: "Acroread and realplayer wont't run on dapper. how to solve?"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by acer_peri on 2006-06-04
My computer is Amd64 3200+. I use both dapper amd64 and i386. Realplayer and Acrobat reader run properly in amd64 version, but when it comes to i386 version, when I run them, nothing happens, no error message displayed. Does it missing some library files, or ...?How can I fix that?
p.s. Formerly I use breezy i386 as well, but both of the two software run good.
Thanks everyone.

---

### Post by ctgray on 2006-06-04
Have you tried running them in the terminal? Maybe it will give you the reason why they don't start.

---

### Post by rhussong on 2006-06-27
I have solved this problem for Acrobat on my system.  In my case, it happened because I am using the SCIM input method, and SCIM has apparently been compiled with a different gcc/glibc than Acrobat.  As a workaround, I start Acrobat with the command "GTK_IM_MODULE=xim acroread", which causes SCIM not to be used for this instance of Acrobat.  I don't know if the fix will work with RealPlayer.

For further information, see [http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started")

---

### Post by Kilz on 2006-06-27
[QUOTE=acer_peri]My computer is Amd64 3200+. I use both dapper amd64 and i386. Realplayer and Acrobat reader run properly in amd64 version, but when it comes to i386 version, when I run them, nothing happens, no error message displayed. Does it missing some library files, or ...?How can I fix that?
p.s. Formerly I use breezy i386 as well, but both of the two software run good.
Thanks everyone.[/QUOTE]
Now there is a switch, usualy its someone saying its the other way around. You may get more answers asking i386 questions in the general Dapper support section.

---

