---
title: "thinkpad t61 Gutsy amd64 hibernation problem"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by tstavely on 2008-03-19
Dear All,

Most things have worked fine with my installation of Gutsy on a 14.1-inch Thinkpad t61, including hibernation (in most respects) and sleep -- though I did make the usual changes to /boot/grub/menu.lst and elsewhere.  However, something doesn't shut down completely in hibernation mode, at least on most occasions.  For example, last night after a long session of use while plugged in I put the computer into hibernate mode with /etc/acpi/hibernate.sh and unplugged.  Seven or eight hours later when I plugged the computer in and turned it on the battery was at 95% of full charge.  When I run in Gnome and do the hibernate I often get a little panel balloon on coming back to life indicating the shutdown had been incomplete.

I've scanned various logs but I don't know what I am looking for so I haven't discovered what my problem is.  All suggestions greatly appreciated!

Tony

---

### Post by John Jason Jordan on 2008-03-19
> **tstavely said:**
> I've scanned various logs but I don't know what I am looking for so I haven't discovered what my problem is.  All suggestions greatly appreciated!
I have a T61, but I have never gotten hibernate to work at all. On the other hand, I don't really need it anyway, so I just ignore the problem. I do know that some people do have it working, but the solutions vary according to which video you have and which driver you are using.

I know this issue has been discussed in detail on the Thinkpad e-list, which you can find here:

[http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad](http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad)

There is also a wiki for Thinkpads, which the above page should have a link to.

---

### Post by tstavely on 2008-03-19
Thanks, JJJ.  I've subscribed to that list.  Two other thinkpads I've had have needed tweaking to hibernate and/or sleep.  Often when there's a Ubuntu upgrade more tweaking is required for that or other functions.  Meanwhile, I can always just shutdown when I want to stop draining the battery and stop computing.  Coming back from hibernation isn't much faster than a reboot.

---

