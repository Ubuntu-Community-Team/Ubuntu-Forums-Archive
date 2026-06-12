---
title: "wine"
date: 2012-11-27
forum: Wine
---

### Post by cmcanulty on 2012-11-27
i messed up the graphics settings in wine and now it is unusable. i've tried reinstall, completely remove and purge nothing changes see screenshot. I can't see any more than the screenshot

---

### Post by Promille on 2012-11-27
> **cmcanulty said:**
> i messed up the graphics settings in wine and now it is unusable. i've tried reinstall, completely remove and purge nothing changes see screenshot. I can't see any more than the screenshot

Try running it in terminal in the format "wine someprogram.exe" and post the output, if any. The screenshot isn't helping that much unfortunately.

---

### Post by cmcanulty on 2012-11-27
I set the resolution to the highest so now all I get is the huge print like I posted and can't reach anything else to reset it. Why doesn't purge take all my configs and start fresh?

---

### Post by howefield on 2012-11-27
Thread moved to the "*Wine*" forum.

---

### Post by cmcanulty on 2012-11-27
sorry I didn't realize there was a wine forum

---

### Post by Mr. Hibba on 2012-11-28
> **cmcanulty said:**
> i messed up the graphics settings in wine and now it is unusable. i've tried reinstall, completely remove and purge nothing changes see screenshot. I can't see any more than the screenshot

I might have a solution.

1. Click on the top checkbox labeled "Automatically Capture the ..." 
2. Press the Tab key exactly 4 times.
3.  Press and hold the left arrow key for a few seconds.  
4.  Press the Enter key.  
5.  Run Winecfg again and see if it is fixed ;-)

Hope this helps, 

Mr. Hibba.

---

### Post by cmcanulty on 2012-11-28
No change. Isn't there a way to start over & why does purge retain the bad setting? I thought completely remove and purge took everything out as far as config settings. I was just trying to make it more easy to read so I increased the resolution to max. Isn't there a file somewhere I can edit to fix this. I tried your fix 2X but it did nothing. Thank you

---

### Post by sudodus on 2012-11-28
> **cmcanulty said:**
> No change. Isn't there a way to start over & why does purge retain the bad setting? I thought completely remove and purge took everything out as far as config settings. I was just trying to make it more easy to read so I increased the resolution to max. Isn't there a file somewhere I can edit to fix this. I tried your fix 2X but it did nothing. Thank you
Have you tried to remove the .wine directory in your home directory?

```
rm -r ~/.wine
```

---

### Post by cmcanulty on 2012-11-28
well I tried something drastic and it worked. I deleted the .wine folder then reconfigured and then pasted back in all my program files. Very weird that purge wouldn't do that,solved but not pretty

---

