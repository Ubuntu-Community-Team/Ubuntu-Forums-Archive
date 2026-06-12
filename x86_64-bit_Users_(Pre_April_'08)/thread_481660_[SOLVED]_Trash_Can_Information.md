---
title: "[SOLVED] Trash Can Information"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-22
I have found that when I delete files in ubuntu and empty the trash can the files are still taking up space on my HD.  I booted into windows for some video work and found that my data drive has a directory called .trashcan

This directory is hidden while booted to ubuntu but not windows.  Looking inside the directory, I found 16 GB of data I had erased from the drive days before.

Is there a way to make ubuntu empty out this folder on it's own so that my HD space isn't being occupied or do I have to boot to windows to actually reclaim my HD space?  It seems that ubuntu only moves the files to the trashcan directory and then hides them from the user.

---

### Post by eentonig on 2007-06-22
I believe it's like this:
The diskspace used by the files is actually freed. So if the diskspace is needed, those files will be overwritten.

Personnally, I don't use the trashcan. If I need to remove somthing, I have the habit of doing it via the cli. But you can enable a nautilus option to add a 'Delete' menu item that doesn't move files to the trashcan.

---

### Post by crjackson on 2007-06-22
> **eentonig said:**
> I believe it's like this:
The diskspace used by the files is actually freed. So if the diskspace is needed, those files will be overwritten.

Personnally, I don't use the trashcan. If I need to remove somthing, I have the habit of doing it via the cli. But you can enable a nautilus option to add a 'Delete' menu item that doesn't move files to the trashcan.

I'm not sure what you mean by cli.  But I'll look for the option to add a "Delete" selection to the menu.  When I delete, I want it GONE...  I don't mind having the trashcan thingy, but you would think that when you tell it to empty it would do just that, rather than HIDE the contents...

Thanks...

---

### Post by NeoLithium on 2007-06-22
cli is just the command line interface. Like using rm <filename> to delete something in a shell (terminal) window. :)

---

### Post by i0Null on 2007-06-22
You can delete a file without it going to the trash by highlighting the selected files and pressing Shift+Delete. 

Same goes for Windows.

---

### Post by scradock on 2007-06-22
As I read the OP question, it's actually a bit more subtle. He was trying to delete files on a "data drive" - presumably a separate drive/partition. What happens then, as far as I know, is that a separate .Trashxx folder (hidden) is created _on that drive_. 

Emptying the regular Trashcan does nothing to that. You can delete it by opening the drive/partition in file browser, enabling View of hidden files, then right-clicking .Trashxx and choosing "Send to Trash". 

That actually _does_ delete the folder and its contents. Next time you delete something on the same drive the .Trashxx is recreated, and stuff is "moved" to it until you send it all to the ultimate .wp once again.

It is confusing, until you get used to it. Hidden folders are hard to spot if you're not looking for them....

---

### Post by crjackson on 2007-06-23
> **scradock said:**
> As I read the OP question, it's actually a bit more subtle. He was trying to delete files on a "data drive" - presumably a separate drive/partition. What happens then, as far as I know, is that a separate .Trashxx folder (hidden) is created _on that drive_. 

Emptying the regular Trashcan does nothing to that. You can delete it by opening the drive/partition in file browser, enabling View of hidden files, then right-clicking .Trashxx and choosing "Send to Trash". 

That actually _does_ delete the folder and its contents. Next time you delete something on the same drive the .Trashxx is recreated, and stuff is "moved" to it until you send it all to the ultimate .wp once again.

It is confusing, until you get used to it. Hidden folders are hard to spot if you're not looking for them....

You nailed it.  There is no avoidence of this then?  I'll just have do do regular housekeeping I guess...

---

### Post by CrankyFilipino on 2007-07-10
I've spent the last 30 minutes or so with this issue. Man I really appreciate this fix of sending the .Trash to the trash. Gained 4 gigs back of space and I stopped from going mad. Although the regular housekeeping angle is pretty annoying and I'm still looking for the fix so that I don't have to do that. I guess I'll have to remember Shift + Delete. Also, as I become more and more familiar with Ubuntu and like it more, I'm probably going to do at least 50/50 with Vista on the partition. Make it 60 gigs each. :)

---

