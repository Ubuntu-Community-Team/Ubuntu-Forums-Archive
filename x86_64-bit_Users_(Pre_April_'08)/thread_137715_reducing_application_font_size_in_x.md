---
title: "reducing application font size in x"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomislavmedak on 2006-02-28
i started using ion3 window manager. fonts used for menus and all what is default app text are now bigger than i would like them to be. 

i guess, as there are no gnome font rules that would override the application rules, i'd like to know how can i reduce the application font size - for two applications in particular - thunderbird and firefox, but for others as well. 

is there a general way to set per application rules and X-wide rules?

---

### Post by felix_stegerman on 2006-03-04
Hi,

I think GNOME was messing with your DPI settings by adding some extra X resource information.

You could try adding this to your ~/.Xresources:
  Xft.dpi: 96

I'm not sure whether this file is automatically used by X or ion, but you can always use:
  # xrdb -merge ~/.Xresources
to activate the resource information manually.

To find out what your GNOME settings were, log in to GNOME and run:
  # xrdb -query | grep Xft


Felix

---

