---
title: "Thunar won't let me unmount USB drive when copying large files"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by lufte on 2009-11-10
I'm running the 64-bit version of Xubuntu Karmic and I have this problem. When a copy a large file (a movie for example, around 700 MB) to a USB flashdrive, the "remaining time" is obviously wrong, because it reads 10 seconds more or less. When it finishes and I try to unmount the drive, it returns the "there's still data that needs to be written to the device, please do not remove bla bla" message, and a moment after it says that the volume couldn't be unmounted and that's all. The volume remains as unmounted but I can't mount it back, and if I reinsert the drive I see that the file didn't copy.

Is there a way to fix this? A workaround would be to tell Thunar to show the **real** remaining time, but I don't know how to do that. Any help will be appreciated.

---

### Post by lufte on 2009-11-12
up

---

### Post by lensman3 on 2009-11-13
I think with a flash drive, the OS allocates the entire 700 meg file and then starts writing it.  The write is delayed so it returns and says its done.  Try typing "sync" in a text window.  Everything will be written to the disk before the prompt returns.

This is normal in Linux/Unix, however, you should be able to control this during the flash drive mount (though I'm not sure the automounter will let you change this).

The eject/umount won't let umount the drive until everything is flushed.

---

### Post by lufte on 2009-11-17
Thanks for the answer. I should type that "sync" command while I'm copyng or after that? If you could explain me how to mount the drive with that option included, even if I've got to mount it manually, I would really appreciate it. Thanks again.

---

### Post by dcstar on 2009-11-18
> **lufte said:**
> I'm running the 64-bit version of Xubuntu Karmic and I have this problem. When a copy a large file (a movie for example, around 700 MB) to a USB flashdrive, the "remaining time" is obviously wrong, because it reads 10 seconds more or less. When it finishes and I try to unmount the drive, it returns the "there's still data that needs to be written to the device, please do not remove bla bla" message, and a moment after it says that the volume couldn't be unmounted and that's all. The volume remains as unmounted but I can't mount it back, and if I reinsert the drive I see that the file didn't copy.

Is there a way to fix this? A workaround would be to tell Thunar to show the **real** remaining time, but I don't know how to do that. Any help will be appreciated.

The file manager probably does no know when the actual physical write is complete, only the logical completion when the all the data has been delivered to the disk cache (and the disk cache is being written to the device in background).

You either have to disable any write caching or just wait for the data to be actually written - either way will take the same amount of time.

---

### Post by lufte on 2009-11-18
Disabling the writing cache seems as a very difficult/low level task. Besides, I would only want to do this when writing on flash drives, not every time. I could give it a shot but I have no idea where to start, I'll try to do som research anyway. Thanks for the tip!

---

