---
title: "How to delete Ubuntu"
date: 2006-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Seggons on 2006-04-02
Hi I am after some help/guidence and was hoping this is the right place to ask.

I have had Ubuntu on my system for a while and have had what I wanted from it and would like to remove it. The trouble I have is whenever I try my hardest to remove it, I just get a error to say that it cannot find the grub loader and freezes there. The only way to get into windows is to install Ubuntu again which installs the grub loader.

Is there a guide or something that helps me remove this?
Thanks alot for reading this :)
Seggons

---

### Post by paul cooke on 2006-04-02
[QUOTE=Seggons]Hi I am after some help/guidence and was hoping this is the right place to ask.

I have had Ubuntu on my system for a while and have had what I wanted from it and would like to remove it. The trouble I have is whenever I try my hardest to remove it, I just get a error to say that it cannot find the grub loader and freezes there. The only way to get into windows is to install Ubuntu again which installs the grub loader.

Is there a guide or something that helps me remove this?
Thanks alot for reading this :)
Seggons[/QUOTE]

apparently you boot with the windows cd, go into the recovery console, and fix the MBR...

don't actually have personal experience as all my boxes are 100% Linux.

there's some clues here:

[http://www.digg.com/linux_unix/Howto_remove_Linux._A_guide_from_Microsoft](http://www.digg.com/linux_unix/Howto_remove_Linux._A_guide_from_Microsoft)

and the official page from Microsoft on how to completely remove Linux prior to installing XP... 

[http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)

no clues there on how to keep and existing XP though

---

### Post by aciidboot3r on 2006-04-04
If you allready have Ubuntu and Windows on the same computer, you can just startup in windows, delete the ubuntu partitions, and then use the WinXP disk and go to the commandline and enter fixmbr. Quite easy.

---

### Post by evergreen on 2006-04-09
[QUOTE=aciidboot3r]If you allready have Ubuntu and Windows on the same computer, you can just startup in windows, delete the ubuntu partitions, and then use the WinXP disk and go to the commandline and enter fixmbr. Quite easy.[/QUOTE]


Yes I have used this method & It works very well

---

