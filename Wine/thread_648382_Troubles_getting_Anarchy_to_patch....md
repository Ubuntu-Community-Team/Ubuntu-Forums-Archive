---
title: "Troubles getting Anarchy to patch..."
date: 2007-12-23
forum: Wine
---

### Post by SoliDphantoM on 2007-12-23
Now i've done some searching in the forums and outside, and the general idea seems to be...download the 17.5.1-17.5.2 patch, run it, copy the old patcher from the temp file, then run the old patcher to update anarchy and never run it from the client. 

Well, i've tried running it one of two ways,
1) goto the directory, then ```
wine anarchypatcher.exe
``` when i do this, it brings up the client and it updates to the new patcher and i get the "Unsupported" error.

2) goto the directory, then ```
wine anarchypatcher.exe* version to patch to*
``` it's opens up the patcher and gives me the "Unsupported" error.

So am i doing this wrong? Am i suppose to copy more than just the old patcher from the temp file? 

And another error i sometimes get, is "cannot write make sure you have the proper permissions" or something along those lines. I have AO installed on my NTFS Windows partition.  I do have the NFTS Config Tool so i know i can write to it and have done it before....is there something special i need to do w/ Wine? I searched on here and tried to do the Nautilus thing, and change the permissions to that folder that way, but what i go back to that folder, it doesn't seems like it saves those settings.


But i'm happy cause it's been almost 3-4 months since i've booted windows and i'm loving Ubuntu! The community for it is in a word awesome, i've usually been able to find my exact problem on the forums.....with the exception of this one. So i figured i give it a try.... thanks for your help!!

---

### Post by markharding557 on 2007-12-27
try installing it directly in to wine this will eliminate ntfs permission problems.
an easy way to use wine is to load winefile,type winefile in a console and you will get wines file manager you can run progs and install using this

---

