---
title: "Can I run wine without a windows installation?"
date: 2008-07-07
forum: Wine
---

### Post by KOTAPAKA on 2008-07-07
Well What I did is I installed windows, installed all the windows programs I needed and I formated the drive with the windows installation keeping the drive with the installed programs intact. Can I run those programs with wine and how?

---

### Post by cogadh on 2008-07-07
Wine does not require the presence of Windows at all, however, the way you did things is not the correct way to use Wine. Instead of installing things in Windows, then deleting Windows and keeping the installed directories, skip that whole mess and just install the Windows software directly into Linux through Wine. That is how Wine is meant to work and is the way you will have the most success running applications with Wine.

Unfortunately, using Wine to try and run those applications you already had installed on the Windows drive is not likely to work. Most modern Windows software uses the Windows registry quite a bit. Since you installed the software in Windows, all of the associated registry entries were in Windows, not Wine. Now that you have deleted Windows, the registry is gone and the apps are very likely to just error out when you try to run them. If you install the apps in Linux through Wine, then all the necessary registry entries will be written into the Wine registry, which the application will happily access when run.

---

### Post by johannelim on 2008-08-18
actually... I'd like to have a more specific follow up to this question though I think i'd get shot asking.  :-)

Can one install Visual Basic Studio 6.0 in Wine and then successfully compile apps on it?

I've recently run the LiveCD ubuntu I just downloaded today and whoa does it blow windows away frommy first impression.  Everything runs so smoothly and the aesthetics is mind-boggling.  Great work.

But since most of my development work runs off of VB... can I continue that solely under Ubuntu?

---

### Post by kdorf on 2008-08-18
Don't bump old threads, start new ones.

If Wine doesn't run the compiler/IDE, you can use a virtual machine with Windows installed.

---

