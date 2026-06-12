---
title: "More usplash, resolution issues with widescreen"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by ziesemer on 2008-12-02
I've already done a lot of searching, including finding and reading through the following bug (and many of its duplicates):
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623 ]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623") "[amd64 + nvidia 8xxx] usplash shows nothing"

However, it seems that most everyone has accepted that issue as resolved.  It was marked as "fix released" against Hardy on 2008-03-22.  I'm assuming that running Intrepid with all the latest updates as of today, I should have that, too.

I was apparently having the exact same issues, though.  usplash would only intermittently display during startup.  Sometimes I'd get to the graphical login screen anyway, sometimes it would take several minutes, and sometimes it seemed to hang indefinitely.  I had the issue before and after installing the proprietary nVidia 177 driver, thinking that it may help resolve the issue.

After adding "vga=0x031b" to my /etc/grub/menu.lst (1280x1024), then adding xres=1280 and yres=1024 into /etc/usplash.conf, all of the immediate issues appear to be resolved.

However, the proper resolution for my system is 1920x1200, which I would like to use.  The vga mode I used for this was 0x037d.  While this also "worked", usplash doesn't appear to display properly in that resolution.  The progress bar appears "too low" on the screen.  The progress text (I have "quiet" turned off) then collides with it.  Additionally, even before the text starts colliding, the height of the progress bar continuously flickers between the normal height and only a few (3-5?) pixels.

I've attempted leaving the vga mode at 0x037d (1920x1200) while switching /etc/usplash.conf to different resolutions - including resolutions that maintain the same aspect ratio and otherwise.  While the above issue is apparently fixed, usplash either fails to display at all, or the entire usplash view appears normal but off-center - almost always to the left.

I've seen various suggestions about un-blacklisting various framebuffer modules, but have not yet tried any of them without knowing if this is even related to this issue, etc.

A collection of system config files and logs are attached.  The system is a Dell Latitude E6500 with a nVidia Quadro NVS 160M.  Please let me know if you need anything further.


Should the above changes still be needed to get a stable boot?

What should be done about the apparent usplash progress bar issues at 1920x1200?

Is there anything else I should attempt, or should I file this as another bug report?

Thanks!

---

