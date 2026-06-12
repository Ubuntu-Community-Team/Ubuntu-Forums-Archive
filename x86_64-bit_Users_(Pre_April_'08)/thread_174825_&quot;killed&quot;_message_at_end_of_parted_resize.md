---
title: "&quot;killed&quot; message at end of parted resize"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by davygravy on 2006-05-12
I am using parted to resize the HFS+ partition on my eMac.  Everything goes along just fine, and then when done (or nearly done) I get a message at then end (unceremoniously)

killed


???

This has happened twice.  I am still able to boot into OS X, but unfortunately I  see my "space available" (as it appears at the bottom of any finder window) for OS X is dropping each time I do it.  From both the Mac OS X and Ubuntu side (when running any sort of disk utility), the HFS+ partition still reads at the original size.

It is now down to the point that it OS X is, of course, complaining that there is not enough available space on the startup disk.

Ideas on what is going wrong?

thanks,

davygravy

---

### Post by farruinn on 2006-05-12
This isn't something I have attempted, but I assume you were following directions from this thread: [http://www.ubuntuforums.org/showthread.php?t=89960]("http://www.ubuntuforums.org/showthread.php?t=89960") ?

There is a message there that indicates this feature is experimental but that the author of parted would like you to e-mail him if the resizing failed for you.

[quote=davygravy]Ideas on what is going wrong?[/quote]

Sounds like everything is screwed up. I strongly recommend you backup all your important data and reformat.

Good luck :/

---

### Post by slux on 2006-05-13
"Killed" gets output when a process gets forcefully killed (ended) by user action, by the system during a runlevel change or as is the only possibility I can see in your case - by the kernel itself when the out of memory killer springs into action to prevent running out of memory and tries to choose a process that is consuming too much of it. This is most often the result of a runaway process that starts eating it indefinitely but can also happen if you have a machine that doesn't really have enough memory for all of what you're trying to run at the same time.

Whether or not you had too little memory or the resizer would've consumed any possible amount of it, your filesystem is probably now not in a very nice shape. I'd backup everything to another media ASAP unless you have already done that and try to check the filesystem and failing that do a reinstall (maybe shrinking the volume in the process to accommodate Ubuntu).

---

### Post by davygravy on 2006-05-14
Backup?  What's that? Never occurred to me...  :^)  just joking...already done.

I wasn't able to recover from whatever problem it had.  There were some pretty big files on the HFS+ , and the eMac has only 384MB, so it could have had a memory requirement problem.

In the end, I had to use OS X and Carbon Copy Cloner to copy the contents to a firewire drive, partition it in OS X, and then install Dapper.  

Just about done now, just have to reinstall the OS X over to the newly created HFS+ partition, and configure yaboot to see the OS X as well as the Dapper.

Thanks for your ideas.

davygravy

---

